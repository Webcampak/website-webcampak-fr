---
layout: page
subheadline: "Software"
title: "Une histoire d'insecte ... et de migration."
date: 2016-10-26 10:00:00+00:00
teaser: "Avant toute mise en production nous testons l'ensemble des composants autant que possible. Parfois, tout ne se passe pas comme prévu..."
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

Comme vous le savez peut être, nous sommes actuellement en train de migrer nos serveurs cloud vers la nouvelle version du Webcampak. Les tests sont terminés et le système est maintenant prêt pour le déploiement.

## Stratégie de migration

Nous avons donc plusieurs terabytes de données à transférer entre nos serveurs. Pour limiter les risques d'incidents et d'interruptions, nous réalisons une migration Active/Active. 

La procédure est la suivante; nous installons le Webcampak sur un nouveau serveur, réalisons un duplicata des fichiers, reconfigurons le Webcampak distant pour envoyer les clichés vers le nouveau serveur à la place de l'ancien. Puis réalisons une nouvelle synchronisation des fichiers pour transférer les derniers clichés.

Cette procédure limite l'interruption et nous permet aussi de revenir en arrière facilement. 

Mais parfois tout ne se passe pas comme prévu ...


## Synchronisation des clichés

Nous avons donc commencé à transférer les clichés, mais maintenant que nous avons cette fonctionalité de synchronisation des clichés, nous avons décidé de l'utiliser à la place de [Rsync](https://fr.wikipedia.org/wiki/Rsync).

Nul doute qu'avec Rsync la manipulation aurait été plus rapide, une seule commande pour copier l'ensemble des clichés pour l'ensemble de nos clients sur le serveur. Mais utiliser notre fonctionalité de synchronisation, bien qu'ayant à initier le transfer pour chacun de nos clients, nous permet aussi de réaliser un peu de test de charge.

## Un nombre de clichés importants

Et ce fut le drame...

Nous exagèrons un peu étant donné l'absence d'impact pour nos clients. Mais ça a mis en lumière un point que nous n'avions pas validé lors de nos tests. Nous avions testé avec quelques milliers de fichiers, plus précisément les 8640 clichés capturés lors des vieilles charrues 2011.

Aucuns problèmes lors des différents tests de transfer, dans les deux sens (disant vers local ou local vers distant).

Revenons donc au sujet de ce billet, l'étape suivante consistait donc à sauvegarder une "vraie" source, un projet en cours et ses plus de 58300 clichés pour plus de 200GB (ci-dessous).

[![]({{ site.urlimg }}webcampak.sync.large_600x232.png)]({{ site.urlimg }}webcampak.sync.large.png)

Etant confiant, autant lancer quelques synchronisations en parralèlle pour les différents clients à migrer.

L'application de visualiation des rapports devint inaccessible... Impossible de consulter les rapports, remplacés par des messages d'erreurs en provenance de notre API.

## Un diagnostique rapide

Trouver la cause du soucis n'a pas été très complexe. 

Pour améliorer la réactivité du système et économiser les resources système, en particulier pour les Webcampak installés sur site, nous avons tendance à privilégier le stockage d'information système par rapport au calcul ou à la génération de ces informations. L'espace disque pour ce type de fichiers est rarement problématique, et dans ce cas précis nous stockions tout simplement beaucoup, beaucoup, trop d'informations.

Le rapport stockait la liste des fichiers présents sur la source, sur la destination, les fichiers communs entre les deux source, les fichiers manquants sur la source et enfin les fichier manquants sur la destination. 

Beaucoup trop, d'autant plus qu'à court terme seul les fichiers manquants sur la destinations (les fichiers à transférer) nous étaient utiles.

La solution a donc consisté à supprimer les informations inutiles et compresser (GZip) la liste des fichiers manquants dans un fichier à part (cette liste n'étant utilisée qu'une seule fois). Nous ne conservons dans ce rapport que quelques statistiques (nombre de fichiers, taille).

Quelques lignes de code plus tard et les informations inutiles (pour le moment) enlevés, tout était rentré dans l'ordre, avec un rapport de synchronisation passant de 70MB à 1.7MB. 
Nous aurions pût pousser encore plus loin et ne pas conserver la liste, faisant passer le rapport de synchronisation à 3.9KB mais nous aurions perdu un historique pouvant se révéler utile pour de futures fonctionalités.

Voici notre insecte (bug) identifié et éliminé, nous pouvons reprendre nos activités.
