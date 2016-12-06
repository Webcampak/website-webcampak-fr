---
layout: page
subheadline: "Software"
title: "Mecanisme d'alerte automatisé"
date: 2016-12-01 10:00:00+00:00
teaser: "La clef du succès d'un project timelapse consiste à ne manquer ou ne perdre aucune image pendant toute la durée de l'installation. Les mécanismes d'alerte jouent un rôle clef car ils vous permette d'être informés du moindre soucis de capture. Dans ce billet nous allons détailler comment le Webcampak gère cet aspect et les améliorations que nous avons apporté au système."
header:
    image_fullwidth: "webcampak-to-alerts.png"
    caption: Configuration des alertes Webcampak
    caption_url: "http://www.webcampak.com"
image:
    thumb:  webcampak-to-pictures_thumb.png
    homepage: webcampak-to-alerts.png
categories:
    - alertes
    - software
comments: false
show_meta: true
---

Nous avons rapidement compris, lorsque nous avons dévelopé le système, que la gestion des alertes est un aspect tout aussi critique que sensible à mettre en place. Trop d'alertes créé une accoutumance (et diminue le niveau d'attention de la personne recevant les alertes), pas assez entraine des problématiques pertes de clichés. 

# Webcampak 2

Lors de nos précédentes versions, la gestion des alertes en série sur les captures d'images était très efficace. La configuration se faisait sur trois points:

* Définir le seuil d'alerte à partir duquel une alerte est envoyée (après X échecs de capture)
* Définir à quel fréquence envoyer un rappel
* Définit si l'on souhaite être alerté à chaque rétablissement de la capture (même si on reste sous le seuil d'alerte).

Aucune difficulté pour générer des alertes sur la source directement connecté à l'appareil photo, la capture a fonctionné ou non, c'est aussi simple que ça.

Là Webcampak manquait par contre de flexibilité sur les sources de consolidation, en particulier les sources distantes. Par exemple, un Webcampak sur site, capture à deux rythmes différents et envoi ses clichés sur le Cloud. Comment gérer cette différence de planning tout en prenant en compte de possibles retard causés par le réseau ?

Pour éviter l'envoi de faux positifs, la configuration des alertes sur le cloud devenait un jeu d'équilibriste demandant de la précision. 

# Webcampak 3

Nous avons donc réfléchi à une meilleure manière de réaliser cette configuraiton et d'envoyer les alertes corresondantes. La configuration peut dorénavant se réaliser de deux manières: 

* Sur un retard de capture
* Sur un calendrier

## Alerte sur retard de capture

Ce mode est le plus simple à configurer et reprend un concept très similaire au Webcampak 2. 

A intervale régulier le système calcule le temps écoulé depuis la dernière capture. Si ce temps se situe au dessus du seuil configuré, une alerte est envoyée.

Le système continue ensuite à vérifier l'état de la source, puis renvoie un email de rappel à intervale régulier jusque au retour en fonctionnement du système.

## Alerte sur calendrier

Le second mode consiste à définir à l'avance un calendrier de capture et vérifier que les images soient présentes au moment souhaité. 

En configurant le seuil d'alerte sous forme de créneaux de capture manqués, ce mode permet de gérer facilement un nombre illimité de rythmes de captures différents sur une même source.

Là aussi, le système configure à vérifier l'état de la source et renvoir un email de rappel à intervale régulier.

Il est aussi possible de définir une période de "grace", pour retarder la déclaration d'une alerte en cas de retard dans la transmission de l'image. 

## Deux modes compatibles

Les deux modes peuvent être utilisés simultanément. Il est par exemple possible de configurer le système pour déclencher une alerte sur la base du calendrier, plus envoyer un reminder toutes les heures (sur base du retard de capture), le tout pour plus de souplesse.

# Conclusion

Cette nouvelle fonctionalité permet de rendre la déclaration des alertes plus simple et aussi plus pertinente, en particulier pour les sources distantes.

Couplé à l'envoi journalier des statistiques de captures il devient quasiment impossible de rater un incident, ceci sans recevoir trop d'emails. 

