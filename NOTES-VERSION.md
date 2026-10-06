# Note de version — 0.23.1

Texte à coller dans la description de la version GitHub.

---

Une version de correction, issue d'une relecture complète de la 0.22 et de
deux séances de mesures sur le matériel. Elle ne change pas l'usage : elle
retire des façons de se tromper sans le savoir.

> La 0.23.0 n'a pas été publiée : tout ce qui suit la complète.

## Les chiffres

- **Le pour cent retenu se tire du dixième affiché.** Une lecture affichée
  « 28,5 » donnait parfois NX28 sur l'étiquette : l'arrondi se faisait sur une
  valeur que l'écran ne montrait pas. Écran, étiquettes, registre et journal
  passent désormais tous par le même arrondi.
- **La MOD et l'équivalent narcotique sont ceux des tables.** La virgule
  flottante faisait tomber environ un mélange sur vingt-cinq un mètre trop
  bas ou trop haut, à la frontière d'un arrondi. La MOD reste arrondie au
  mètre inférieur, le seul arrondi qui ne promet jamais plus profond que le
  calcul.
- Le panneau en direct montre la MOD du mélange **qui sera retenu**, et non
  celle de la lecture brute : on ne voit plus 39 m avant de figer et 40 m après.

## L'analyseur

- **L'ECHO se reconnaît à l'identifiant que le Bluetooth SIG attribue à
  Divesoft**, et non plus à son nom : une enceinte Amazon « Echo » n'est plus
  prise pour un analyseur.
- **Votre ECHO est retenu.** Le dernier analyseur avec lequel la mesure a
  tourné est mémorisé par son adresse. S'il est à portée, c'est lui ; si un
  autre répond seul, l'application l'attend cinq secondes, puis se lie à
  l'autre — et le nom de l'appareil lié s'affiche toujours en tête de l'écran.
- Une liaison qui ne livre plus de mesures pendant dix secondes échoue et se
  relance, au lieu de laisser l'écran figé sur une valeur ancienne.
- Ouvrir l'application deux fois — par un raccourci, par exemple — ne crée plus
  deux sessions qui se disputent l'analyseur.

## L'imprimante

- **« Imprimer quand même »** sur un rouleau dont la longueur ne correspond
  pas à l'étiquette, quand c'est le seul problème : la confirmation nomme les
  deux longueurs, et le journal garde la trace. Un capot ouvert, un papier ou
  un ruban épuisé, une pause, ne se contournent jamais.
- **Vider la file** de l'imprimante après une coupure en plein envoi, depuis
  l'application, au lieu de l'éteindre.
- « Imprimer les 2 étiquettes » **s'arrête à la première qui n'est pas
  sortie**, au lieu d'envoyer la suivante derrière un reste.
- La recherche **dit quand elle n'a pas pu écouter** — Bluetooth éteint,
  balayage refusé — au lieu de conclure qu'il n'y a pas d'imprimante. Les
  appareils écartés se montrent, repliés, et se choisissent : une Zebra au
  préfixe d'adresse inconnu peut s'y trouver.
- Une imprimante éteinte depuis la dernière recherche reste listée, mais sans
  puissance de signal : elle ne paraît plus répondre.
- **Une imprimante qui demande une association** coupe la liaison au bout de
  trente secondes. Le message le dit désormais, avec le remède. Le cas s'est
  produit : une ZD421t gardait en mémoire un appairage qu'on avait défait côté
  téléphone seulement, et réclamait une association à ce téléphone-là à chaque
  connexion. **Ne l'acceptez pas** ; videz le cache d'associations de
  l'imprimante (commande SGD `bluetooth.clear_bonding_cache`).

## Le journal

- Chaque étiquette sortie est consignée **avec le mélange et la ppO₂ de son
  envoi**. Un rattrapage d'oxygène fait après l'impression, sans réimprimer,
  se signale dans la liste.
- **Le fichier partagé se relit après chaque écriture.** Rien ne compte comme
  envoyé qui ne se relit pas à l'identique : une écriture coupée ne peut plus
  laisser croire que le dossier a tout reçu, et « Effacer l'appareil » reste
  fermé tant que ce n'est pas le cas.
- Une copie locale illisible ne passe plus pour vide, et ne s'efface pas.
- **Une mesure que le journal n'a pas pu écrire se dit sur tous les écrans**,
  par un bandeau rouge qui mène au journal.

## La simulation

Le simulateur n'existe pas dans ce fichier. Dans la version de développement,
**rien de simulé ne part plus vers une imprimante** : le papier ne dit pas
« simulé », et une étiquette sortie se colle sur une bouteille.

---

## Ce qui n'a pas été éprouvé

La coupure en plein envoi a été provoquée sur la ZD421t : la machine abandonne
d'elle-même l'étiquette coupée. Ce que l'état de l'imprimante dit d'un travail
en attente n'a donc jamais été vu levé, et ne fait qu'avertir.

« Imprimer quand même » a été éprouvé sur la ZD421c ; le retour au bon rouleau
entre le refus et la confirmation ne l'a pas été sur papier.

Zebra présente ce Bluetooth comme réservé à son application de configuration :
une mise à jour du micrologiciel pourrait fermer cette voie, et il n'y en a
plus d'autre. L'export d'un fichier ZPL reste possible.

L'alarme de CO n'a toujours jamais été vue se déclencher sur du vrai gaz : le
capteur de l'appareil de test est en défaut.

**Application non officielle, sans lien avec Divesoft s.r.o.**

| | |
|---|---|
| Version | 0.23.1 |
| Android minimum | 13 (API 33) |
| Taille | 8,4 Mo |
| SHA-256 | `3868e1ee51b553795b3de09be32336c36a163bfa56c95fa3f454844a519071ba` |
