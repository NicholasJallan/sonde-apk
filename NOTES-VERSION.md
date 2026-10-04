# Note de version — 0.21.0

Texte à coller dans la description de la version GitHub.

---

L'impression passe désormais par le **Bluetooth basse consommation**. Une
**ZD421c** — la ZD421 à cartouche de ruban — imprime donc comme une ZD421t,
sans appairage et sans module à ajouter. Et cette version porte aussi la
refonte des écrans préparée pour la 0.20.0, qui n'avait pas été publiée.

## Deux imprimantes, deux radios

Une ZD421 n'a pas toujours de Bluetooth classique. La seconde imprimante de
l'atelier, une ZD421c en référence `ZD4A042-C0EE00EZ`, n'a qu'un port Ethernet
et la radio basse consommation montée d'usine sur toutes les ZD421. Le profil
série par lequel l'application imprimait jusqu'ici n'y existe pas : Android la
classe en basse consommation seule, l'appel en Bluetooth classique reste sans
réponse, et son réglage n'offre pas d'autre mode.

Zebra présente cette radio comme réservée à son application de configuration.
Elle porte pourtant un **service d'impression**, décrit dans une note
technique de Zebra et repris par son kit de développement Android. C'est par
lui que l'application imprime maintenant, d'abord, sur toute imprimante qui
l'a :

- **la radio d'Android décide de l'ordre** : basse consommation seule pour une
  machine qui n'a qu'elle, basse consommation puis liaison série pour une
  machine qui a les deux, liaison série seule pour une Zebra plus ancienne ;
- **aucun appairage** sur la nouvelle voie ;
- **chaque morceau est acquitté** par l'imprimante : la fin de l'envoi se sait,
  au lieu de s'attendre ;
- **l'écran dit toujours par où l'étiquette est sortie** — « Bluetooth basse
  consommation », « liaison série », « liaison série sans appairage ».

Le débit est modeste, et c'est sans importance : une étiquette de col ou de
diluent part en une seconde, l'étiquette du bailout qui porte le logo en une
dizaine.

## Une imprimante pas prête refuse l'étiquette

Avant chaque envoi, l'application demande son état à l'imprimante. Tête
ouverte, plus de papier, plus de ruban, imprimante en pause : **rien ne part**,
et l'écran dit pourquoi.

Ce n'est pas un confort. Une Zebra dont la tête est ouverte accepte
l'étiquette, la garde en mémoire et l'imprime à la fermeture — plus tard,
devant une autre bouteille peut-être, sans que l'écran ait jamais dit qu'elle
attendait.

Un état qui ne se lit pas n'empêche rien : on ne refuse pas d'imprimer sur une
ignorance.

## Trouver une Zebra, même cachée

Les Zebra publient en basse consommation un identifiant que le Bluetooth SIG
attribue à Zebra. La recherche de l'écran **Imprimantes** l'écoute désormais
en plus de la recherche classique, et marque « Zebra (BLE) » ce qui s'y
annonce. Une machine dont la découverte classique est coupée — ce que Zebra
recommande hors usage — y apparaît quand même.

## Des écrans repensés

- **Une barre en bas du téléphone** : Analyse, Étiquettes, Journal, et « Plus »
  pour les imprimantes, le diagnostic et la simulation. Sur tablette, le menu
  reste permanent.
- **Une pastille d'état** dans la barre du haut, sur tous les écrans :
  l'analyseur, ou `SIMULÉ` ; les mesures en attente d'envoi au journal.
- **Analyse** : la cible se centre tant que le gaz bouge, et le nom de qui
  analyse tient sur la ligne de la liaison.
- **Étiquettes** : une barre d'action fixe — « Imprimer les 2 étiquettes »
  (celles qui ne sont pas encore sorties), « Choisir une imprimante »,
  « Bouteille suivante » une fois tout sorti.
- **Imprimantes** : une carte par support, une seule liste d'appareils qui dit
  ce que chacun imprime.
- **Journal** : rangé par jour, avec une recherche par bouteille ou mélange ;
  sur tablette, la liste à gauche et le détail à droite.
- Un thème tiré de la palette de l'application, une échelle de textes, des
  chiffres qui ne dansent plus.

## Ce qui a été corrigé

- Un envoi en cours écrivait « envoyé » à côté d'une étiquette qui avait changé
  pendant l'envoi, et une série continuait d'imprimer l'ancienne. Ce n'est plus
  possible : seule l'étiquette affichée au départ peut être déclarée sortie.
- Une analyse simulée relue du journal se réimprimait sans le dire. Elle est
  désormais **refusée** dans cette version.
- « Effacer l'appareil » pouvait perdre sans confirmation des mesures pas
  encore versées au dossier, et s'offrir devant un dossier qui venait de
  changer.
- Une écriture du journal qui échouait passait en silence.
- Les notations de mélange ne dépendent plus de la langue de l'appareil.

---

## Ce qui n'a pas été éprouvé

L'impression par la basse consommation a été vérifiée **sur deux machines** :
une ZD421t (Link-OS 6.6) et une ZD421c (Link-OS 7.1), depuis un Pixel 10 Pro XL
— grand format, bailout avec logo, col, et refus capot ouvert. Elle ne l'a été
ni sur une autre Zebra, ni depuis une tablette, ni après une mise à jour du
micrologiciel de l'imprimante. Zebra ne présente pas cette voie comme une voie
d'impression : une mise à jour pourrait la fermer. La liaison série reste alors
en secours — sur les machines qui l'ont.

L'alarme de CO n'a toujours jamais été vue se déclencher sur du vrai gaz : le
capteur de l'appareil de test est en défaut.

**Application non officielle, sans lien avec Divesoft s.r.o.**

| | |
|---|---|
| Version | 0.21.0 |
| Android minimum | 13 (API 33) |
| Taille | 8,3 Mo |
| SHA-256 | `46d1bcc3ac54129374f1bf488369f711dcd45dd1f1609e7395e59a954e7be7c3` |
