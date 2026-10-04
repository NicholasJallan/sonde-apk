# Note de version — 0.22.0

Texte à coller dans la description de la version GitHub.

---

L'impression ne passe plus que par le **Bluetooth basse consommation**, et
chaque échec dit maintenant ce qui s'est passé, si quelque chose est parti, et
quoi faire.

## Une seule voie, sans appairage

La liaison série Bluetooth des versions précédentes est retirée. Elle ne
servait qu'à la ZD421t — la ZD421c n'en a pas —, ne pouvait pas lire l'état de
l'imprimante, ne savait pas quand l'envoi était fini, et poussait à
l'appairage.

Or une imprimante appairée est **tenue par Android** : le téléphone garde une
liaison ouverte avec elle, et elle cesse de répondre aux autres appareils. Une
tablette ne voyait plus la ZD421t appairée au téléphone.

**N'appairez pas votre imprimante.** Si elle l'est déjà, oubliez-la dans les
réglages Bluetooth du téléphone : Sonde n'en a pas besoin, et chaque envoi
ouvre sa liaison puis la referme en quelques secondes.

## Trouver une Zebra

L'écran **Imprimantes** lance une recherche dès qu'on l'ouvre. Une Zebra s'y
reconnaît à deux choses :

- l'identifiant **0xFE79** qu'elle annonce, attribué à Zebra par le Bluetooth
  SIG — même quand sa découverte classique est coupée ;
- le **préfixe de son adresse**, attribué à Zebra Technologies par l'IEEE —
  c'est ce qui reconnaît une imprimante retenue ou saisie à la main avant
  qu'on l'ait entendue.

Tout le reste — montres, écouteurs, voitures — est écarté, et le nombre
d'appareils écartés est affiché. Le nom affiché est celui que l'imprimante
annonce aujourd'hui, et non celui que le téléphone avait noté autrefois.

Une imprimante que la recherche ne montre pas se retient encore par son
adresse, imprimée sur l'étiquette de configuration de la machine.

## Une imprimante pas prête refuse l'étiquette

Avant chaque envoi, l'application demande son état à l'imprimante. Rien ne
part si :

- le capot est ouvert, le papier ou le ruban épuisé, l'imprimante en pause ;
- la tête ou le moteur est trop chaud ;
- le **rouleau chargé n'est pas celui de l'étiquette** — un col envoyé à
  l'imprimante du grand format, par exemple.

Chaque refus dit le geste qui le lève : « capot ouvert — referme-le, puis
appuie sur Pause ». Une Zebra dont le capot est ouvert accepte l'étiquette, la
garde, et l'imprime à la fermeture — plus tard, devant une autre bouteille
peut-être. C'est ce que ce refus empêche.

Les avertissements qui n'empêchent pas d'imprimer — calibration à refaire,
tête à nettoyer, fin de rouleau proche — accompagnent le message d'envoi.

## Des échecs qui se lisent

- **Imprimante injoignable** : « ne répond pas. Rien n'a été envoyé », puis ce
  qu'il faut vérifier — allumée, à portée, pas connectée à un autre appareil.
- **Coupure en plein envoi** : l'écran prévient qu'une étiquette tronquée a pu
  sortir, et dit de la jeter et de redémarrer l'imprimante.
- **Le message ne se cache plus** sous la barre d'impression du téléphone :
  la barre le redit au-dessus de son bouton.

---

## Ce qui n'a pas été éprouvé

Toutes ces erreurs ont été provoquées sur **une ZD421t et une ZD421c**, depuis
un Pixel 10 Pro XL : capot ouvert, pause, cartouche retirée, mauvais rouleau,
imprimante éteinte, imprimante tenue par un autre appareil. La surchauffe, le
massicot et les avertissements d'entretien suivent le format documenté par
Zebra mais n'ont pas été vus sur une vraie machine. La coupure en plein envoi
n'a pas été provoquée.

Zebra présente ce Bluetooth comme réservé à son application de configuration :
une mise à jour du micrologiciel pourrait fermer cette voie, et il n'y en a
plus d'autre. L'export d'un fichier ZPL reste possible.

L'alarme de CO n'a toujours jamais été vue se déclencher sur du vrai gaz : le
capteur de l'appareil de test est en défaut.

**Application non officielle, sans lien avec Divesoft s.r.o.**

| | |
|---|---|
| Version | 0.22.0 |
| Android minimum | 13 (API 33) |
| Taille | 8,3 Mo |
| SHA-256 | `d911173c1c99aaf2069fd9c8eca4d93eb381e7625d6e92200b73c1e7f7d41108` |
