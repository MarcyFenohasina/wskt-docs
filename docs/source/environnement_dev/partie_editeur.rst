Partie Editeur
==================

.. _partie_editeur:

La plateforme d'édition WebSoKeyTo est un logiciel permettant de concevoir des interfaces de communication alternative augmentée (CAA).

La plateforme est actuellement composée de deux pages : Couche et Interface.
Elle est en cours de conception et est à la version 2.1 actuellement.

Installation et exécution
--------------------------

Procédure d'installation
~~~~~~~~~~~~~~~~~~~~~~~~

Pour utiliser la plateforme, il est nécessaire d'installer les dépendances requises via le gestionnaire de paquets **npm**.

Afin de pouvoir utiliser le gestionnaire de paquets **npm**, vous aurez besoin au préalable d'installer **NodeJS** :

https://nodejs.org/en

Une fois installé, naviguez dans le répertoire du projet puis **Partie Editeur** -> **WebSoKeyTo** et ouvrez un terminal à cet endroit.

Effectuez ensuite la commande :

.. code-block:: bash

    npm install

afin d'installer la liste des paquets décrits dans le fichier **package.json**.

Exécution
~~~~~~~~~

Une fois les paquets installés, vous pouvez maintenant lancer l'éditeur en effectuant la commande :

.. code-block:: bash

    npm start

Cette commande va lancer le script de lancement du serveur web comme décrit dans la partie **"scripts"** du fichier **package.json** :

.. code-block:: json

    "scripts": {
        "start": "rsbuild dev --open http://localhost:3000/websokeyto/v4",
        "build": "rsbuild build",
        "preview": "rsbuild preview"
    },

Ce script démarre **rsbuild**, l'outil de compilation et de lancement du serveur utilisé pour ce projet.

Travaux des années antérieures
-------------------------------

Ajouts de fonctionnalités de domotique
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**fichier *src\components\interface\SousMenu.js* :**

**const *typeToAction* (33-49)**  
Constante qui permet de stocker les différentes actions possibles en fonction du type de l'item.
Établi suivant la documentation d'openHAB sur les items : https://www.openhab.org/docs/configuration/items.html

**const *[itemList, setItemList]* (70)**  
Hook d'état permettant de stocker les objets récupérés sur OpenHAB.

**const *[selectItem, setSelectItem]* (72)**  
Hook d'état permettant d'enregistrer l'item sélectionné.

**const *[selectCommand, setSelectCommand]* (74)**  
Hook d'état permettant d'enregistrer la commande sélectionnée.

**useEffect()** (124-134)  
Fonction permettant la mise à jour de la liste des items avec une requête GET à l'API d'OpenHAB.  
**->** Cette fonction est probablement obsolète, puisque une API a été développée pour simplifier les requêtes vers OpenHAB.

Affichage des éléments React :

- **(1147-1165)**  
  Affichage de la liste déroulante contenant les items disponibles.

- **(1166-1184)**  
  Affichage de la liste déroulante contenant les commandes disponibles pour l'item sélectionné.

Travaux de l'année 2023-2024
----------------------------

L'application a subi une refonte complète de la fonctionnalité d'exportation des interfaces de CAA.
En effet, elle devait être capable de répondre aux nouvelles exigences de l'exécutable (Refonte de l'exécutable avec le framework Qt pour Python).

Les travaux ont consisté à simplifier la syntaxe des fichiers XML exportés (extension **.ui**, anciennement **.wskt**) et permettre une importation native du design des interfaces avec Qt.

Cette fonctionnalité d'exportation se base sur la modification de templates d'interfaces / de composants Qt (contenus dans le dossier **src/xml_templates/**), en remplaçant les propriétés par défaut du template par les propriétés choisies par l'utilisateur lors de l'édition de l'interface, comme les boutons (texte, couleur, image), ou encore la taille de l'interface, par exemple.

L'éditeur est également capable d'assigner des actions à des boutons, en les stockant dans un fichier **Actions.json**.  
Actuellement, l'exportation de la plupart des actions est gérée par l'éditeur **('txt', 'execution', 'lienInternet', 'chgmtCouche')**.

Ces implémentations se trouvent dans le fichier **src/components/commun/ParseStateToXML.js**.

Ce qu'il reste à implémenter
----------------------------

- Pour la fonctionnalité d'exportation d'interfaces de CAA, la plupart des actions ont été implémentées, mais il manque tout de même l'action **'domotique'** qui n'a pas encore été ajoutée, ainsi que les actions **'macro'** et **'ambigue'**, dont je ne connais pas les spécificités.

\

- Par ailleurs, la fonctionnalité de balayage des boutons n'est également pas prise en compte lors de l'exportation.  
  Pour implémenter l'exportation de cette fonctionnalité, il serait probablement judicieux de créer un nouveau fichier **JSON** dans lequel se trouveraient les informations de balayage. Sinon, si cela simplifie les choses, se contenter de rajouter une propriété (property) **XML** à chaque page de l'interface (sauf **App.ui**, car c'est la fenêtre principale), ce qui permettrait à chaque page d'avoir des informations sur son balayage associé.

\

- Comme nous l'avions évoqué précédemment, la fonctionnalité d'exportation d'interface a subi une refonte complète (**ParseStateToXML.js**), mais la fonctionnalité d'importation, elle, reste inchangée à ce jour.  
  Une refonte complète de cette fonctionnalité est donc nécessaire.  
  Pour refaire la fonctionnalité d'importation, il sera nécessaire d'étudier la structure d'une interface exportée depuis l'éditeur WebSoKeyTo, en s'aidant du code écrit dans **src/components/commun/ParseStateToXML.js** pour mieux comprendre à l'inverse comment effectuer le processus d'importation.

  Le code à ré-implémenter se trouve dans le fichier **src/components/commun/ParseXMLToState.js**.
