# Sonde — APK

Application Android qui lit l'analyseur de gaz **Divesoft ECHO** en Bluetooth et
imprime les étiquettes de bouteilles correspondantes sur une **Zebra ZD421**, à
ruban (ZD421t) ou à cartouche (ZD421c) — ou sur deux.

Ce dépôt ne contient qu'un fichier installable. Le code source n'est pas publié.

**[→ Télécharger la dernière version](../../releases/latest)**

---

## Avertissement

**Cette application n'est pas un produit. Elle n'a jamais été conçue pour être
distribuée.**

Elle a été écrite pour un seul plongeur, un seul analyseur et une seule
imprimante. Elle est mise à disposition telle quelle, sans support, sans
garantie, sans engagement de correction et sans promesse de mise à jour.

**En l'installant, vous acceptez d'en assumer l'intégralité des risques.**

### Elle produit des chiffres dont dépend votre sécurité

Cette application affiche et imprime une **profondeur maximale d'utilisation**,
un **équivalent narcotique** et une **densité de gaz**. Un mélange mal analysé,
mal étiqueté ou mal interprété peut tuer.

- Elle ne remplace **aucune** vérification que vous feriez autrement.
- Elle ne remplace pas l'écran de votre analyseur : **recoupez toujours**.
- Elle ne vous dispense pas de votre propre calcul.
- Une étiquette qu'elle imprime n'engage qu'une chose : votre responsabilité.

L'auteur ne pourra être tenu responsable d'aucun dommage, incident, blessure ou
décès résultant directement ou indirectement de son usage.

### Ce qui n'a jamais été vérifié

Par honnêteté, plutôt qu'un avertissement général, voici précisément ce qui
n'est pas éprouvé :

| Point | État réel |
|---|---|
| **Largeur imprimable** | Le flux suppose une tête de 100 mm utile. À confirmer : la tête 4 pouces de la ZD421t en couvre un peu plus. |
| **Protocole de l'analyseur** | Reconstitué par rétro-ingénierie, sans documentation du fabricant. Validé sur **un seul appareil**, à travers **une** mise à jour de son micrologiciel, qui n'a rien cassé — rien ne garantit les suivantes. Sur un autre appareil, ou après une autre mise à jour, les valeurs affichées pourraient être fausses **sans que rien ne le signale**. |
| **Alarme de monoxyde de carbone** | Le seuil est celui de l'analyseur — 5 ppm —, et l'unité est confirmée par l'opérateur. Mais le capteur CO de l'appareil de test est **en défaut** : l'alarme n'a jamais été vue se déclencher sur du vrai gaz, seulement en simulation. Ne lui confiez pas votre seule décision. |
| **Réglages du support** | Transfert thermique et détection par l'espace inter-étiquette sont imposés en dur. |
| **Imprimantes à 300 dpi** | L'application demande sa résolution à l'imprimante et rend l'étiquette pour elle. Ce rendu n'a **jamais été imprimé** : il est vérifié par le calcul, pas sur papier. Une imprimante qui ne répond pas est servie à 203 dpi — sur une 300 dpi, l'étiquette sortirait alors aux deux tiers de sa taille, et l'envoi le signale. **Vérifiez votre première étiquette.** |
| **Impression en Bluetooth basse consommation** | C'est la **seule** voie d'impression. Zebra la présente pourtant comme réservée à son application de configuration. Éprouvée sur **une ZD421t et une ZD421c**, depuis un téléphone et une tablette ; une mise à jour du micrologiciel de l'imprimante pourrait la fermer, et il n'y aurait alors plus que l'export d'un fichier ZPL. |

### Ce qu'elle ne sait pas faire

L'application n'a que **deux réglages** : le nom imprimé par défaut sur les
étiquettes, et une imprimante ou deux. Rien d'autre ne se règle.

- **Une seule famille d'imprimantes** : Zebra ZD421, à ruban ou à cartouche, à
  203 dpi — éprouvée — ou à 300 dpi — prise en charge, jamais imprimée.
- **Deux formats d'étiquettes** seulement : 100 × 150 mm et 76 × 51 mm. Avec
  une seule imprimante, tout sort sur le 100 × 150, le col et le registre
  partageant une étiquette à couper au trait.
- **Les étiquettes portent la marque de l'auteur**, imprimée en dur. Vous ne
  pouvez pas la retirer ni la remplacer par la vôtre.
- **Français uniquement**, **mètres uniquement**.
- **N'appairez pas l'imprimante** dans les réglages Bluetooth du téléphone :
  l'application n'en a pas besoin, et une imprimante appairée devient
  injoignable depuis les autres appareils.
- Elle **préfère le dernier analyseur ECHO** avec lequel la mesure a tourné,
  retenu par son adresse — mais ne l'exige pas : s'il ne répond pas dans les
  cinq secondes, elle se lie au premier autre qu'elle trouve. La toute
  première fois, ou si le vôtre est éteint alors qu'un autre est allumé à
  portée, rien ne garantit que ce soit le vôtre : **lisez le nom de
  l'appareil** affiché en tête de l'écran.
- Elle **exige un dossier Google Drive** au lancement, et ne s'ouvre pas sans.
  Le journal des analyses y est consigné, un fichier par appareil, pour que
  plusieurs téléphones tiennent le même cahier. C'est vous qui désignez le
  dossier, dans le sélecteur système ; l'application n'a pas la permission
  réseau et ne choisit rien à votre place — mais **ce que vous y consignez
  quitte le téléphone**, par l'application Drive. Si vous ne voulez pas de cela,
  ne l'installez pas : il n'y a pas d'option pour s'en passer.

## Divesoft

**Application non officielle, sans aucun lien avec Divesoft s.r.o.**

Le nom « Divesoft » et « ECHO » appartiennent à leur propriétaire et ne sont
employés ici que pour désigner l'appareil avec lequel l'application dialogue.
Ni Divesoft ni aucun de ses représentants n'a participé à ce travail, ne l'a
approuvé, ni n'en assume la moindre responsabilité.

Le protocole a été reconstitué par observation, à des fins d'interopérabilité.

## Installation

L'application ne passe par aucune boutique. Il faut donc autoriser
l'installation depuis une source inconnue :

1. téléchargez l'APK depuis la page des versions ;
2. ouvrez le fichier ; Android proposera d'autoriser votre navigateur ou
   gestionnaire de fichiers à installer des applications ;
3. acceptez, puis installez.

**Android 13 minimum**, et un téléphone doté du Bluetooth basse consommation.

Android 13 plutôt que 8 est un choix délibéré. En deçà d'Android 12, tout scan
Bluetooth exige la permission de **localisation**, et l'autorisation dont
dépend la sélection d'imprimante n'existe pas : l'app y réclamerait davantage
pour en faire moins. Et le dialogue Bluetooth emploie des méthodes apparues à
Android 13, qui reçoivent leurs données directement au lieu de les faire
transiter par un objet partagé où deux échanges simultanés s'écrasent. Mieux
vaut ne pas s'installer que s'installer à moitié.

L'application n'a par ailleurs été **éprouvée que sur Android 16**.

### Vérifier que le fichier est bien celui-ci

Chaque version publiée indique l'empreinte SHA-256 de son APK. Comparez-la :

```bash
shasum -a 256 sonde-0.25.0.apk
```

Toutes les versions sont signées par la même clé, dont l'empreinte SHA-256 est :

```
DB:86:5C:20:BC:AA:5D:BA:44:7B:EA:06:5D:B4:D1:0A:C6:82:C8:58:BD:48:F1:DC:B5:25:DD:75:2A:2A:C7:E4
```

Un APK signé par une autre clé ne vient pas d'ici.

## Permissions demandées

L'application **n'a pas la permission réseau** : elle ne peut d'elle-même
joindre aucun serveur. Aucune donnée n'est collectée, aucune statistique n'est
levée, et rien n'est envoyé à l'auteur ni à personne d'autre.

Une réserve, et elle est importante : depuis la 0.19.0, le **journal des
analyses** est écrit dans un dossier Google Drive **que vous désignez
vous-même**, par le sélecteur de fichiers d'Android. L'application n'y accède
qu'à travers l'autorisation que vous lui donnez sur ce dossier-là, et c'est
l'application Drive — pas celle-ci — qui le synchronise. Ce sont donc vos
mesures, dans votre Drive, mais elles ne restent plus sur l'appareil.

Elle demande **deux** permissions, et rien d'autre :

| Permission | Pourquoi |
|---|---|
| `BLUETOOTH_SCAN` | trouver l'analyseur et les imprimantes. Déclarée `neverForLocation` : Android lui interdit alors d'en déduire une position, et le système le garantit |
| `BLUETOOTH_CONNECT` | dialoguer avec l'analyseur et avec l'imprimante |

Pas de localisation, pas de stockage, pas de réseau, pas de caméra, pas de
contacts — l'accès au dossier du journal n'en demande aucune, il passe par le
cadre d'accès au stockage et n'existe que pour le dossier que vous avez choisi.
C'est vérifiable sur le fichier lui-même :

```bash
aapt2 dump permissions sonde-0.25.0.apk
```

## Licence et droits

Voir **[LICENSE](LICENSE)**. En résumé, sans que ce résumé ne s'y substitue :

- l'application peut être installée et utilisée librement, gratuitement, dans
  n'importe quel contexte ;
- le fichier peut être retransmis, mais **à l'identique** et accompagné de son
  avertissement — ni modifié, ni resigné, ni vendu ;
- le code source n'est pas publié et reste la propriété de son auteur ;
- les logotypes affichés et imprimés appartiennent à leur titulaire et ne sont
  couverts par **aucune** autorisation d'usage ;
- l'application est fournie **« en l'état », sans garantie d'aucune sorte**, et
  vous demeurez seul responsable de tout gaz que vous respirez.
