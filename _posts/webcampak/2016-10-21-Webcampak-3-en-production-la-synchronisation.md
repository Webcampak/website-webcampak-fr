---
layout: page
subheadline: "Corporate"
title: "Webcampak 3.0 en production - La synchronisation"
date: 2016-10-21 10:00:00+00:00
teaser: "Second billet détaillant les fonctionalités du Webcampak, nous allons nous pencher un peu plus en détails sur le dispositif de synchronisation des clichés."
header:
    image_fullwidth: "webcampak-to-pictures.png"
    caption: Un de nos Webcampak de test
    caption_url: "http://www.webcampak.com"
image:
    thumb:  webcampak-to-pictures_thumb.png
    homepage: webcampak-to-pictures.png
categories:
    - corporate
    - software
comments: false
show_meta: true
---

## Synchronisation de fichiers

Ce nouveau module, que nous avons appellé, "Sync-Reports", permet à nos clients de répondre aux problématiques suivantes:

* S'assurer que tous les clichés ont correctement étés transférés sur un serveur distant
* Ajouter un nouveau serveur distant et y transférer l'ensemble des clichés
* Transférer les clichés n'ayant pas étés transférés du fait d'une panne réseau

### Fonctionnement du système

Le fonctionnement est assez simple, une fois une demande de rapport créée, le Webcampak va comparer les fichiers situés à deux emplacement différents. Il utilisera pour comparer chaque fichier, son nom, son emplacement et sa taille. 

Le Webcampak va ensuite générer un rapport, qui pourra ensuite être utilisé pour initier le transfer des fichiers manquants.

### Création du rapport

Lors de la création du rapport, l'utilisateur renseigne la source et la destination qu'il souhaite comparer.

[![]({{ site.urlimg }}webcampak.sync.create_600x196.png)]({{ site.urlimg }}webcampak.sync.create.png)

Le rapport est ensuite placé dans une file d'attente et est traité.

[![]({{ site.urlimg }}webcampak.sync.queue_600x271.png)]({{ site.urlimg }}webcampak.sync.queue.png)

### Analyse du rapport

Le rapport affiche des informations sur les clichés présents sur la source, présents sur la destination, communs entre les deux, absent de la source ou absent de la destination.

[![]({{ site.urlimg }}webcampak.sync.large_600x232)]({{ site.urlimg }}webcampak.sync.large_600x232)

Il ne reste plus qu'à cliquer sur "Re-run & Sync" pour déclencher le transfer des fichiers.

