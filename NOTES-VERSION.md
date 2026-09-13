# Note de version — 0.13.0

Texte à coller dans la description de la version GitHub.

---

Sur l'étiquette de col, le mot **MOD** ne s'imprimait pas. L'imprimante le
repliait sur lui-même et sortait un « DIO » superposé — et il en allait de même,
plus discrètement, sur quinze autres champs. Cette version le corrige, et
l'application alarme désormais sur le monoxyde de carbone.

## Le CO alarme

Au-delà de **5 ppm** — le seuil de l'ECHO lui-même — un avertissement passe
devant tout le reste sur l'écran de mesure, et suit la mesure une fois figée.

Il **n'interdit rien** : ni de figer, ni d'imprimer. Décider qu'une bouteille
part à la purge n'appartient pas à un téléphone.

Un capteur de CO en défaut le dit maintenant, au lieu d'afficher le même tiret
que « pas de capteur ». Sur le seul contaminant qui tue sans odeur ni goût, un
silence se lirait « air propre ».

## La police de l'imprimante est mesurée

Le rendu estimait la largeur des textes avec un ratio moyen unique. Il se
trompait des deux côtés : trop large pour les chiffres, il rabotait la MOD ;
trop étroit pour les capitales, il réservait aux blocs de texte moins de place
que les lettres n'en prennent. L'imprimante repliait alors la ligne.

Une table **mesurée glyphe par glyphe** — 99 caractères, relevés au dot sur un
moteur qui applique les métriques réelles de la police Zebra — remplace ce
ratio. Vérifié étiquette par étiquette :

- **seize débordements de ligne avant, aucun après** ;
- la MOD gagne jusqu'à **26 % de hauteur**, quatre chiffres compris.

## Trois défauts silencieux

- Une mesure entre 0 et 0,5 % d'oxygène se figeait, puis **n'avait aucune
  étiquette** : l'écran annonçait « Mesure figée » pendant que celui des
  étiquettes répondait qu'aucune mesure ne l'était.
- Une **coupure de liaison propre** laissait l'application sur « En attente »
  devant un analyseur de nouveau disponible, sans jamais retenter.
- Un refus de mise en page **fermait l'application** au lieu d'afficher sa
  raison.

## Vos réglages ne quittent plus l'appareil

`allowBackup="false"` fermait la sauvegarde dans le nuage, et couvrait le
transfert d'appareil à appareil **jusqu'à Android 12**. Il ne le couvre plus :
l'imprimante retenue, la ppO₂ et le prénom de l'analyste pouvaient suivre vers
un téléphone neuf pendant sa configuration. Les deux chemins sont désormais
fermés explicitement.

---

**Lisez le [README](../../blob/main/README.md) avant d'installer.** Cette
application n'est pas un produit : elle a été écrite pour un seul plongeur, un
seul analyseur et une seule imprimante, et hors le prénom qui signe les
étiquettes, elle ne se règle pas. Vous en assumez tous les risques.

Elle produit des chiffres — profondeur maximale, équivalent narcotique, densité
— dont dépend votre sécurité. Recoupez-les toujours.

L'alarme de CO, en particulier, n'a jamais été vue se déclencher sur du vrai
gaz : le capteur de l'appareil de test est en défaut. Elle a été éprouvée en
simulation, pas au bord du bassin.

**Application non officielle, sans lien avec Divesoft s.r.o.**

| | |
|---|---|
| Version | 0.13.0 |
| Android minimum | 12 (API 31) |
| Taille | 6,4 Mo |
| SHA-256 | `9b8c362d3b0d4587ff5261f9662b5691be5d6bc031538e484756dcf12ad2765d` |
