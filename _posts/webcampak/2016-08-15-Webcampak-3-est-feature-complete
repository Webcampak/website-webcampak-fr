---
layout: page
subheadline: "Corporate"
title: "Webcampak 3.0 est 'feature complete'"
date: 2015-08-10 10:00:00+00:00
teaser: "Après presque 18 mois à travailler sur la nouvelle mouture du Webcampak, nous nous approchons de la fin du dévelopement"
header:
    image_fullwidth: "header_typewriter.jpg"
    caption: Image by Florian Klauer
    caption_url: "http://florianklauer.de/"
image:
    thumb:  typewriter_thumb.jpg
    homepage: homepage_typewriter.jpg
categories:
    - corporate
comments: false
show_meta: true
---

Comme avez put le constater, la mise à jour vers la version 3.0 a pris beaucoup plus de temps que prévu. Durant cette migration, nous avons changé de nombreux éléments clefs du système.

Le Webcampak est divisé en plusieurs composants, chacuns ayant un rôle précis dans le système.

# Le fonctionement interne

## L'interface graphique
L'interface a été entièrement ré-écrite pour devenir plus modulaire, structurée et permettre l'ajout plus facile de nouvelles fonctionalités.

Le framework Sencha Extjs/Touch 4.x a été remplacé par Sencha Extjs 6.x.

## L'API
Précédemment basée sur un framework PHP custom, l'API a été entièrement ré-écrite et est maintenant basée sur le framework Symfony.

## Le Core
La capture d'image est les opérations internes sont gérés par un coeur en Python, l'ensemble a été lui aussi ré-écrit et le framework CLI Cement est maintenant utilisé pour les appels à ces outils faisant parti du coeur du Webcampak.

Cette ré-écriture nous a aussi permis de nettoyer le code et enlever des fonctionalités qui n'étaient pas utilisées.

## La Base de Données

Nous essayons au maximum de limiter les dépendences à la base de données, mais elle reste nécessaire pour toute la partie base utilisateurs et authorisations. Nous avons migré la base de données de MySQL vers SQLite, ce qui rend l'ensemble un peu plus léger.

# Les fonctionalités

Mais ce qui vous intéressera probablement le plus sont les nouvelles fonctionalités et les changements du Webcampak qui vous impacterons au jour le jour.

Nous détaillerons prochainement ces différents changements, mais pour faire simple, un effort important a été dédié à rendre la gestion d'un ou d'une flotte de Webcampak plus simple, ainsi que de simplifier la gestion des incidents (panné réseau par exemple), voici une rapide liste de ces changements.

## Rapports de synchronisation
Le Webcampak est maintenant en mesure de comparer les photos qu'il a stocké en interne à une source distance. Et si des différences sont trouvés, l'utilisateur peut décider de transférer les fichiers manquants.

Ces rapports peuvent êtres générés à n'importe quel moment, et peuvent par exemple êtres utilisés pour re-synchroniser un nombre important de fichiers après une panne réseau.

## Xfer
La fonctionalité Xfer est une file d'attente pour les transfer de fichiers. Précédemment le transfer de fichier était sérialisé à la capture, avec Xfer ce transfer se déroule en parralèle des captures et vous permet de transférer à un rythme défini sans risquer de saturer le Webcampak.

Cette fonctionalité permet aussi de capturer, pour de courtes périodes, à un taux plus important que la bande passante disponible. La file d'attente Xfer se déroulant à son propre rythme.

## Emails
Le système envoie dorénavant de meilleurs emails résumant la capture du jour, et pour les utilisateurs possédant plusieurs Webcampak, un seul email est envoyé chaque jour (et non un email par Webcampak comme précédemment)

## Nouvelle interface mobile
Une nouvelle interface mobile a été développée, elle fourni plus de détails sur le bon déroulement des captures et permet de réaliser quelques manipulations simples.

# Et Ensuite ?

Nous allons maintenant entrer un phase de correction de bugs, et préparer Webcampak 3.0 pour son entrée en production. Une grande étape a été franchie !
