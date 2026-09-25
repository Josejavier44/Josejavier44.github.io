# Tu web personal — próximos pasos

Este sitio está construido con [al-folio](https://github.com/alshedivat/al-folio), la plantilla académica más usada en Jekyll + GitHub Pages. Ya está personalizado con lo que se sabía de ti (afiliación al IFT-UAM/CSIC, beca FPU24/02041, tus líneas de investigación y tus dos publicaciones conocidas), **ya está subido a tu cuenta de GitHub y publicado en https://josejavier44.github.io/**. Falta rellenar los datos que solo tú tienes.

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

## 4. Ya está publicado — cómo actualizarlo a partir de ahora

Tu repositorio es `Josejavier44/Josejavier44.github.io`, ya con git inicializado y conectado a GitHub. La carpeta en tu escritorio ("Página web") es tu copia de trabajo. Para publicar cualquier cambio futuro (rellenar un TODO, subir tu foto, añadir una publicación nueva):

```bash
git add -A
git commit -m "Describe aquí qué cambiaste"
git push
```

En cuanto hagas `push` a `master`, el workflow `Deploy site` (en `.github/workflows/deploy.yml`) reconstruye la web automáticamente y GitHub Pages la publica en un par de minutos en https://josejavier44.github.io/. Puedes seguir el progreso en la pestaña **Actions** de tu repositorio en GitHub.

## 5. Cosas que dejé desactivadas por si no las necesitas (puedes reactivarlas)

- **Blog** (`_pages/blog.md`, `nav: false`): la plantilla trae ~30 entradas de ejemplo que muestran cómo usar cada función (vídeo, tablas, Jupyter, diagramas...). Bórralas o sustitúyelas por tus propias entradas antes de activarlo.
- **Teaching** (`_pages/teaching.md`, `nav: false`): actívalo si en algún momento impartes clases o prácticas.
- **People/Repositories** (`_pages/profiles.md`, `_pages/repositories.md`, `nav: false`): la primera es para páginas de grupo/lab; la segunda muestra tus repos de GitHub automáticamente en cuanto rellenes tu usuario en `_data/socials.yml` y `_data/repositories.yml`.
- **Books** (`_pages/books.md`): estantería de lecturas, ya estaba oculta del menú por defecto en la plantilla.

## 6. Nota sobre tamaño de descarga

Para que la descarga no pesara demasiado, quité `assets/video/`, `assets/audio/` y `assets/plotly/` (los ejemplos que usan las entradas de blog de demostración sobre cómo incrustar vídeo, audio y gráficos Plotly — nada de eso está enlazado en el menú). Si algún día activas el blog y quieres esas entradas de ejemplo concretas, puedes recuperar esos archivos desde el repositorio original: [github.com/alshedivat/al-folio](https://github.com/alshedivat/al-folio).

## 7. Tu web ya está publicada

**https://josejavier44.github.io/** — el repositorio es `Josejavier44/Josejavier44.github.io`, el despliegue via GitHub Actions (`.github/workflows/deploy.yml`) está funcionando, y GitHub Pages sirve la rama `gh-pages` que ese workflow genera.

Por el camino, el primer despliegue falló dos veces porque algunos de los campos que dejé como "pendiente" en `_data/socials.yml` y `_data/cv.yml` estaban con un valor vacío (`campo: ` sin nada detrás). Jekyll interpreta eso como `null`, y el plugin de redes sociales intenta construir una URL concatenando texto con ese valor nulo, lo cual rompe todo el build. Ya lo arreglé (los campos sin valor están comentados con `#` o llevan `""` en vez de estar vacíos). **Ten esto en cuenta cuando rellenes los TODOs que quedan**: para añadir un dato nuevo, quita el `#` de delante y escribe el valor; nunca dejes `campo:` sin nada después de los dos puntos.

## 8. Comprobaciones que hice

- La configuración YAML de todas las páginas y archivos de datos modificados es válida.
- Las entradas de `_bibliography/papers.bib` tienen las llaves bien balanceadas.
- El _style contract_ del propio repositorio (`npm run lint:style-contract`) pasa correctamente.
- El workflow de despliegue (`Deploy site`) se ejecutó de verdad en GitHub Actions y terminó en verde; GitHub Pages confirma el sitio como `built`.

## Documentación completa

Toda la documentación original de la plantilla sigue en `docs/CUSTOMIZE.md` y `docs/INSTALL.md` — es la referencia más completa si quieres ir más allá de esta guía rápida.
