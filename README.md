# TP - DEVOPS CI/CD

Equipe 4

- EVANO Thomas
- LAMRI Yahia
- BAYRAKLI Diyar
- VAUTOUR Jessy

## Etape 2 - Définition des méthodes de gestion des branches

- une branche de développement: `dev`
- une branche d'intégration/pré-prod: `staging`
- une branche de production: `main`

Lors de nouvelle feature une nouvelle branche `feature/` a partir de `dev` puis lorsque celle-ci est complète l'on créer une pull request afin de pouvoir merge sur dev de même pour un bugfix.

Si la pull request est coché verte dans la CI ✔ et que les autres développeurs ont approuvé lors de review alors on peut merge celle-ci.

Cela déclenche donc une actualisation de la branche `dev` avec un nouveau passage de tests et build, s'ils s'effectuent avec succès alors la branche `dev` est push sur `staging`.

OK


