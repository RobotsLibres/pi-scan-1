# Pi Scan vue d'ensemble

Pi Scan est un contrôleur d'appareil photo simple et robuste pour les scanners de livres. Il a été conçu pour fonctionner avec le [scanner de livres des archivistes] (http://diybookscanner.org/archivist). Pour toute question ou aide, visitez le [forum] (http://diybookscanner.org/forum) ou envoyez un courriel à l'aide à tenrec dot builders.

## Traductions : [Espanol](https://github.com/Tenrec-Builders/pi-scan/blob/master/README.es.md)
## Traductions : [French](https://github.com/Tenrec-Builders/pi-scan/blob/master/README.fr.md)

# Exigences

* Framboise Pi 2 ou Framboise Pi 3
* Deux appareils photo (Canon PowerShot A2500 ou Canon PowerShot ELPH 160 (alias IXUS 160) ou Nikon 1 J5)
* Trois cartes SD de 4 Go (2 pour les appareils photo, 1 pour Pi). Une doit être micro (pour les Pi). Les deux autres doivent être de taille standard ou avoir des adaptateurs.
* Un périphérique de stockage USB (soit un lecteur de carte SD et une carte SD rapide, soit une clé USB)
* Dispositifs de saisie (voir ci-dessous

# Options des dispositifs de saisie

Dans la mesure du possible, évitez d'utiliser un hub USB. Une grande partie des problèmes signalés par les utilisateurs ont été causés par un problème avec un hub USB qui a été résolu en branchant les appareils directement sur le Raspberry Pi.

Un problème connu est que les périphériques d'entrée USB ne fonctionnent que s'ils sont branchés avant le démarrage de Pi Scan. Si vous les branchez plus tard ou s'ils se débranchent, vous devrez alors redémarrer Pi Scan pour les faire fonctionner.

## Souris

Pi Scan peut être entièrement contrôlé via une souris et un écran HDMI. Cette option est incompatible avec le toucher mais fonctionne avec tous les autres types d'entrée. Si vous avez l'intention d'utiliser une souris, téléchargez l'image de Pi Scan compatible avec la souris ci-dessous.

## Écran tactile

Pi Scan fonctionne avec l'écran tactile officiel de la framboise Pi. Cela permet d'obtenir un appareil de balayage plus compact et plus autonome. L'option tactile est incompatible avec la saisie à la souris. Si vous souhaitez utiliser un écran tactile, téléchargez l'image de Pi Scan compatible avec l'écran tactile.

## Clavier

Pi Scan peut désormais être entièrement contrôlé par un clavier. Chaque bouton est accompagné d'un raccourci clavier, généralement un chiffre. Le clavier fonctionne à la fois avec la version écran tactile et la version souris de Pi Scan. Pour naviguer dans les aperçus avec un clavier, utilisez les touches "+", "-" et "0" pour régler le niveau de zoom et déplacez la fenêtre de visualisation avec le WASD ou les touches fléchées. Lors de la numérisation, utilisez la barre d'espace, "b" ou "c" pour la capture.

## Pédale de commande USB

La plupart des pédales USB bon marché émulent un clavier et envoient la touche "b" par défaut. Comme la touche "b" est une touche de raccourci pour la capture, les pédales USB peuvent être utilisées pour déclencher la capture de page.

## Pédale de commande industrielle

Les pédales industrielles sont plus robustes que les pédales USB de prix équivalent. Mais elles n'ont pas l'électronique nécessaire pour gérer le protocole USB. Elles peuvent être câblées jusqu'à deux broches sur le Raspberry Pi et Pi Scan traitera toute connexion entre ces broches comme un déclencheur pour la capture lors du balayage. Notez que cela ne permet de capturer des images que sur l'écran de numérisation, et non lors du réglage de la mise au point, du niveau de zoom ou de la vitesse d'obturation. Pour plus de détails, consultez le manuel d'assemblage de l'Archivist Quill (http://tenrec.builders/quill/guide/electronics/pedal/).

## Boutons et microcommutateurs

Toute connexion électrique entre les broches GPIO21 et GND sur le Raspberry Pi provoquera une capture lors du balayage. Ainsi, tout bouton ou microcommutateur peut fonctionner comme un déclencheur de balayage s'il est correctement câblé.

# Utilisation d'appareils photo Nikon 1 J5 ou d'autres appareils sans miroir/DSLR

La dernière version de Pi Scan inclut gphoto2 et l'utilise pour prendre en charge une multitude d'appareils photo DSLR et sans miroir (voir [liste des appareils photo pris en charge](http://www.gphoto.org/proj/libgphoto2/support.php)). La numérisation à l'aide d'un DSLR fonctionne un peu différemment de l'utilisation d'un appareil photo Canon de type "pointer et tirer" supporté par CHDK.

Avec un DSLR, toute la configuration des appareils photo, y compris la mise au point et le zoom, doit être effectuée manuellement par l'utilisateur via l'interface standard de l'appareil photo. Pi Scan lui-même ne fait que déclencher la capture des images et les stocke ensemble sur le stockage externe. La plupart des réglages d'un appareil photo persistent même lorsqu'il est éteint. Mais si certains paramètres reviennent, vous devez être prêt à les réinitialiser au début de chaque session.

Un autre avantage de l'utilisation d'appareils photo compatibles avec les photos est que si vous spécifiez une sortie d'image brute, Pi Scan ira automatiquement chercher et assembler les images brutes avec les fichiers JPEG.

L'appareil photo de haute qualité que nous recommandons actuellement est l'appareil Nikon 1 J5. Si vous n'êtes pas sûr de l'appareil à prendre, c'est celui-là qu'il faut choisir. Il est plus probable qu'il fonctionne (c'est le modèle d'appareil utilisé pour tester le Pi Scan), et nous serons plus à même de vous fournir une assistance efficace s'il ne fonctionne pas. En outre, il a une durée de vie exceptionnellement longue. De nombreux DSLR sont conçus pour seulement 100 000 déclenchements. Les appareils Nikon 1 J5 ont une durée de vie beaucoup plus longue, dépassant le million de déclenchements.

Paramètres recommandés pour la numérisation avec une Plume d'Archiviste ou Archiviste utilisant un appareil photo Nikon 1 J5 :

- Mode manuel (M sur le sélecteur de mode)
- Vitesse d'obturation : 1/15 seconde
- F-Stop : 5,6
- ISO : 100
- Balance des blancs : Incandescent ou nous une carte grise pour un ensemble personnalisé
- Qualité de l'image : JPEG fine ou NEF (RAW) + JPEGfine
- Taille de l'image : L (5568x3712)
- Contrôle de la distorsion automatique : sur
- Mode de mise au point : AF-A -- L'appareil photo Nikon 1 J5 utilise un autofocus par zone, ce qui signifie qu'il devrait bien fonctionner même sur des pages qui sont pour la plupart vierges. Si nécessaire, l'appareil Nikon 1 J5 dispose également d'un mode de mise au point manuelle. Mais la mise au point manuelle doit être refaite à chaque fois que l'appareil est éteint.
- Mode zone AF : Zone automatique
- Zoom : Zoomez jusqu'à ce que les quatre bords du plateau soient juste visibles. Notez que le Nikon 1 J5 perd le réglage du zoom à la mise hors tension, il doit donc être réglé à chaque session et vous pouvez vous retrouver avec une valeur de zoom légèrement différente d'une session à l'autre. C'est pourquoi il est préférable de scanner un livre entier en une seule session plutôt que de le diviser entre plusieurs sessions.

# Télécharger

Les variétés de framboises Pi 2 et Pi 3 sont toutes deux soutenues. Il existe deux variantes. L'une d'entre elles prend en charge la saisie à la souris et tout écran HDMI. L'autre version prend en charge l'écran tactile officiel de Raspberry Pi :

* [Image de la framboise Pi (pour la souris)](http://tenrec.builders/pi-scan/latest/pi-scan-latest-mouse.zip)
* [Image Pi de la framboise (pour l'écran tactile)](http://tenrec.builders/pi-scan/latest/pi-scan-latest-touch.zip)

Deux modèles de caméras sont pris en charge. Téléchargez l'image appropriée pour votre appareil photo :

* [Image Canon PowerShot A2500](http://tenrec.builders/pi-scan/latest/pi-scan-camera-a2500-latest.zip)
* [image Canon PowerShot ELPH/IXUS 160](http://tenrec.builders/pi-scan/latest/pi-scan-camera-elph160-latest.zip)

Utilisez ces images à vos propres risques. Ces images peuvent endommager votre appareil photo. Lors des premiers tests de l'image ELPH 160, une caméra a été endommagée et la cause de ce problème n'a jamais été trouvée de façon définitive. Voir [ce lien] (http://chdk.setepontos.com/index.php?topic=12321.140).

D'autres caméras compatibles CHDK peuvent ou non fonctionner. Si vous souhaitez l'essayer, il vous suffit d'installer le paquet CHDK complet pour la caméra appropriée et le micrologiciel que vous utilisez. Si cela fonctionne, c'est parfait. Sinon, vous devrez peut-être consulter le journal de débogage, le code et les forums CHDK pour savoir pourquoi. Bien que je ne supporte pas moi-même d'autres modèles d'appareils photo, je suis prêt à accepter des demandes de patchs pour rendre Pi Scan compatible avec d'autres appareils photo.

# Installation

Le logiciel est présenté sous la forme d'images de disques entiers qui doivent être flashées sur des cartes SD d'au moins 4 Go. Comme rien n'est stocké sur ces images, la vitesse de la carte n'a pas d'importance.

Extrayez les images des archives et utilisez un outil approprié pour les écrire sur les cartes. Ne vous contentez pas de copier le fichier sur la carte. Cela ne fonctionnera pas et vous serez triste. Si vous mettez à jour les cartes de caméra, il se peut qu'elles soient verrouillées. Avant de les numériser, vous devez les déverrouiller. Le petit interrupteur à gauche doit être en position *top*.

Tutoriels d'écriture d'images :

* [Windows](https://www.raspberrypi.org/documentation/installation/installing-images/windows.md)
* [Mac](https://www.raspberrypi.org/documentation/installation/installing-images/mac.md)
* [Linux](https://www.raspberrypi.org/documentation/installation/installing-images/linux.md)

## Ecrire une carte SD sur Windows

Vous en aurez besoin :

* Imageur de disque Win32 ([lien](http://sourceforge.net/projects/win32diskimager/))
* Un lecteur de carte SD
* Une carte SD (assurez-vous que la carte SD est déverrouillée. Le petit interrupteur à gauche doit être en position *top*)
* Une image de disque téléchargée à partir d'un emplacement situé au-dessus
* Au moins 4 Go d'espace disque disponible

L'image que vous avez téléchargée se présente sous la forme d'un fichier ZIP compressé. Faites un clic droit dessus et sélectionnez "Extraire tout..." dans le menu.

Choisissez un dossier de destination pour le fichier extrait.

Insérez la carte SD dans le lecteur de carte SD.

Lancez l'imageur de disque Win32. Il vous sera demandé si vous souhaitez l'autoriser à effectuer des modifications, cliquez sur oui.

A l'intérieur de Win32 Disk Imager, cliquez sur le petit dossier et trouvez le fichier image que vous avez extrait auparavant. Sélectionnez-le et cliquez sur OK.

Sélectionnez le lecteur sur lequel la carte SD est montée dans le menu déroulant "périphérique". Ouvrez "Poste de travail" ou "Explorateur de fichiers" et vérifiez que c'est le bon lecteur.

Cliquez sur le bouton "Ecrire". Ceci effacera tout ce qui se trouve sur la carte et écrira le contenu de l'image sur le lecteur. Soyez donc absolument sûr que vous écrivez à l'endroit où vous pensez être.

## Utilisation des cartes SD

Une fois les images installées, vous disposerez de trois cartes SD. L'une d'entre elles doit être insérée dans votre Pi 2 Framboise. Les autres cartes sont destinées à vos appareils photo. Les cartes pour appareils photo doivent maintenant être verrouillées. Le petit interrupteur à gauche doit être en position *bas*.

Lorsque vous allumez les caméras, un écran d'accueil CHDK apparaîtra brièvement. C'est ainsi que vous savez que tout s'est bien passé. Si vous ne voyez pas l'écran de démarrage, c'est que les cartes ne sont pas verrouillées ou qu'il y a eu un autre problème d'imagerie des cartes.

Parfois, lorsque vous allumez les caméras, un écran apparaît pour vous demander de régler l'heure et le fuseau horaire. Cela se produit la première fois que vous allumez les caméras, ou si elles ont été débranchées pendant longtemps. Si cela se produit, débranchez le câble USB de l'appareil, utilisez le clavier pour régler la date et l'heure et supprimez ces écrans, puis rebranchez le câble USB.

Branchez les caméras sur le Pi. Branchez le lecteur de carte SD sur le Pi. Branchez un moniteur, une souris et un clavier (facultatif) sur le Pi. Allumez le Pi. Notez qu'il n'y a pas de mode réseau pour ce logiciel. Il fonctionne en connectant directement les périphériques d'entrée/sortie sur le Pi.

# Utilisation

Pour un aperçu de l'utilisation de Pi Scan, voir le [tutoriel vidéo] (https://vimeo.com/150385938).

Le système d'exploitation Pi Scan est entièrement en lecture seule. Tout est enregistré sur une carte SD externe que vous pouvez insérer dans le lecteur de carte SD. Les journaux de débogage, la configuration et les images scannées y sont tous enregistrés. Chaque fois que vous revenez à l'écran de démarrage, Pi Scan démonte le disque dans le lecteur de carte afin que vous puissiez le retirer en toute sécurité ou éteindre le Pi.

Il existe de nombreux paramètres de l'appareil qui ne sont pas encore configurables par l'utilisateur. Ces paramètres sont réglés sur des valeurs qui supposent que vous utilisez un scanner de livres Archivist.

## Étapes de numérisation

1. Bootez le Pi à la framboise. Une fois que le Pi lui-même a démarré, vous verrez l'écran de démarrage du Pi Scan. Sur cet écran, le Pi Scan éjectera votre disque externe pour que vous puissiez le supprimer. Si nécessaire, vous pouvez également quitter la console et vous connecter en utilisant le nom d'utilisateur "pi" et le mot de passe "framboise", mais pour la plupart des utilisateurs, cela ne sera pas nécessaire.
1. Sur la page de configuration du disque, Pi Scan recherche et monte votre stockage externe. Le stockage externe est utilisé pour la configuration, le débogage des journaux, et c'est là que les images scannées sont sauvegardées. Branchez votre lecteur USB ou votre lecteur de carte SD et votre carte SD. Après quelques secondes, votre lecteur sera détecté et vous pourrez appuyer sur la touche suivante. Si votre lecteur n'est pas détecté, essayez de débrancher et de rebrancher l'appareil.
1. Sur la page de configuration de l'appareil photo Pi Scan recherche deux appareils photo connectés par USB au Pi. Une fois qu'il les a trouvées, vous pourrez passer à l'étape suivante ou, en option, définir un niveau de zoom pour chaque caméra.
1. (Facultatif) Les paramètres de zoom peuvent être définis pour chaque caméra individuellement. Appuyez sur "test shot" pour prendre une photo de chaque appareil photo, puis réglez les paramètres de zoom dans les coins supérieur gauche et supérieur droit. Ne vous inquiétez pas si les pages sont du mauvais côté pour l'instant. Une fois que vous avez réglé le niveau de zoom souhaité, appuyez sur "Terminé". Le réglage du zoom est enregistré sur la mémoire externe, donc tant que vous utilisez la même carte, vous n'aurez pas besoin de réajuster ces réglages.
1. (Facultatif) La vitesse d'obturation peut être réglée pour chaque appareil photo. Si vos photos sont systématiquement trop sous-exposées ou trop surexposées, réglez la vitesse d'obturation.
1. Pour que la mise au point de l'appareil reste constante, Pi Scan effectue une mise au point automatique une fois par session, puis verrouille cette mise au point pour le reste des photos. Pour obtenir la meilleure mise au point possible, vous devez appuyer deux pages sur la platine de votre scanner comme si vous les scanniez, puis appuyer sur "Refocus". Assurez-vous que ces pages contiennent beaucoup de texte, car les caméras ont du mal à faire la mise au point sur les espaces blancs uniquement. Vérifiez sur l'aperçu que la mise au point est bonne. Vous devez également vérifier que la page "impaire" pointe vers une page impaire de votre livre et que la page "paire" pointe vers une page paire. Si ce n'est pas le cas, vous pouvez appuyer sur "swap" pour échanger les deux pages. Cela permettra de s'assurer que les pages sont correctement imbriquées lors de la numérisation.
1. Pendant la numérisation, appuyez sur les pages contre la platine et appuyez sur le bouton "Capture". Après avoir entendu les obturateurs de l'appareil photo, vous pouvez passer à la page suivante pendant que Pi Scan traite les photos. Lors de votre premier balayage, vous devrez vérifier que tout semble correct. Vous devez également vérifier périodiquement au fur et à mesure que vous scannez, en particulier pour vos premiers livres utilisant Pi Scan. Si vous remarquez un problème pendant la numérisation, vous pouvez recréer les deux dernières pages avec le bouton "Rescan".
1. Une fois la numérisation terminée, appuyez sur "Terminé" pour revenir à l'écran de démarrage. Ici, vous pouvez supprimer votre stockage externe et déplacer les fichiers de celui-ci vers votre ordinateur. Si vous numérisez le même livre en plusieurs sessions, Pi Scan continuera à numéroter les images là où vous vous êtes arrêté. Si vous déplacez toutes les images du stockage externe, l'enregistrement reprendra à "0000.jpg".

### Échec de la capture

Il arrive qu'un appareil photo renvoie une photographie vide ou ne réussisse pas à la capturer. Lorsque cela se produit, Pi Scan vous en informe et aucune image de l'appareil photo n'est enregistrée sur le disque. Appuyez sur "Ok" pour la notification, puis sur "Capture" pour réessayer. Si vous constatez que cela se produit plus fréquemment, notez l'erreur que vous voyez et informez l'aide des constructeurs de tenrec dot du problème. Il arrive parfois qu'un appareil photo se mette dans un mauvais état et que toutes les tentatives de capture échouent. Si quelques captures d'affilée échouent, essayez d'éteindre et de rallumer la caméra à la main.

### Crash de l'appareil photo

Il arrive parfois qu'une caméra s'écrase ou se déconnecte. Pi Scan ne peut pas faire la différence entre ces deux événements, il suppose donc toujours que la déconnexion est un accident. Lorsque Pi Scan pense qu'il y a eu un plantage, il affiche un écran de débogage de l'appareil photo. Il vous indiquera quelle caméra est déconnectée et la dernière chose qu'il a essayé de faire quand cela s'est produit. Reconnectez ou mettez la caméra sous tension et elle devrait détecter que la caméra est de nouveau en ligne. Lorsque la caméra est de retour, vous pouvez appuyer sur "Get Debug Log" et le journal de débogage sera enregistré dans le répertoire de débogage pour le dernier plantage sur votre stockage externe. Vous pouvez envoyer ce journal de débogage et le message d'erreur que vous avez vu sur l'écran de débogage pour aider les constructeurs de tenrec dot.

Une fois que toutes les caméras sont à nouveau connectées, vous pouvez appuyer sur "Ok" pour revenir à l'analyse. Vous devrez d'abord repasser par l'écran de "mise au point" pour vous assurer que la mise au point est correctement réglée.

### Crash du balayage Pi

Avec un peu de chance, vous ne verrez jamais Pi Scan se planter, mais si vous le faites, il y a une page spéciale de débogage qui montre ce qui s'est passé. Envoyez une photo de cette page pour aider les constructeurs de tenrec dot afin qu'elle puisse être corrigée.

### Journal d'erreurs

Un journal d'erreurs de chaque panne et crash de caméra est enregistré sur votre stockage amovible. Cela signifie que même si vous appuyez rapidement sur Ok et que vous manquez le message, vous pouvez toujours revenir en arrière et voir les détails plus tard. Si vous rencontrez des pannes ou des problèmes persistants, il est utile d'envoyer ce journal d'erreurs pour aider les constructeurs de tenrec dot.

### Redémarrage

Rappelez-vous toujours que vous ne pouvez pas corrompre Pi Scan en le redémarrant. Ainsi, si jamais vous ne parvenez pas à résoudre un problème ou si le système ne répond plus complètement, vous pouvez toujours débrancher et rebrancher Pi Framboise pour reprendre le scan. Le seul danger est que votre stockage externe n'ait pas été démonté proprement, donc si vous devez couper l'alimentation et redémarrer, assurez-vous de vérifier les scans que vous avez déjà effectués pour vous assurer qu'ils sont tous là et que vous pouvez les ouvrir normalement. 

# Notes de version

- 1.5 -- Ajout de la prise en charge de gphoto2 ([liste des appareils photo pris en charge](http://www.gphoto.org/proj/libgphoto2/support.php)), des cartes SD de plus de 32 Go.
- 1.0 -- Ajout du réglage de la vitesse d'obturation, support du déclenchement via les broches GPIO, support du clavier complet, support de l'écran tactile, mécanisme de mise à jour, bip sur erreur, mise au point lors du zoom, nombreux crashs, et plus encore.
- 0.7 -- Ajout de numéros de page lors de la capture. Correction des paramètres ISO et de la vitesse d'obturation. Tentative de correction des plantages de l'appareil photo lors de l'entrée en mode alt. Ajout de la détection de crash Pi Scan pour la prévisualisation et les fils de l'appareil photo.
- 0.6 -- Correction de la rotation de la prévisualisation. Les images étaient affichées à l'envers.
- 0.5 -- Correction des problèmes de numérotation des pages. Ajout d'une interface utilisateur pour le réglage du zoom.
- 0.4 -- Détection lorsque les répertoires /debug et /images ne sont pas créés et note le problème dans l'écran de stockage.
- 0.3 -- Ajout de la détection de crash et d'un écran qui affiche l'erreur en cas d'exceptions inattendues
- 0.2 -- Correction des problèmes d'espaces dans les noms de chemin et lors de l'écriture des journaux d'erreurs.
- 0.1 -- Version initiale
