# Sonde — APK

Application Android qui lit l'analyseur de gaz **Divesoft ECHO** en Bluetooth et
imprime les étiquettes de bouteilles correspondantes sur une **Zebra ZD421t**.

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
| **Impression Bluetooth** | Le transport n'a **jamais rencontré une vraie imprimante**. Le langage ZPL produit a été validé contre les métriques Zebra, le lien Bluetooth ne l'a pas été. |
| **Protocole de l'analyseur** | Reconstitué par rétro-ingénierie, sans documentation du fabricant. Validé sur **un seul appareil et un seul firmware**. Sur un autre, les valeurs affichées pourraient être fausses **sans que rien ne le signale**. |
| **Largeur des caractères imprimés** | Le modèle d'avance de police est approximatif. Les textes imprimés peuvent sortir plus petits que prévu. |
| **Réglages du support** | Transfert thermique et détection par l'espace inter-étiquette sont imposés en dur. |

### Ce qu'elle ne sait pas faire

L'application n'est **pas configurable**. Ni réglage, ni option, ni préférence.

- **Un seul modèle d'imprimante** : Zebra ZD421t à 203 dpi. Sur une imprimante
  300 dpi, les étiquettes sortiraient aux deux tiers de leur taille.
- **Deux formats d'étiquettes** seulement : 100 × 150 mm et 76 × 51 mm.
- **Les étiquettes portent la marque de l'auteur**, imprimée en dur. Vous ne
  pouvez pas la retirer ni la remplacer par la vôtre.
- **Français uniquement**, **mètres uniquement**.
- Elle se connecte au **premier analyseur ECHO qu'elle trouve**. Si plusieurs
  sont allumés à portée, rien ne garantit que ce soit le vôtre.
- Aucun réglage n'est mémorisé : le choix de l'imprimante et de la ppO₂ est à
  refaire à chaque démarrage.

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

**Android 8.0 minimum.** Un téléphone doté du Bluetooth basse consommation est
indispensable.

Sur Android 8 à 11, l'analyse fonctionne mais **l'impression Bluetooth n'est pas
accessible** ; l'export du fichier d'étiquette reste possible.

### Vérifier que le fichier est bien celui-ci

Chaque version publiée indique l'empreinte SHA-256 de son APK. Comparez-la :

```bash
shasum -a 256 sonde-0.8.1.apk
```

Toutes les versions sont signées par la même clé, dont l'empreinte SHA-256 est :

```
DB:86:5C:20:BC:AA:5D:BA:44:7B:EA:06:5D:B4:D1:0A:C6:82:C8:58:BD:48:F1:DC:B5:25:DD:75:2A:2A:C7:E4
```

Un APK signé par une autre clé ne vient pas d'ici.

## Permissions demandées

L'application **n'accède pas au réseau** — elle n'en a pas la permission, et ne
peut donc rien transmettre nulle part. Aucune donnée n'est collectée, aucune
mesure n'est envoyée, aucune statistique n'est levée.

| Permission | Pourquoi |
|---|---|
| `BLUETOOTH_SCAN` | trouver l'analyseur. Déclarée `neverForLocation` : le scan n'est jamais utilisé pour en déduire une position |
| `BLUETOOTH_CONNECT` | dialoguer avec l'analyseur et avec l'imprimante |
| `BLUETOOTH`, `BLUETOOTH_ADMIN` | idem, sur Android 11 et antérieur uniquement |
| `ACCESS_FINE_LOCATION` | **Android 11 et antérieur uniquement.** Ces versions d'Android imposaient cette permission pour tout scan Bluetooth, sans rapport avec la localisation. Elle n'est ni demandée ni utilisable au-delà d'Android 11 |

## Licence et droits

Le code source n'est pas publié et reste la propriété de son auteur.

Les logotypes présents dans l'application et sur les étiquettes appartiennent à
leur propriétaire et ne sont couverts par aucune autorisation d'usage.

L'application est fournie **« en l'état », sans garantie d'aucune sorte**,
expresse ou implicite, y compris et sans limitation les garanties de qualité
marchande, d'adéquation à un usage particulier et d'absence de contrefaçon.
