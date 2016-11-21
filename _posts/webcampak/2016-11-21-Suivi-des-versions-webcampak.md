---
layout: page
subheadline: "Software"
title: "Suivi des versions Webcampak"
date: 2016-11-21 10:00:00+00:00
teaser: "Nous en sommes à notre second version du Webcampak 3. Moment idéal pour préciser un peu plus notre plan concernant les versions Webcampak."
header:
    image_fullwidth: "webcampak-to-pictures.png"
    caption: Un de nos Webcampak de test
    caption_url: "http://www.webcampak.com"
image:
    thumb:  webcampak-to-pictures_thumb.png
    homepage: webcampak-to-pictures.png
categories:
    - bug
    - software
comments: false
show_meta: true
---

Nous avons très récemment sorti la version 3.0.1 du Webcampak, à peine deux semaines après la version 3.0.0 et vous vous demandez (légitimement) quelle est la signification de ces numéros de versions.

Une incrémentation du dernier chiffre indique que les changements associés à cette mise à jour ne vont pas casser la compatibilité avec la version précédente. Par exemple le migration de la version 3.0.3 vers la version 3.0.4 ou de la version 3.0.1 vers la version 3.0.7 devrait être simple et peu risquée.

Une incrémentation du second chiffre indique un changement pouvant potentiellement impacter la configuration existante. Par exemple une modification de la structure des fichiers de configuration des sources. La migrations vers cette version doivent donc se faire avec précaution. Par exemple migrer de la version 3.0.10 vers la version 3.1.0. Nous essayerons autant que possible de bien documenter la procédure de migration vers toute version majeure.

Une incrémentation du premier chiffre indique une mise à jour majeure de l'application (changement de framework, nouvelle fonctionalité ayant un impact sur l'ensemble du système, ...). Dans ce cas précis, il sera probablement conseillé de réaliser une installation fraiche du système. Par exemple migrer de la version 3.1.10 vers la version 4.0.0

Voilà en espérant avoir été clair sur notre plan concernant les numéros de versions.

