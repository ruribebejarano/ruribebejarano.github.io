# ruribebejarano.github.io

Portafolio personal de **Ricardo Uribe Bejarano** — Ingeniería Electrónica (PUCP): sistemas embebidos, IoT industrial, control y robótica, sistemas de transporte inteligente y aprendizaje automático.

🌐 **Sitio:** https://ruribebejarano.github.io · **English:** https://ruribebejarano.github.io/en/

## Estructura

| Carpeta / archivo | Contenido |
| :--- | :--- |
| `_pages/` | Páginas (español) y sus versiones en inglés (`en_*.md`) |
| `_projects/` | Un archivo por proyecto (`N_project.md`) y su traducción (`en_N_project.md`) |
| `_bibliography/papers.bib` | Publicaciones |
| `_news/` | Novedades de la portada |
| `_data/ui.yml` | Textos de la interfaz en ES/EN |
| `_layouts/about.liquid`, `_includes/header.liquid` | Portada y barra de navegación personalizadas |
| `assets/css/main.scss` | Tema visual "tech oscuro" |
| `assets/img/` | Fotos y portadas de proyectos |

## Publicación

Cada `push` a `main` ejecuta `.github/workflows/deploy.yml`, que compila el sitio con Jekyll y lo publica en la rama `gh-pages`.

Para probarlo localmente: `bundle install && bundle exec jekyll serve`.

## Créditos

Basado en el tema [al-folio](https://github.com/alshedivat/al-folio) (licencia MIT, ver `LICENSE`).
