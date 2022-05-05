# Voting App

Exemple d'une application micro-services.  
Cette application se décompose ainsi:  
- __vote__: serveur web python permettant à l'utilisateur externe de faire un choix
- __redis__: serveur redis mémorisant de façon temporaire le vote
- __result__: serveur web nodejs affichant les pourcentages de votes
- __postgres__: serveur postgresql mémorisant de façon permanente les votes
- __worker__: programme en boucle infinie assurant le relais entre redis et postgres 

![Schéma](/assets/votin-app-schema.png)

Les 5 composants de cette application seront déployés dans un cluster kubernetes/openshift.  

## redis
Création d'un déploiement et d'un service associé par import 
dans le projet des fichiers yaml situés dans le dosser redis 

## vote
Création d'une application Python depuis le catalogue.  
Modification de la configuration de build: Docker Strategy afin d'utiliser le Dockerfile.
Modification du service. targetPort 5000

## postgres
Création d'une application Postgresql depuis le catalogue.

## result
Création d'une application Nodejs depuis le catalogue.  
Ajout de la variable d'env PORT=8080

## worker
Création d'une application .NET depuis le catalogue.  
Modification de la configuration de build: Docker Strategy afin d'utiliser le Dockerfile.