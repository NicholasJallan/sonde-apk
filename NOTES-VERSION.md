# Note de version — 0.27.0

Texte à coller dans la description de la version GitHub.

---

Une version d'ajout : **l'application peut vous dire qu'une version plus
récente est publiée**. Les étiquettes ne changent pas d'un point : la mise en
page et le ZPL sont ceux de la 0.26.1.

## Mises à jour

- Au premier lancement, une question : **vérifier les nouvelles versions ?**
  Elle dit pourquoi, ce qui part et ce qui se passe sans. Rien ne part avant
  votre réponse.
- Si vous l'avez permis, l'application demande à GitHub, à chaque lancement,
  le numéro de la dernière version publiée ici. Quand la vôtre n'est plus la
  plus récente, un message le dit au lancement, et **Réglages → Mises à
  jour** offre d'ouvrir sa page dans le navigateur.
- Ce qui part : une seule requête vers `api.github.com`. GitHub voit
  l'adresse IP de l'appareil et la version de l'application — ni mesure, ni
  nom, ni journal.
- **Sans réseau, ou si vous refusez, rien ne change** : aucune erreur, rien
  de bloqué, l'application fonctionne entièrement hors ligne. Le choix se
  change à tout moment dans les réglages.

## Une permission de plus

`INTERNET`, pour cette seule requête. Android l'accorde à l'installation sans
rien demander : c'est l'application qui pose la question. Voir « Permissions
demandées » dans le README.

**Application non officielle, sans lien avec Divesoft s.r.o.**

| | |
|---|---|
| Version | 0.27.0 |
| Android minimum | 13 (API 33) |
| Taille | 9,0 Mo |
| SHA-256 | `f7a68918f4e147d1329a3831922782f69ae02ab8175106e4e026b136e6ce5fa8` |
