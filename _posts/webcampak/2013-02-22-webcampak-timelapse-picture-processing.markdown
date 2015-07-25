---
layout: page
subheadline: "Tech"
title: "Traitement des images au sein de l'infrastructure Webcampak (2/4)"
date: 2013-02-22 15:41:38+00:00
teaser: "Avec Webcampak nous avons apporté une attention particulière à la sauvegarde des clichés, quitte à multiplier les emplacements où un même cliché peut être sauvegardé."
header:
    image_fullwidth: "blog/2013/02/Webcampak-Typical-Pictures-110-1024x961.png"
    caption: Webcampak infrastructure highlight
    caption_url: "http://www.webcampak.com"
image:
    thumb:  blog/2013/02/Webcampak-Typical-Pictures-110-150x150.png
    homepage: blog/2013/02/Webcampak-Typical-Pictures-110-1024x961.png
categories:
    - tech
comments: false
show_meta: true
redirect_from:
    - /2013/02/22/webcampak-timelapse-picture-processing/
    - /fr/2013/02/22/webcampak-timelapse-picture-processing/
    - /en/2013/02/22/webcampak-timelapse-picture-processing/
---

[![]({{ site.urlimg }}blog/2013/02/Webcampak-Typical-Pictures-110-1024x961.png)]({{ site.urlimg }}blog/2013/02/Webcampak-Typical-Pictures-110.png)

L'acquisition d'image, depuis l'appareil photo reflex peut se faire en JPG et RAW. Le choix de capturer en JPG ou en JPG+RAW est laissé à la libre appréciation de nos clients, une image RAW étant plus volumineuse qu'une image JPG, la faisabilité dépendra donc aussi des contraintes techniques propres au projet.

Une fois l'image acquise, le Webcampak peut y appliquer un premier traitement avant envoi et/ou archivage. Ce traitement permettra par exemple de réduire la taille des clichés (découpe / redimensionnement).

La première portion du schéma ci-dessus (Customer Site) illustre quelques exemples d'archivage et de traitement des images:

  * Un Webcampak peut capturer en RAW et JPG et transmettre l'ensemble des clichés à distance.
  * Un Webcampak peut capturer en RAW et JPG, archiver les clichés sur un stockage réseau local redondant, et envoyer les fichiers JPG à distance
  * Un Webcampak peut capturer en JPG et transmettre l'ensemble des clichés à distance.
  * Un Webcampak peut capturer en RAW et JPG, archiver les clichés sur un stockage réseau local redondant, et envoyer à distance une version réduite (1920x1280 par exemple) de l'image capturée.

Les images arrivent ensuite sur Webcampak Cloud, où elles peuvent subir un traitement complémentaire.

Une copie des clichés est automatiquement envoyée sur un dispositif redondant de forte capacité situé dans nos locaux.

Webcampak peut aussi envoyer une version des clichés sur un dispositif de stockage tiers. L'envoi progressif des clichés permet d'éviter de transférer l'ensemble des clichés en une seule fois en fin de projet (transfert pouvant être très long).

Enfin, Webcampak peut envoyer ses clichés (habituellement sous forme "hotlink") vers un site Internet pour un affichage public.

