# Note de version — 0.19.2

Texte à coller dans la description de la version GitHub.

---

Le journal des analyses ne vit plus sur un téléphone. Il vit dans un **dossier
Google Drive**, que plusieurs appareils tiennent ensemble.

> **La 0.19.0 et la 0.19.1 ne doivent pas servir.** Deux défauts les rendaient
> inaptes au cahier commun, et ils sont décrits plus bas. Installer celle-ci.

## Un cahier commun

Chaque mesure figée puis relâchée entre au journal, avec tout ce que porte
l'étiquette du registre de gonflage : la bouteille, la date, l'analyste, la
lecture des capteurs **au centième**, la valeur retenue, le CO, la ppO₂, la MOD,
les drapeaux de l'appareil, la dérive du dernier contrôle à l'air — et,
désormais, **quel appareil a mesuré**.

Chaque appareil tient **son propre fichier** dans le dossier,
`journal-Pixel-10-Pro-XL.csv`, `journal-SM-X920.csv`. Un seul fichier commun
aurait l'air plus simple et ne l'est pas : deux appareils qui écrivent le même
fichier dans un dossier synchronisé produisent tôt ou tard deux versions
concurrentes, et c'est le service de synchronisation — pas l'application — qui
décide laquelle survit. Un fichier par appareil rend la collision impossible.
L'écran, lui, relit tout le dossier et recompose le cahier entier, rangé par
instant, appareils mêlés.

## Ce qui ne peut pas arriver

Trois garanties, et chacune répond à une façon réelle de perdre des lignes.

**Rien ne s'écrase.** Ce qui part vers le dossier est toujours la réunion de ce
qu'on y lit et de ce qu'on a localement, jamais le seul contenu local. Une
application réinstallée, ou un « Effacer » local, ne peut donc pas vider le
cahier de tout le monde — c'est aussi pourquoi « Effacer » ne touche que la
copie de l'appareil, et le dit.

**Rien ne se perd, pas même l'incompris.** Une ligne que cette version ne sait
pas relire — écrite par une version postérieure, ou éditée à la main — est
conservée telle quelle plutôt que jetée. Un format qui jette ce qu'il ne
comprend pas détruit en silence.

**Rejouer un envoi ne coûte rien.** Deux lignes identiques sont la même mesure,
et une seule est retenue. C'est toute la gestion du hors connexion : une mesure
prise au bord d'un bassin sans réseau entre dans le fichier local, qui ne fait
que croître et qui fait foi, puis part au prochain envoi réussi — dans dix
secondes ou dans trois jours. L'écran dit combien de mesures attendent encore.

## Aucune permission de plus

Le dossier se désigne dans le **sélecteur de fichiers d'Android**, et c'est
l'application Drive qui le synchronise. Pas d'API Google, pas de compte à
connecter dans l'application, pas de permission `INTERNET` : le relevé
`aapt2 dump permissions` de cette version est identique à celui des
précédentes — deux permissions Bluetooth, et rien d'autre.

Ce sont donc vos mesures, dans votre Drive, sur un dossier que vous avez choisi.
Mais elles ne restent plus sur l'appareil : lisez l'avertissement du README, il
a été mis à jour pour le dire.

## Un barrage au lancement

L'application ne s'ouvre plus tant que le Bluetooth et le dossier ne sont pas
accordés, et elle redemande tant qu'ils manquent.

Ce n'est pas de la rigueur pour elle-même. Sans Bluetooth, l'écran d'analyse
attend une trame qui n'arrivera jamais ; sans dossier, les mesures se consignent
là où personne n'ira les chercher. Dans les deux cas l'application *paraît*
fonctionner, et c'est cela qu'il fallait empêcher.

Le barrage porte sur l'**autorisation**, jamais sur la joignabilité : un Drive
hors ligne n'interdit pas de mesurer.

## Corrigé depuis la 0.19.0

Deux défauts, trouvés en éprouvant le dispositif entre un téléphone et une
tablette. Le second est le plus grave.

**Un dossier local passait pour un dossier partagé.** Le sélecteur système mêle
Drive, le stockage de l'appareil et le reste, et il s'ouvre sur le stockage
local : un dossier interne se choisissait en deux gestes, l'application y
écrivait sans broncher, et l'écran continuait d'annoncer « dossier partagé »
devant un dossier que personne d'autre ne verrait jamais. L'application lit
désormais la provenance du dossier, **refuse** le stockage de l'appareil au
moment du choix, et nomme la source à l'écran — « Google Drive · mon_dossier ».
Une source qu'elle ne sait pas nommer passe, avec un avertissement : refuser sur
une ignorance fermerait la porte à tout service qui n'est pas Drive.

**Les fichiers des autres appareils n'étaient pas lus.** Le contenu du dossier
était parcouru en lisant les colonnes par leur rang. Un fournisseur de documents
n'est pas tenu de les rendre dans l'ordre demandé, et Drive ne le fait pas : le
dossier paraissait vide alors que le sélecteur système y montrait les fichiers.
Les colonnes se lisent maintenant par leur nom.

Ce second défaut en cachait un troisième, et c'est celui qui aurait pu coûter :
un échec de lecture était avalé et rendait une liste vide, si bien que la
réunion prenait un fichier illisible pour un fichier vide — et la réécriture qui
suit l'aurait **effacé**. La garantie « rien ne s'écrase » tombait en silence.
Une lecture qui échoue interrompt désormais l'envoi, et l'écran le dit.

## Depuis la 0.15.0

Les versions 0.16 à 0.18 n'ont pas été publiées ; ce qu'elles contenaient arrive
ici.

- **Ce que l'appareil dit de lui-même est enfin écouté** : dépassement de plage,
  température, hélium imprécis. Ces drapeaux remontent jusqu'à l'analyse et
  suivent la mesure figée. Comme le CO, ils avertissent sans rien interdire.
- **Le contrôle de cellule à l'air**, retenu d'une session à l'autre, affiché à
  côté des propositions de rattrapage d'oxygène. Rien n'est appliqué en silence.
- **La bouteille figure sur l'étiquette du registre**, en tête : elle manquait,
  et l'on relisait une MOD, une date et un prénom sans savoir à quoi les
  rapporter.
- **Le passage au vert s'entend.** Pendant les cinq secondes de calme, les deux
  mains sont sur le robinet.
- **Le journal des analyses et la réimpression** : relire une analyse et
  refaire ses étiquettes sans rebrancher la bouteille. Une étiquette réimprimée
  le dit, par un bandeau — sans lui, rien ne la distinguerait d'une mesure
  fraîche.
- **Trois chemins vers l'imprimante** : les appareils appairés, une recherche
  menée par l'application, une adresse saisie à la main. Une ZD421t sortie
  d'usine s'appaire sous son numéro de série, où rien ne rappelle la marque ;
  et depuis One UI 7, les réglages Bluetooth de Samsung ne listent pas toujours
  une imprimante que l'application, elle, trouve. L'envoi tente les deux
  liaisons et **dit par laquelle** l'étiquette est sortie.
- **La version se lit vraiment sur l'écran de lancement.**
- **Le plancher passe à Android 13.** La recherche d'imprimante lit les données
  de l'appareil trouvé par des méthodes typées apparues à cette version ; en
  deçà, la première imprimante trouvée faisait tomber l'application.

---

## Ce qui n'a pas été éprouvé

Le dossier partagé a été vérifié de bout en bout entre un Pixel 10 Pro XL et une
Galaxy Tab S10 Ultra, sur Google Drive : dossier créé depuis le sélecteur,
mesure figée sur le téléphone puis relâchée, et **relue sur la tablette** avec
sa colonne appareil. Il n'a **pas** été éprouvé sur un autre fournisseur de stockage, ni
sur un dossier partagé à plusieurs comptes, ni sur deux appareils du **même
modèle** — ceux-là partageraient un fichier, ce qui se répare de soi-même mais
n'a pas été observé en conditions réelles.

L'alarme de CO n'a toujours jamais été vue se déclencher sur du vrai gaz : le
capteur de l'appareil de test est en défaut. Elle a été éprouvée en simulation,
pas au bord du bassin.

**Application non officielle, sans lien avec Divesoft s.r.o.**

| | |
|---|---|
| Version | 0.19.2 |
| Android minimum | 13 (API 33) |
| Taille | 8,3 Mo |
| SHA-256 | `83e64d418aeae9537e54710ee1c0af566dc5d321dad3e7eca8b66ec0627a6273` |
