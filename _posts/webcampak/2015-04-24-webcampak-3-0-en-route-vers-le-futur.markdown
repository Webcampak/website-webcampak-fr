---
layout: page
subheadline: "Roadmap"
title: "Webcampak 3.0 - Development on track"
date: 2015-04-24 19:07:50+00:00
teaser: "Un manque d'activités sur le blog ne signifie pas que le projet Webcampak est à l'arrêt, bien au contraire. La troisième version majeure du Webcampak est en préparation depuis quelques semaines et apportera son lot de nouveautés et d'améliorations."
header:
    image_fullwidth: "blog/2015/07/webcampak-login-large.png"
    caption: Webcampak lost password screen
    caption_url: "http://www.webcampak.com"
image:
    thumb:  blog/2015/07/webcampak-login_150x150.jpg
    homepage: blog/2015/07/webcampak-login-large.png
categories:
    - logiciel
comments: false
show_meta: true
---
Parmi les nombreuses fonctionnalités dans les tuyaux, nous sommes actuellement en train de complètement ré-écrire l'interface d'administration. L'objectif est toujours de donner un maximum de contrôle et d'autonomie à nos clients dans l'utilisation de leur Webcampak(s). En faisant une utilisation plus poussée de nos APIs REST, chaque Webcampak pourra faire office de centre de contrôle pour les autres Webcampak, permettant une configuration centralisée, le tout sans nécessiter de serveur spécifique.

[![]({{ site.urlimg }}blog/2015/07/webcampak-sources_600x420.png)]({{ site.urlimg }}blog/2015/07/webcampak-sources.jpg)

Il y a quelques années le Webcampak faisait ses premiers pas dans le cloud, il va dorénavant mettre le pied dans le "BigData".

Nous allons aussi améliorer la gestion transfert de données et en particulier dans les situations tendues (rythme de capture supérieur à la bande passante, panne électrique sur le dispositif de stockage de masse pour les projets à forte cadence, ...). Nos process existant nous permettent d'êtres avertis en cas d'incident et les différents mécanismes dont nous disposons (principalement un cache volumineux) nous permettent d'éviter de perdre les clichés. Nous allons ajouter une couche d'automatisation complémentaire pour limiter encore les interventions en cas d'incident en donnant au Webcampak la capacité de déterminer par lui même si incident est terminé et si il peut transférer les clichés qu'il a stocké dans son cache pendant un incident.

Au niveau matériel, nous visons une baisse de la consommation, un support natif de la 4G/LTE et probablement un boitier plus compact.

De nombreuses autres nouveautés devraient suivre, stay tuned.

{% include list-posts.html tag='header' %}
