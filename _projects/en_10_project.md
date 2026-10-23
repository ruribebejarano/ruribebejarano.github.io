---
layout: page
lang: en
permalink: /en/projects/10_project/
title: Self-balancing robot with LQR control
description: Two-wheeled inverted pendulum with an ESP32, Kalman-filter state estimation and optimal LQR control designed in MATLAB.
img: assets/img/proj_lqr.jpg
stack: ["ESP32", "LQR", "Kalman filter", "MATLAB", "State space"]
importance: 1
category: control and robotics
---

**Modern control · Academic project · ESP32 + MATLAB**

A two-wheeled robot that keeps its own balance: an **inverted pendulum on wheels**. It is **unstable in open loop** and **underactuated** (two motors must control both the body angle and the robot's position at the same time), which makes it a classic case for **state-space control** with an optimal **LQR** regulator.

<div class="row justify-content-sm-center">
  <div class="col-sm-9 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/lqr_robot.jpg" title="Self-balancing robot" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Prototype: three-level chassis with threaded rods, two DC gear motors with encoders, battery pack and the control electronics on top.</div>

### 1. Mathematical modeling

The robot is modeled as a body (pendulum) pivoting on the axle of two wheels. The **Euler-Lagrange** (or Newton) equations give the nonlinear equations of motion, including the DC motor dynamics (torque constant $$K_t$$, back-EMF constant $$K_e$$ and armature resistance $$R_a$$), so that the input is the applied **voltage**.

The state vector is

$$
\mathbf{x} = \begin{bmatrix} x & \dot{x} & \theta & \dot{\theta} \end{bmatrix}^T
$$

where $$x$$ is the wheel position and $$\theta$$ the body tilt. Linearizing around the upright equilibrium ($$\theta = 0$$) gives

$$
\dot{\mathbf{x}} = A\,\mathbf{x} + B\,u, \qquad y = C\,\mathbf{x}
$$

### 2. Parameter identification

The model is only useful if its parameters are real:

- Body and wheel **masses**, wheel **radius** and **center-of-mass height**.
- Body **moment of inertia** (for example, with a pendulum test).
- **Motor parameters** from step responses and current/speed measurements, including the gear motor's **dead zone**.

### 3. System analysis

- The **eigenvalues** of $$A$$ show a pole in the right half-plane: the system is unstable without control.
- **Controllability** is checked with $$\operatorname{rank}\,[B \;\; AB \;\; A^2B \;\; A^3B] = 4$$, and **observability** with the measured outputs (angle and encoders).

### 4. LQR controller design

LQR computes the feedback gain $$u = -K\mathbf{x}$$ that minimizes

$$
J = \int_0^{\infty} \left( \mathbf{x}^T Q\, \mathbf{x} + u^T R\, u \right) dt
$$

by solving the **algebraic Riccati equation**, with $$K = R^{-1}B^T P$$. Matrix $$Q$$ penalizes the error in each state (especially $$\theta$$ and $$\dot{\theta}$$) and $$R$$ the control effort; **Bryson's rule** is a good starting point before tuning experimentally. Unlike one PID per loop, LQR controls **all states at once**, balancing angle and position with a single control law.

The gain $$K$$ is computed in **MATLAB** (`lqr` / `dlqr`). Since the controller runs on the **ESP32**, the model is **discretized** with the sampling period $$T_s$$ and the discrete-time LQR is used.

### 5. State estimation

Not every state is measured directly, so they are estimated:

- **Angle $$\theta$$**: fusion of the accelerometer (accurate in the long term, noisy) and the gyroscope (accurate in the short term, drifts) with a **Kalman filter**, which estimates the angle and compensates for gyroscope drift.
- **Angular rate $$\dot{\theta}$$**: directly from the gyroscope.
- **Position and velocity $$x, \dot{x}$$**: from the wheel **encoders**.

### 6. Simulation

Before touching the hardware, the controller is tested in simulation in **MATLAB/Simulink** on the **nonlinear model**, including voltage saturation, sensor noise, sampling delay and disturbances, to validate the gains and robustness.

### 7. Embedded implementation on the ESP32

- **Fixed-rate control loop** driven by a timer interrupt.
- **IMU over I2C** and **encoders via interrupts**.
- Computing $$u = -K\mathbf{x}$$, **dead-zone compensation**, **saturation** and **PWM** output to the H-bridge.
- **Safety cutoff** when the tilt exceeds a limit.
- State **telemetry** to tune $$Q$$ and $$R$$ with real data.

### 8. Testing and tuning

Static balance, response to pushes (disturbances) and behavior while moving are evaluated, tuning $$Q$$ and $$R$$ until reaching a good trade-off between stability, response speed and motor effort.

### My contribution

- **Modeling and LQR controller design in MATLAB**, including simulation of the nonlinear model.
- **Embedded programming on the ESP32**: real-time control loop, IMU and encoder reading, **Kalman filter** and PWM output to the motors.
- Experimental tuning of $$Q$$ and $$R$$ on the prototype.

**Technologies:** ESP32 · C/C++ · State-space control · LQR · Kalman filter · IMU · Encoders · PWM · MATLAB/Simulink
