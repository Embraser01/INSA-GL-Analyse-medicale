# Projet Génie Logiciel - Analyse médicale

[![license](https://img.shields.io/github/license/Embraser01/INSA-GL-Analyse-medicale.svg)](./LICENSE.md)
[![build](https://api.travis-ci.org/Embraser01/INSA-GL-Analyse-medicale.svg?branch=prod)](https://travis-ci.org/Embraser01/INSA-GL-Analyse-medicale)

# Sommaire
1. [Presentation](#presentation)
2. [Utiliser l'application](#utiliser-lapplication)
3. [Contribuer](#contribuer)


## Presentation
  Ceci est un projet fait en Génie Logiciel 3IF à l'INSA de Lyon. Le sujet est disponible [ici](docs/sujet.pdf)
  Auteurs :
*    Marc-Antoine FERNANDES
*    Julia LU DAC
*    Lucas ONO
*    Tianhao WU
*    Ye YUAN

_Remarque :_ L'ensemble de la documentation est disponible dans le dossier [`docs`](docs/)

-------------------------------------------------------------------------------

## Utiliser l'application

### Serveur

L'application serveur permet d'évaluer les maladies possibles qui peuvent être incluses dans un génome. 

##### Fichiers utilisés

Il s'appuie sur un fichier contenant un dictionnaire des maladies qu'il est capable d'évaluer. 

##### Démarrage du serveur

Lorsque l'interface est lancée, un numéro de port sur lequel doit démarrer le serveur est demandé, 
ainsi que le nom du fichier contenant le dictionnaire de maladies. C'est le port sur lequel sera lancée l'application serveur. 
Ces paramètres choisis, il suffit de cliquer sur le bouton "Start Server", qui démarrera le serveur si tout fonctionne.
Un serveur en exécution est capable de répondre à des requêtes de client arrivant sur son adresse IP et son numéro de port. 
Ces requêtes doivent concerner l'une des trois fonctions : 

* Fournir la liste des maladies du dictionnaire

* Indiquer si un risque de maladie est présente dans un génome

* Fournir la liste des risques de maladie dans un génome


##### Diffusion de l'adresse IP et du port via multicast

Un bouton "Start Multicast" permet au serveur d'envoyer à intervalles réguliers (2.5 s) son adresse IP et
le port de connexion sur une adresse multicast, pour en informer les clients. L'adresse IP est 225.6.7.8 et le port est 5678.
Le bouton "Stop Multicast" permet d'arrêter ces envois.


##### Quitter
Un bouton permet de quitter l'application à tout moment.


##### Erreurs possibles 
Lorsque le fichier du dictionnaire des maladies ou que le port sur lequel vous voulez démarrer est déjà occupé, le serveur ne démarre pas 
et vous devrez spécifier une autre valeur.


--------

### Client

L'application cliente permet d'obtenir des évaluations des maladies à risque sur des génomes de patient.
Pour cela, elle envoie des requêtes à des serveurs qui lui envoient la réponse.


##### Evaluer une analyse médicale


C'est la fonction primaire de l'application. Lorsque l'on clique sur ce bouton, une fenêtre s'ouvre avec 3 boutons. Chaque bouton permet d'envoyer une requête à un ou plusieurs serveurs :

* Get diseases : Vous recevrez la liste des maladies à risque que le serveur cible est capable d'évaluer.

* Evaluate All Disease : Le génome à évaluer est demandé. Vous recevrez la liste de l'ensemble des 
maladies à risque que les serveurs répertoriés ont trouvé sur ce génome.

* Evaluate One Disease : Le génome à évaluer et la maladie à chercher sur ce génome sont demandés. 
Vous recevrez une réponse "Yes" ou "No" lors de la présence ou non de la maladie sur le génome.

##### Gestion des serveurs enregistrés
Une fenêtre s'ouvre. 
* Update Servers List : met à jour les serveurs répertoriés dans la base de données. 

* Add Server : permet d'ajouter manuellement un serveur dans la base de données. 
Son adresse IP et son nom sont demandés. 

* Remove Server : permet d'enlever manuellement un serveur répertorié de la base de données. 
Son adresse IP est demandée. 


##### Quitter
Un bouton permet de fermer l'application à tout moment.

##### Erreurs possibles 
* Impossible de lire le fichier contenant le génome
* Impossible de manipuler la base de données des serveurs répertoriés
* Erreur de réseau 


-------------------------------------------------------------------------------

## Contribuer

### Dépendance

* [Visual Studio 2017+](https://www.visualstudio.com/)

### Configurer l'environnement

Pour ouvrir le projet, il suffit de cloner 
le projet et d'ouvrir la solution sur Visual Studio (VS 2017+)


### Lancer les tests

Les tests utilisent la librairie [_Catch_](https://github.com/philsquared/Catch).


Pour que les tests fonctionnent, il faut configurer les projets pour 
que le dossier de travail soit la racine de la solution. 

Pour cela, il suffit de faire : clic droit sur _ServerTests_ > Onglet
_Deboggage_ > dans _Dossier de travail_ remplacer `$(ProjectDir)` par `$(SolutionDir)`.

Refaire la même chose pour _ClientTests_

Maintenant pour lancer les tests, il faut soit lancer l'executable généré par VS,
soit utiliser l'extension [_Resharper C++_](https://www.jetbrains.com/resharper-cpp/) 
qui offre une interface de test. Dans ce cas là, il faut lancer les tests en faisant 
Clic droit sur le projet > Run Unit Test


## Licence

[Copyright (C) 2017  Marc-Antoine FERNANDES, 
Julia LU DAC, Lucas ONO, Tianhao WU, Ye YUAN](./LICENSE.md)
