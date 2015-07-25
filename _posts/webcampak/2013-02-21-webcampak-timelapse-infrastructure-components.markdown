---
layout: page
subheadline: "Tech"
title: "Les composants d'une infrastructure Webcampak (1/4)"
date: 2013-02-21 15:41:27+00:00
teaser: "Les solutions que nous mettons en place sont habituellement répartis sur trois niveaux:"
header:
    image_fullwidth: "blog/2013/02/Webcampak-Typical-Install-blank-110-1024x961.png"
    caption: Webcampak infrastructure highlight
    caption_url: "http://www.webcampak.com"
image:
    thumb:  blog/2013/02/Webcampak-Typical-Install-blank-110-150x150.png
    homepage: blog/2013/02/Webcampak-Typical-Install-blank-110-1024x961.png
categories:
    - tech
comments: false
show_meta: true
redirect_from:
    - /fr/2013/02/21/webcampak-timelapse-infrastructure-components/
    - /en/2013/02/21/webcampak-timelapse-infrastructure-components/
    - /2013/02/21/webcampak-timelapse-infrastructure-components/
---
  * Les équipements sur site, dédiés à l'acquisition et au traitement des clichés
  * L'infrastructure centrale Webcampak Cloud et son stockage redondant
  * L'infrastructure distante du client

[![]({{ site.urlimg }}blog/2013/02/Webcampak-Typical-Install-blank-110-1024x961.png)]({{ site.urlimg }}blog/2013/02/Webcampak-Typical-Install-blank-110.png)

Evidemment, ceci n'est qu'un exemple, et de nombreuses variations sont possibles, notamment en ne raccordant pas un Webcampak aux infrastructure centrales Webcampak Cloud.

### Les équipements sur site

Un Webcampak peut être directement raccordé à Internet par une liaison filaire (ADSL, Cable, ...) où sans-fil (Wi-Fi, 3G, 4G/LTE).

Dans ce cas de figure le nombre d'équipements à installer sur site est limité mais la performance de l'accès Internet aura un impact sur la configuration mise en place:

  * L'ensemble des clichés (RAW + JPG) peuvent êtres transmis, sous réserve d'un rythme de capture faible et d'une bonne performance de l'accès Internet. Par exemple, un transfert RAW + JPG, au rythme d'une image toutes les 10 minutes, nécessitera environ 50ko/s de bande passante. La mémoire interne du Webcampak permettra de stocker environ 70 jours de clichés en cas de panne de l'accès Internet.
  * En ne capturant et ne transmettant que les clichés JPG, au rythme d'une image toutes les 10 minutes, seuls 10ko/s seront nécessaires (T3I/T4I 18 Mpix), où encore un rythme de capture maximal d'une image par minute pour une bande passante de 1Mbps (120ko/s). La mémoire interne du Webcampak permettra de stocker environ 370 jours de clichés (1 image toutes les 10mn) en cas de panne de l'accès Internet.
  * Conserver les clichés en interne, et ne transmettre qu'une version redimensionnée (par exemple 1920x1280) sur Internet. Il est possible de s'adapter à tous types de contraintes et autres limitations associées à l'accès Internet. Les clichés restent ici stockés au sein du Webcampak.
  * Enfin, n'utiliser l'accès Internet que dans un but de supervision. Dans ce cas de figure, l'utilisation de l'accès Internet est extrêmement faible.

Notez néanmoins que stocker l'ensemble des clichés au sein du Webcampak comporte un risque. Par exemple en cas de vol ou de dégradation du Webcampak vous perdez l'ensemble des clichés qui n'ont pas étés sauvegardés sur un stockage externe.

Pour s'affranchir des contraintes de bande passante, en particulier pour les projets composés de plusieurs dispositifs de capture, il est possible d'y adjoindre un dispositif de stockage redondant.

Ce dispositif de stockage aura vocation à stocker les clichés dans leur résolution maximale (RAW et/ou JPG). Nous proposons habituellement un firewall matériel, permettant aussi bien de protéger l'infrastructure cliente d'un risque en provenance de l'infrastructure Webcampak, que de protéger l'infrastructure Webcampak d'un risque en provenance du réseau client.

Lorsqu'un dispositif de stockage réseau est mis en place sur site, il est possible de totalement adapter l'infrastructures aux contraintes de l'accès Internet, que ce soit en réduisant la taille des clichés envoyés et/ou en réduisant la fréquence à laquelle ces clichés seront envoyés sur Internet.

### Les équipements centraux Webcampak Cloud

Tout d'abord un petit rappel, l'utilisation de Webcampak Cloud n'est en rien impératif. Votre Webcampak peut fonctionner de manière totalement indépendante de nos infrastructures centrales, et ce, sans pertes de fonctionnalités.

Nos infrastructure centrales sont composées de la manière suivantes:

  * Des serveurs Webcampak Cloud, localisés en France et au Canada. Ces serveurs performants sont connectés sur des liens internet performants (100 Mbps) et disposent de stockage interne redondant (RAID-1).
  * Une plateforme de supervision réseau (nagios pour les connaisseurs), qui se charge de vérifier en permanence l'état de l'ensemble de nos Webcampak et des équipements installés (firewall, stockage réseau, ...).
  * Des dispositifs de stockage redondant, situés dans nos locaux. Ils archivent l'ensemble des clichés transitant par les serveurs Webcampak Cloud et offrent un niveau de redondance RAID-5. Ces dispositifs nous protègent d'une panne générale de nos serveurs Webcampak Cloud (incident majeur dans un de nos datacenter par exemple).

### Les infrastructures tierces

Les équipements Webcampak, qu'ils soient implémentés sur site ou en datacenter, peuvent interagir avec des infrastructures tierces.

Les clichés peuvent êtres envoyés, après un traitement automatisé définit à l'avance (découpe, ajout watermark, redimensionnement, ajout légende, ...), sur un site Internet pour affichage instantané de type "live-cam".

Les clichés peuvent aussi êtres envoyés automatiquement sur un dispositif de stockage tiers (dans les locaux du photographe par exemple), lui permettant un accès rapide aux clichés.