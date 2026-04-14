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

Le test local est important pour éviter de pousser du code invalide.
Si un test échoue dans une CI, deux choses peuvent se passer:

- Si configuré comme non-bloquant, la CI donne un avertissement mais continue son
  exécution
- Si configuré comme bloquant (comportement par défaut) alors la CI échoue, il faudra
  alors résoudre via un commit supplémentaire le problème

## Partie 3 — Couverture de code et artefacts

### Question 4

#### Qu'est-ce qu'un artefact GitHub Actions ? Donnez 3 exemples d'artefacts utiles

L'intérêt d'un artefact GitHub est de persister les données choisies à la fin
d'un job, le conteneur étant détruit à la fin de l'exécution.

Cet artefact peut-être ensuite utilisé à différents buts.
Par exemple:

- Générer un rapport de test
- Utiliser un artefact dans le job suivant
- Générer des logs d'exécution de job

### Question 5

#### Qu'est-ce que la couverture de code ? Pourquoi 100% n'est pas toujours souhaitable ? <!-- rumdl-disable-line MD013 -->

Selon la [documentation de Sonar](https://www.sonarsource.com/resources/library/code-coverage/)
La couverture de code consiste à évaluer quel à quel percentile le code source de
l'application est testé.

Le taux de 100% n'est pas souhaitable et Sonar recommande plutôt une base de 80%
pour la majorité des projets, au-delà de ce palier, le résultat ne vaut peut-être
pas le taux d'investissement.

## Partie 4 — Linting et cache

### Question 6

#### Quel est le rôle d'un linter ? Pourquoi l'exécuter avant les tests dans le pipeline ? <!-- rumdl-disable-line MD013 -->

Un linter a pour de lire le code qu'on lui fournit et de le comparer aux standards
et normes porposés par les créateurs (ou la communauté) du langage.
Il permet donc de respecter les meilleures pratiques et de repérer les erreurs
lorsqu'on écrit du code.

Il est mieux de l'exécuter avant les tests de pipeline afin d'éviter que
cette dernière soit:

1. Mise en erreur si le code est erronné
2. Rejette le commit si elle a été configuré pour linter le code

### Question 7

#### Comment fonctionne le cache dans GitHub Actions ? Que se passe-t-il quand requirements.txt change ? <!-- rumdl-disable-line MD013 -->

Le cache permet d'accélérer l'exécution des pipelines, si activé pour des package
python par exemple, il créera un Hash identifiant le fichier contenant les packages.

Ensuite lorsque dans un autre job consécutif, on appelle le cache, le job cherchera
le hash du cache, s'il le trouve il s'en servira, ce qui empêche de retélécharger
chaque dépendence.

Si le fichier `requirements.txt` change, le hash changera aussi et le cache devra
être renouvellé.

## Partie 5 — Badge, protection de branche et pipeline final

### Question 8

#### Comparez les runners GitHub-hosted et self-hosted : avantages, inconvénients, et dans quel cas utiliser chacun <!-- rumdl-disable-line MD013 -->

### Question 9

#### Décrivez le workflow complet qu'un développeur doit suivre pour intégrer du code quand la branche main est protégée <!-- rumdl-disable-line MD013 -->

### Question 10

#### Quelle action avez-vous trouvée et intégrée ? Expliquez son rôle, montrez la configuration YAML que vous avez ajoutée, et décrivez le résultat obtenu. Indiquez le lien vers la page de l'action dans la marketplace <!-- rumdl-disable-line MD013 -->
