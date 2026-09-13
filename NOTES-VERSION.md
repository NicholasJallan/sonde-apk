# Note de version — 0.12.0

Texte à coller dans la description de la version GitHub.

---

Les étiquettes disent désormais **qui** a fait l'analyse, et deux d'entre elles
en sortent avec une MOD plus grande qu'avant.

Le prénom se saisit sur l'écran de mesure, se conserve d'une bouteille à la
suivante, et se corrige tout seul — `jean-pierre` devient `Jean-Pierre`. Il
signe le col, la seconde étiquette d'un bailout et l'étiquette de diluent ;
jamais la grande étiquette de MOD, qui ne porte que son chiffre et n'a rien à
partager.

Le loger a été l'occasion de reprendre deux compositions. Sur le **diluent**, la
date quitte le dessous du mélange pour la colonne libre à côté de lui, où elle
ne coûte plus rien : la MOD y passe de 4,8 à **5,6 cm** de chiffres. Sur le
**col**, le groupe `MOD 66 M` se centre enfin sur toute la largeur de
l'étiquette au lieu de la seule colonne que laisse la marque, et le chiffre y
gagne un cinquième de largeur sans rien perdre en hauteur.

L'écran de lancement affiche sa version dans le coin, pour qu'on sache quel
binaire tourne sans ouvrir le menu.

## Depuis la 0.10.0

La 0.11.0 n'a jamais été publiée ; ce qu'elle contenait arrive ici.

- **Le diluent tient sur une seule étiquette** au lieu de deux, avec mélange,
  MOD et ppO₂ retenue lus ensemble.
- **La MOD du col occupe toute la place qui lui revient** : la valeur est
  séparée de son unité, et le filet n'attend plus la hauteur de la marque.
- **Le CO du canal gas1 s'affiche** sur l'écran de mesure.
- **La mesure survit à ce qui arrive à l'écran** — rotation, changement de
  taille de police, multi-fenêtre. L'imprimante retenue et la ppO₂ choisie
  survivent en outre à la fermeture de l'application.
- **L'impression attend que l'imprimante ait fini de lire** avant de fermer la
  liaison : sur les envois longs, la dernière commande n'arrivait pas.

Le transport Bluetooth vers la Zebra a entre-temps rencontré une vraie ZD421t.
Le README est corrigé en conséquence — c'est la seule des limites annoncées qui
tombe.

**Lisez le [README](../../blob/main/README.md) avant d'installer.** Cette
application n'est pas un produit : elle a été écrite pour un seul plongeur, un
seul analyseur et une seule imprimante, et hors le prénom qui signe les
étiquettes, elle ne se règle pas. Vous en assumez tous les risques.

Elle produit des chiffres — profondeur maximale, équivalent narcotique, densité
— dont dépend votre sécurité. Recoupez-les toujours.

**Application non officielle, sans lien avec Divesoft s.r.o.**

| | |
|---|---|
| Version | 0.12.0 |
| Android minimum | 12 (API 31) |
| Taille | 6,4 Mo |
| SHA-256 | `546141fe0a04f34ed7afdd3dc6b0517740eb1ba27a17430750a731ca9ae758b6` |
