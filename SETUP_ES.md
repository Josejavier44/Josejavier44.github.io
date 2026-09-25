# Tu web personal — próximos pasos

Este sitio está construido con [al-folio](https://github.com/alshedivat/al-folio), la plantilla académica más usada en Jekyll + GitHub Pages. Ya está personalizado con lo que se sabía de ti (afiliación al IFT-UAM/CSIC, beca FPU24/02041, tus líneas de investigación y tus dos publicaciones conocidas). Falta rellenar los datos que solo tú tienes.

## 1. Datos que tienes que rellenar (buscar "TODO" en el proyecto)

Puedes buscar todos los pendientes con: `grep -rn "TODO" .` (o con el buscador de tu editor).

- **`_config.yml`**: tu apellido completo (`last_name`), y más abajo, en el bloque `scholar:`, tu apellido otra vez (debe coincidir con el de `_bibliography/papers.bib`).
- **`_pages/about.md`**: foto (`assets/img/prof_pic.jpg`), despacho si quieres mostrarlo, y un par de frases más personales.
- **`_bibliography/papers.bib`**: la lista real de autores de cada trabajo (ahora mismo dice `[TU NOMBRE] and [COAUTOR 1] and [COAUTOR 2]`) y el DOI del artículo de Phys. Rev. D.
- **`_data/socials.yml`**: tu GitHub, ORCID, INSPIRE-HEP, Google Scholar, LinkedIn, etc. (todos son opcionales, pero cuantos más pongas, más completo se ve el perfil).
- **`_data/cv.yml`**: formación (universidad, fechas), fecha de inicio del doctorado, idiomas, y los autores reales en la sección de publicaciones.
- **`_data/coauthors.yml`**: añade a tus coautores (empezando por Yashar Akrami) para que se enlacen automáticamente en la lista de publicaciones.

## 2. Foto de perfil

Sustituye `assets/img/prof_pic.jpg` por tu foto (cuadrada funciona mejor).

## 3. Previsualizar en local (opcional pero recomendado)

```bash
bundle install
bundle exec jekyll serve
```

Y abre `http://localhost:4000/` (o la URL que indique la terminal) en el navegador.

## 4. Publicarlo en GitHub Pages

1. Crea un repositorio nuevo en GitHub. Si lo llamas **exactamente** `TU-USUARIO.github.io`, tu web quedará en la raíz (`https://TU-USUARIO.github.io/`) y `baseurl` en `_config.yml` debe quedar vacío (ya está así). Si lo llamas de otra forma (p. ej. `web-personal`), tu web quedará en `https://TU-USUARIO.github.io/web-personal/` y tienes que poner `baseurl: /web-personal` en `_config.yml`.
2. Esta carpeta se entrega sin historial de git (para que la descarga no pese los ~50 MB extra del historial de la plantilla original). Dentro de la carpeta, inicializa un repositorio nuevo y súbelo:
   ```bash
   git init
   git add -A
   git commit -m "Primera versión de mi web personal"
   git remote add origin https://github.com/TU-USUARIO/TU-REPOSITORIO.git
   git branch -M main
   git push -u origin main
   ```
3. En GitHub, ve a **Settings → Pages** de tu repositorio y activa el despliegue automático (el propio repositorio ya trae un workflow de GitHub Actions en `.github/workflows/` que hace el `build` y `deploy` por ti al hacer `push`).
4. Actualiza `url:` en `_config.yml` con la URL final una vez la tengas.

## 5. Cosas que dejé desactivadas por si no las necesitas (puedes reactivarlas)

- **Blog** (`_pages/blog.md`, `nav: false`): la plantilla trae ~30 entradas de ejemplo que muestran cómo usar cada función (vídeo, tablas, Jupyter, diagramas...). Bórralas o sustitúyelas por tus propias entradas antes de activarlo.
- **Teaching** (`_pages/teaching.md`, `nav: false`): actívalo si en algún momento impartes clases o prácticas.
- **People/Repositories** (`_pages/profiles.md`, `_pages/repositories.md`, `nav: false`): la primera es para páginas de grupo/lab; la segunda muestra tus repos de GitHub automáticamente en cuanto rellenes tu usuario en `_data/socials.yml` y `_data/repositories.yml`.
- **Books** (`_pages/books.md`): estantería de lecturas, ya estaba oculta del menú por defecto en la plantilla.

## 6. Nota sobre tamaño de descarga

Para que la descarga no pesara demasiado, quité `assets/video/`, `assets/audio/` y `assets/plotly/` (los ejemplos que usan las entradas de blog de demostración sobre cómo incrustar vídeo, audio y gráficos Plotly — nada de eso está enlazado en el menú). Si algún día activas el blog y quieres esas entradas de ejemplo concretas, puedes recuperar esos archivos desde el repositorio original: [github.com/alshedivat/al-folio](https://github.com/alshedivat/al-folio).

## 7. Comprobaciones que ya hice por ti

- La configuración YAML de todas las páginas y archivos de datos modificados es válida.
- Las entradas de `_bibliography/papers.bib` tienen las llaves bien balanceadas.
- El *style contract* del propio repositorio (`npm run lint:style-contract`) pasa correctamente.
- No pude ejecutar `bundle install` completo en este entorno (la política de red de este espacio de trabajo bloquea rubygems.org), así que antes de darlo por definitivo, haz una build local (`bundle exec jekyll build`) o simplemente súbelo a GitHub: el workflow de Actions del repositorio lo construirá y te avisará si algo falla.

## Documentación completa

Toda la documentación original de la plantilla sigue en `docs/CUSTOMIZE.md` y `docs/INSTALL.md` — es la referencia más completa si quieres ir más allá de esta guía rápida.
