---
layout: profiles
permalink: /resumen/
title: Resumen
description: Resumen de los resultados del análisis
nav: true
nav_order: 6

profiles:
  # if you want to include more than one profile, just replicate the following block
  # and create one content file for each profile inside _pages/
  - align: right
    image: preguntauno.png
    content: about_pregunta1.md
    image_width: 800
    image_circular: False # crops the image to make it circular

  - align: left 
    image: correlacion.png
    content: about_correlacion.md
    image_circular: False # crops the image to make it circular
    more_info: >
      <p>Variable independiente (x) = Total de habitantes</p>
      <p>Variable dependiente (y) = Centro de salud por comuna</p>
  - align : left 
    image : regresion.png
    content: about_regresion.md
    image_circular: False
---