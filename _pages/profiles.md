---
layout: profiles
permalink: /resumen/
title: Resumen
description: Síntesis de resultados encontrados dento del análisis.
nav: true
nav_order: 5

profiles:
  #Todas las tablas del markdown fueron convertidas desde el codigo a formato md por chatgpt
  #El align center fue escrito por chatgpt, su código es de la linea 12 a 21 en profiles.html
  - align : right 
    content : about_pregunta1.md
  - align : center
    image: preguntauno.png
    image_circular: False 
  - align: left 
    content: about_correlacion.md
  - align : center 
    image: correlacion.png
    image_circular: False # crops the image to make it circular
    more_info: >
      <p>Variable independiente (x) = Total de habitantes</p>
      <p>Variable dependiente (y) = Centro de salud por comuna</p>
  - align : left 
    content: about_regresion.md
  - align : center  
    image : regresion1.png
    image_circular: False
  - align : center 
    image : boxplotdensidad.png
    image_circular : False
  - align : right 
    content : about_complejidad.md
    image_circular : False 
  - align : right 
    content : about_tiposervicio.md
  - align : center 
    image : urgencias.png
  - align : center 
    image : complejidadnivel.png
    image_circular : False 
  - align : right 
    content : about_farmacias.md 
  - align : center 
    image : farmaciasreg.png 
    image_circular : False
  - align : left 
    content: about_privpublic.md
  - align : center 
    image : privpublic.png
    image_circular : False 
  - align : center 
    image : distribucionp4.png
    image_circular : False 
  - align : center 
    image : corrp4.png 
    image_circular: False 
  - align : right
    content: about_grupo.md
  - align : center 
    image : clusterstgo.png 
    image_circular : False 
  - align : center 
    image : p5maule.png 
    image_circular : False 
  - align : center 
    image : clusterarica.png 
    image_circular : False
---