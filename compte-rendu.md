# Compte Rendu

## Partie 1 — Premier workflow GitHub Actions

### Question 1

#### Décrivez la structure du fichier ci.yml : que signifient on, jobs, runs-on, steps et uses ? <!-- rumdl-disable-line MD013 -->

`on` permet de cibler deux choses:

- Sur quel type d'action la pipeline sera délenchée (sur un push ou pull request)
- Quelle branche sera ciblée (seulement sur main)

`jobs` définit l'ensemble des tâches effectuées dans la piepeline.

`runs-on` définit le conteneur Docker qui sera utilisé pour le job.

`steps` chaque actions du job en cours, exécutés de manière séquentiels.

`uses` quelles actions de la marketplace sont utilisées pour effectuer le step.

## Partie 2 — Tests automatisés de l'application web

### Question 2

#### Expliquez le rôle de la fixture client dans les tests Flask. Pourquoi utilise-t-on app.test_client() plutôt que de lancer le serveur ? <!-- rumdl-disable-line MD013 -->

Selon la [doc flask](https://flask.palletsprojects.com/en/stable/testing/), une fixture a pour but d'écrire du code
réutilisable pour les tests.
La fonction `app.test_client()` quant à elle permet faire une requête à l'application
sans démarrer le serveur, ce qui a pour avantage de faire remonter les erreurs
directement.

### Question 3

#### Pourquoi est-il important de tester localement avant de pousser ? Que se passe-t-il si un test échoue dans la CI ? <!-- rumdl-disable-line MD013 -->

## Partie 3 — Couverture de code et artefacts

### Question 4

#### Qu'est-ce qu'un artefact GitHub Actions ? Donnez 3 exemples d'artefacts utiles

### Question 5

#### Qu'est-ce que la couverture de code ? Pourquoi 100% n'est pas toujours souhaitable ? <!-- rumdl-disable-line MD013 -->

## Partie 4 — Linting et cache

### Question 6

#### Quel est le rôle d'un linter ? Pourquoi l'exécuter avant les tests dans le pipeline ? <!-- rumdl-disable-line MD013 -->

### Question 7

#### Comment fonctionne le cache dans GitHub Actions ? Que se passe-t-il quand requirements.txt change ? <!-- rumdl-disable-line MD013 -->

## Partie 5 — Badge, protection de branche et pipeline final

### Question 8

#### Comparez les runners GitHub-hosted et self-hosted : avantages, inconvénients, et dans quel cas utiliser chacun <!-- rumdl-disable-line MD013 -->

### Question 9

#### Décrivez le workflow complet qu'un développeur doit suivre pour intégrer du code quand la branche main est protégée <!-- rumdl-disable-line MD013 -->

### Question 10

#### Quelle action avez-vous trouvée et intégrée ? Expliquez son rôle, montrez la configuration YAML que vous avez ajoutée, et décrivez le résultat obtenu. Indiquez le lien vers la page de l'action dans la marketplace <!-- rumdl-disable-line MD013 -->
