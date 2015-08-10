---
layout: page
subheadline: "Corporate"
title: "Nouveau site web"
date: 2015-08-10 10:00:00+00:00
teaser: "Nous utilisions Wordpress depuis plusieurs années pour gérer notre site web et il était temps d'en changer..."
header:
    image_fullwidth: "blog/2015/08/jekyll-banner.png"
    caption: Jekyll website builder
    caption_url: "http://jekyllrb.com/"
image:
    thumb:  blog/2015/08/jekyll-banner_150x150.png
    homepage: blog/2015/08/jekyll-banner_150x150.png
categories:
    - corporate
comments: false
show_meta: true
---
Nous avons donc réalisé une migration vers [jekyll](http://jekyllrb.com/).

Jekyll peut être considéré comme un compilateur de sites web. Il analyse des templates, des fichiers markdown et génère le site web correspondant.

Vu que Jekyll n'utilise pas de fichiers PHP, les besoins de mise à jour et les risques de sécurité en sont grandement réduit. De plus, Github supportant Jekyll nativement, nous pouvons tout héberger là bas.

{% include list-posts.html tag='header' %}