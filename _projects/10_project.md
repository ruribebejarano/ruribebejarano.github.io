---
layout: page
title: Robot autobalanceado con control LQR
description: Péndulo invertido sobre dos ruedas con ESP32, estimación por filtro de Kalman y control óptimo LQR diseñado en MATLAB.
img: assets/img/proj_lqr.jpg
stack: ["ESP32", "LQR", "Filtro de Kalman", "MATLAB", "Espacio de estados"]
importance: 1
category: control y robótica
---

**Control moderno · Proyecto académico · ESP32 + MATLAB**

Robot de dos ruedas que se mantiene en equilibrio por sí mismo: un **péndulo invertido sobre ruedas**. Es un sistema **inestable en lazo abierto** y **subactuado** (dos motores deben controlar a la vez el ángulo del cuerpo y la posición del robot), por lo que es un caso clásico para aplicar **control en espacio de estados** con un regulador óptimo **LQR**.

<div class="row justify-content-sm-center">
  <div class="col-sm-9 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/lqr_robot.jpg" title="Robot autobalanceado" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Prototipo: chasis de tres niveles con varillas roscadas, dos motorreductores DC con encoder, paquete de baterías y la electrónica de control en la parte superior.</div>

### 1. Modelado matemático

El robot se modela como un cuerpo (péndulo) articulado sobre el eje de dos ruedas. Con las ecuaciones de **Euler-Lagrange** (o Newton) se obtienen las ecuaciones no lineales del movimiento, incluyendo la dinámica de los motores DC (constante de torque $$K_t$$, constante de fuerza contraelectromotriz $$K_e$$ y resistencia de armadura $$R_a$$), de modo que la entrada sea el **voltaje** aplicado.

Se elige el vector de estados

$$
\mathbf{x} = \begin{bmatrix} x & \dot{x} & \theta & \dot{\theta} \end{bmatrix}^T
$$

donde $$x$$ es la posición de las ruedas y $$\theta$$ la inclinación del cuerpo. Linealizando alrededor del punto de equilibrio vertical ($$\theta = 0$$) se llega al modelo

$$
\dot{\mathbf{x}} = A\,\mathbf{x} + B\,u, \qquad y = C\,\mathbf{x}
$$

### 2. Identificación de parámetros

El modelo solo es útil si sus parámetros son reales:

- **Masas** del cuerpo y de las ruedas, **radio** de rueda y **altura del centro de masa**.
- **Momento de inercia** del cuerpo (por ejemplo, con un ensayo de péndulo).
- **Parámetros del motor** a partir de la respuesta al escalón y de mediciones de corriente y velocidad, incluyendo la **zona muerta** del motorreductor.

### 3. Análisis del sistema

- Los **autovalores** de $$A$$ muestran un polo en el semiplano derecho: el sistema es inestable sin control.
- Se verifica la **controlabilidad** con $$\operatorname{rank}\,[B \;\; AB \;\; A^2B \;\; A^3B] = 4$$ y la **observabilidad** con las salidas medidas (ángulo y encoders).

### 4. Diseño del controlador LQR

El LQR calcula la ganancia de realimentación $$u = -K\mathbf{x}$$ que minimiza

$$
J = \int_0^{\infty} \left( \mathbf{x}^T Q\, \mathbf{x} + u^T R\, u \right) dt
$$

resolviendo la **ecuación algebraica de Riccati**, con $$K = R^{-1}B^T P$$. La matriz $$Q$$ penaliza el error en cada estado (sobre todo $$\theta$$ y $$\dot{\theta}$$) y $$R$$ el esfuerzo de control; un buen punto de partida es la **regla de Bryson** y luego se ajustan experimentalmente. A diferencia de un PID por lazo, el LQR controla **todos los estados a la vez**, equilibrando ángulo y posición en una sola ley de control.

La ganancia $$K$$ se calcula en **MATLAB** (`lqr` / `dlqr`). Como el control corre en el **ESP32**, el modelo se **discretiza** con el periodo de muestreo $$T_s$$ y se usa la versión discreta del LQR.

### 5. Estimación de estados

No todos los estados se miden directamente, así que se estiman:

- **Ángulo $$\theta$$**: fusión del acelerómetro (preciso a largo plazo, ruidoso) y del giroscopio (preciso a corto plazo, con deriva) mediante un **filtro de Kalman**, que estima el ángulo y compensa la deriva del giroscopio.
- **Velocidad angular $$\dot{\theta}$$**: directamente del giroscopio.
- **Posición y velocidad $$x, \dot{x}$$**: a partir de los **encoders** de las ruedas.

### 6. Simulación

Antes de tocar el hardware, el controlador se prueba en simulación en **MATLAB/Simulink** sobre el **modelo no lineal**, incluyendo saturación del voltaje, ruido de los sensores, retardo de muestreo y perturbaciones, para validar las ganancias y la robustez.

### 7. Implementación embebida en el ESP32

- **Lazo de control a frecuencia fija** con interrupción de temporizador.
- Lectura de la **IMU por I2C** y de los **encoders por interrupciones**.
- Cálculo de $$u = -K\mathbf{x}$$, **compensación de la zona muerta**, **saturación** y salida **PWM** al puente H.
- **Parada de seguridad** cuando la inclinación supera un límite.
- **Telemetría** de los estados para ajustar $$Q$$ y $$R$$ con datos reales.

### 8. Pruebas y ajuste

Se evalúa el equilibrio estático, la respuesta ante empujones (perturbaciones) y el comportamiento al desplazarse, ajustando $$Q$$ y $$R$$ hasta lograr un compromiso entre estabilidad, rapidez de respuesta y consumo de los motores.

### Mi aporte

- **Modelado y diseño del controlador LQR en MATLAB**, incluida la simulación del modelo no lineal.
- **Programación embebida en el ESP32**: lazo de control en tiempo real, lectura de la IMU y los encoders, **filtro de Kalman** y salida PWM a los motores.
- Ajuste experimental de $$Q$$ y $$R$$ en el prototipo.

**Tecnologías:** ESP32 · C/C++ · Control en espacio de estados · LQR · Filtro de Kalman · IMU · Encoders · PWM · MATLAB/Simulink
