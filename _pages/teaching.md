---
layout: page
permalink: /teaching/
title: teaching
description: Course materials, schedules, and resources for classes taught.
nav: false # TODO: pon "true" si en algún momento impartes clases/prácticas y quieres mostrar esta página
nav_order: 6
calendar: true
---

<!-- TODO: si activas esta página, añade tus cursos en _teachings/ (borra los ejemplos de data-science y machine learning que trae la plantilla si no aplican) -->

{% include calendar.liquid calendar_id='test@gmail.com' timezone='Asia/Shanghai' %}

{% include courses.liquid %}
