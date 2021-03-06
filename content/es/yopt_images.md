---
weight: 280
id: "yopt_images"
title: "Optimizar imágenes"
yahoo: "http://developer.yahoo.com/performance/rules.html#opt_images"
tags: ["images"]
locales: "es"
notoc: "true"
description: ""
---

Después de que un diseñador termina con la creación de las imágenes de tu sitio web, hay algunas cosas que usted puede probar antes de subir esas imágenes por FTP a su servidor.

- Usted puede revisar los GIFs y ver si ellos están usando una paleta de tamaño correspondiente al número de colores de la imagen. Con [imagemagick](http://www.imagemagick.org) es fácil usando `identify -verbose image.gif`. Cuando vea una imagen que usa 4 colores y una paleta de 256, es idónea para mejorarla.
- Pruebe convertir los GIFs a PNGs y vea si reducen su tamaño. Muchas veces no es así. Los desarrolladores a menudo dudan en utilizar PNGs debido al soporte limitado de los navegadores, pero eso es cosa del pasado. El único problema real es la transparencia-alpha en PNGs con color real, pero igual, los GIFs no son de color verdadero y tampoco soportan transparencia variable. Así que cualquier cosa que pueda hacer un GIF, un PNG con paleta (PNG8) también puede (excepto para animaciones). Este simple comando de imagemagick resulta totalmente seguro de usar con PNGs: `convert image.gif image.png` “Lo que estamos diciéndole es: Déle una oportunidad a los PNGs!”
- Ejecute [pngcrush](http://pmt.sourceforge.net/pngcrush/) (o cualquier otra herramienta optimizadora de PNGs) en todos sus PNGs. Por ejemplo: `pngcrush image.png -rem alla -reduce -brute result.png`
- Ejecute jpegtran en todos sus JPEGs. Esta herramienta realiza operaciones con los JPEG sin pérdida de calidad, tales como rotación, y además puede ser usado para optimizar y remover comentarios y otra información inútil (como la información EXIF) de sus imágenes. `jpegtran -copy none -optimize -perfect src.jpg dest.jpg`

   