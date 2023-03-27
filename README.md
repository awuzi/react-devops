# TP - DEVOPS CI/CD

Equipe 4

- EVANO Thomas
- LAMRI Yahia
- BAYRAKLI Diyar
- VAUTOUR Jessy

## Etape 2 - Définition des méthodes de gestion des branches

- plusieurs branches de développement nommé en fonction des developpements en cours: `feature-`, `bugfix-` ...
- une branche d'intégration ou sont merge les branche de developpement une fois review: `dev`
- une branche pré-prod: `staging`
- une branche de production: `main`

Notre git flow:

- Lors de nouvelle feature une nouvelle branche `feature-` est crée a partir de `dev` puis lorsque celle-ci est jugée finale par le developpeur, il créer une pull request afin de pouvoir merge sur dev.
- Si la pull request est coché verte dans la CI ✔ car pas de conflits, que les eventuels tests passent et que les autres développeurs ont approuvé lors de review alors on peut merge celle-ci.
- Cela déclenche donc une actualisation de la branche `dev` detecté par jenkins qui va alors lancer un build de l'application a partir de la nouvelle version de cette branche.
- Une fois le déploiment de la branche `dev` réalisée un build et déploiement est effectuer sur la branche `staging`
- Une fois le déploiment de la branche `staging` réalisée un build et déploiement est effectuer sur la branche `main`.

## Example de Jenkins file qui met a jour, build et deploie la branche `staging`

[Jenkinsfile](./Jenkinsfile)
