---
layout: page
subheadline: "Corporate"
title: "Webcampak 3.0 en production - Le transfer de fichiers"
date: 2016-10-20 10:00:00+00:00
teaser: "Depuis mi-Août nous testions la version 3 du Webcampak pour nous assurer qu'elle était prête pour son entrée en production"
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

Après de nombreuses ré-installations, redémarrages et coupures (controllées et impromptues) nous avons maintenant un système aussi stable que la version précédente, tout en amenant de nombreuses améliorations.

Ce billet est le premier d'une série détaillant les nouvelles fonctionalités de cette nouvelle version du Webcampak.

## Transfer de fichiers

Nous avons maintenant deux modes pour le transfer de fichier:

* le mode __série__, envoyant les fichiers dès leur capture par le Webcampak. Cette fonctionalité est la même que précédemment, après les manipulations choisies, les fichiers sont envoyés sur le serveur distant de votre choix.
* le mode __xfer__, place les fichiers dans une file d'attente et les envoie à la vitesse permise par la bande passsante disponible.

Ces deux modes fonctionnent en FTP, mais nous pouvons à tout instant, et simplement, ajouter de nouveaux modes de connexion.

[![]({{ site.urlimg }}webcampak.xfer.to_600x194.png)]({{ site.urlimg }}webcampak.xfer.to.png)

Ce nouveau mode __xfer__ répond à deux problématiques que nous avons rencontrés sur nos projets, les périodes de fortes augmentation du rythme de capture et les dégradations temporaires de la connectivité réseau.

### Augmentation du rythme de capture

Durant certaines phases du projet nos clients souhaitent parfois fortement augmenter la cadence de prise de clichés (par exemple un cliché toutes les 20 secondes). 
En mode série et pour éviter l'engorgement du système, il était nécessaire de s'assurer que l'ensemble du processus de capture soit terminé avant de démarrer le suivant. Et, selon le mode de capture sélectionné, la connectivitié réseau pouvait se révéler bloquante. 

Précédemment nous contournions de problème en désactivant temporairement l'envoi de fichier (nos Webcampak ont habituellement entre 250GB et 500GB de stockage local) pour ensuite re-synchroniser le tout progressivement. 

Ce nouveau mode permettra d'éviter de réaliser ces ajustements, le système continuera d'envoyer au rythme préalablement sélectionné, seule la taille de la file d'attente augmentera.

### Dégradations de la connectivité réseau

Ce problème est de loin le plus problématique car difficile à prévoir car non lié à nos infrastructure. Il est arrivé pour certains Webcampak que la bande passante baisse très fortement, ce qui en plus de retarder l'arrivée des clichés, créé un engorgement des resources sur le Webcampak en lui même.

Bien qu'étant équippé depuis de nombreuses versions d'un mécanisme permettant de décider combien de fois tenter l'envoi d'un cliché avant d'abandonner, la baisse de performances représente un challenge problématique dans le sens où l'envoi des clichés est fonctionnel. 
Le Webcampak n'avait donc pas conscience de cette difficulté (une coupure réseau est par contre facile à traiter et ne posait pas de problèmes) et commençait à empiler les processus de capture jusqu'à saturation.

### Fonctionnement du mode Xfer

Lorsque ce mode de transfer est utilisé, plusieurs files d'attentes sont crées, chacune de ces files d'attendre recevra un ordre de traitement pour l'envoi des fichiers. Les files d'attentes sont communes à l'ensemble du Webcampak et isolées des autres processus de traitement (une source envoi un ordre au système xfer, mais n'agit pas directement sur la file d'attente).

[![]({{ site.urlimg }}webcampak.sysconf_600x218.png)]({{ site.urlimg }}webcampak.sysconf.png)

La configuration se fait ensuite à plusieurs niveaux, lors de la configuration générale, nous indiquons au système le nombre des files d'attentes que nous voulons créer, et le nombre maximum de fichiers que peut contenir chaque file d'attente.

Ces paramètres varieront en fonction du type de matériel sur lequel le Webcampak est installé. Un serveur cloud controllant 50 Webcampak aura des réglages différents d'un Webcampak installé sur un chantier.

Ensuite lors de l'ajout d'un serveur distant, vous pourrez choisir d'activer le mode xfer et pourrez définir combien ce serveur distant pourra supporter d'envoie en parrallèle.

Le système s'assurera ensuite de répartir la charge de travail entre les différentes files d'attentes tout en respectant la configuration choisie.

[![]({{ site.urlimg }}webcampak.xfer.to_600x194.png)]({{ site.urlimg }}webcampak.xfer.to.png)

Par exemple, sur la capture d'écran ci-dessus, vous pouvez constater que le système dispose de 3 files d'attentes de configurées mais seules 2 sont utilisés.

### Avantages, Inconvénients

Le système xfer se révèle particulièrement intéressant dans les cas où la connectivité réseau peut être instable ou insuffisante pour transférer les clichés en temps réel. 

Il entraine néanmoins un possible délais dans l'envoi des clichés (par exemple si la file d'attente contient déjà des clichés) et une très légère augmentation de l'utilisation des resources locales.

Nous recommendons d'utiliser le mode xfer dans la majeure partie des cas, seuls certains cas précis tels que l'envoi d'une image "live" sur un site Web, font que le mode série conserve sa pertinence et c'est pourquoi le Webcampak conserve ces deux modes.
0
