# Note de version — 0.24.0

Texte à coller dans la description de la version GitHub.

---

Une version d'ajout : **une seule imprimante suffit désormais**, et
l'application apprend à servir les Zebra ZD421 à **300 dpi**. Un écran de
réglages fait son apparition — deux réglages, et aucun qui touche à la
sécurité.

## Un écran « Réglages »

- **Le nom imprimé par défaut** sur les étiquettes. Le champ de l'écran
  d'analyse sert toujours, pour un analyste de passage, mais il ne vaut plus
  que pour la session : au lancement suivant, on retrouve le nom par défaut.
  Une installation neuve n'en a aucun ; une installation existante garde le
  sien.
- **Une imprimante ou deux.** À deux, rien ne change : le corps sur une
  100 × 150, le col et le registre sur une 76 × 51.
- La **résolution** de chaque imprimante retenue s'y lit — elle ne s'y règle
  pas, voir plus bas.

Ni ppO₂, ni seuil, ni arrondi n'y figurent : ce sont des décisions prises
bouteille par bouteille, ou celles de l'analyseur.

## Une seule imprimante

- Tout sort du rouleau **100 × 150**. Le col et le registre partagent une même
  étiquette, l'un au-dessus de l'autre, séparés par un **trait de coupe**
  pointillé : on coupe, et chaque moitié porte son étiquette entière.
- Les deux étiquettes sont **exactement** celles du 76 × 51, au point près,
  centrées dans 12 mm de blanc — rien n'a été recomposé.
- Le travail d'une bouteille sort **d'un seul geste** : le corps, puis le col
  et le registre. « Bouteille suivante » n'apparaît qu'une fois le col sorti ;
  on ne peut plus passer à la suite en l'oubliant.
- On bascule d'un mode à l'autre quand on veut — sauf au milieu d'une
  bouteille dont des étiquettes sont déjà sorties. Les imprimantes de l'autre
  mode restent retenues.

## 300 dpi

- Avant chaque envoi, l'application **demande sa résolution à l'imprimante**,
  et l'étiquette part rendue pour elle : à 300 dpi, le même dessin agrandi
  d'une fois et demie, logos compris (tirés de leurs sources, pas agrandis).
  Le contrôle de rouleau se fait dans l'unité de la machine.
- Une imprimante qui ne dit pas sa résolution est servie à 203 dpi, et l'envoi
  le signale ; son refus de rouleau ne se lève alors plus sur confirmation.
- **Le rendu à 300 dpi n'a encore jamais été imprimé.** Il est vérifié par le
  calcul — tous les mélanges, sans débordement ni chevauchement —, pas sur
  papier. Voir l'avertissement.
- L'export d'un fichier ZPL prend la dernière résolution lue sur l'imprimante
  du support, et le dit.

## À savoir

- L'étiquette au logo pèse deux fois plus à 300 dpi : comptez une vingtaine de
  secondes d'envoi au lieu de dix.

Zebra présente le Bluetooth basse consommation de la ZD421 comme réservé à son
application de configuration : une mise à jour du micrologiciel pourrait
fermer cette voie, et il n'y en a plus d'autre. L'export d'un fichier ZPL
reste possible.

L'alarme de CO n'a toujours jamais été vue se déclencher sur du vrai gaz : le
capteur de l'appareil de test est en défaut.

**Application non officielle, sans lien avec Divesoft s.r.o.**

| | |
|---|---|
| Version | 0.24.0 |
| Android minimum | 13 (API 33) |
| Taille | 8,8 Mo |
| SHA-256 | `0107f21464a8f99ed0b9de6f1317e92a18caad49d944d0cfb87e42b3d2a0ee0a` |
