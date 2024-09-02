Partie Exécutable
=================

.. _partie_executable:

L'exécutable a été réalisé en python et fonctionne grâce au framework **Qt for Python Version 6 (PyQt6)**.

Ce logiciel a été pensé pour être exécuté à la fois sur Windows et sur Linux.

Configurer l'environnement Python
---------------------------------

Créer un environnement Python est une pratique courante pour gérer les dépendances et éviter les conflits entre les projets. Voici la méthode pour créer un environnement Python.

Créer un environnement
~~~~~~~~~~~~~~~~~~~~~~

Naviguez jusqu'au répertoire du projet (ou le répertoire où vous souhaitez créer l'environnement) :

Pour Windows
^^^^^^^^^^^^

Ouvrez Powershell, et tapez : ``set-executionpolicy remotesigned`` afin de permettre l'exécution du script d'activation de l'environnement virtuel.

Créez l'environnement virtuel (nécessaire seulement pour l'installation) :

.. code-block:: bash

    cd <C:/path/to/your/project>
    python -m venv websokeyto_env

Activez l'environnement virtuel (nécessaire avant chaque exécution) :

.. code-block:: bash

    .\websokeyto_env\Scripts\activate

Pour Linux
^^^^^^^^^^

Créez l'environnement virtuel (nécessaire seulement pour l'installation) :

.. code-block:: bash

    cd </path/to/your/project>
    python3 -m venv websokeyto_env

Activez l'environnement virtuel (nécessaire avant chaque exécution) :

.. code-block:: bash

    source websokeyto_env/bin/activate

Installer les dépendances
~~~~~~~~~~~~~~~~~~~~~~

Des dépendances sont requises au bon fonctionnement de l'exécutable, voici comment les installer :

.. code-block:: bash

    pip install -r requirements.txt

Structure du Projet
-------------------

.. code-block:: bash

    WSKT-EXECUTABLE
        ├── Assets
        │   └── Icons
        │       ├── arrowDown.png
        │       ├── arrowUp.png
        │       ├── caret-down-solid.svg
        │       ├── circle-plus-solid.svg
        │       ├── gear-solid.svg
        │       ├── power-off-solid.svg
        │       └── trash-can-solid.svg
        ├── ImportedUI
        │   ├── images
        │   └── SavedUI
        ├── Src
        │   ├── AppWindow.py
        │   ├── KeyAction.py
        │   ├── MainWindow.py
        │   ├── settings.json
        │   ├── SettingsWindow.py
        │   └── Utils.py
        ├── UI
            ├── main.ui
            ├── settings.ui
            └── tabInteraction
                ├── balayage.ui
                ├── pointage.ui
                └── temporise.ui

Lancer l'exécutable
-------------------

Accédez au dossier Src et exécutez MainWindow.py :

.. code-block:: bash

    python Src/MainWindow.py
    #python3 

Utilisation de Qt Creator pour développer
-----------------------------------------

Si vous le souhaitez, vous pouvez utiliser le logiciel **Qt Creator** pour continuer à développer l'application.

https://www.qt.io/offline-installers

Le logiciel propose une interface pratique permettant de modifier le design des fichiers XML correspondants aux UI, et permet de passer aisément du design au code.

Importer le projet dans Qt Creator
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- Pour importer le projet dans Qt Creator, démarrez le logiciel puis cliquez sur **Open Project...** et sélectionnez le fichier **Wskt-Executable.pyproject** se trouvant à la racine du projet.

- À la suite de ceci, Qt Creator vous demandera si vous souhaitez créer un nouvel environnement virtuel ou en sélectionner un existant. Si vous décidez de créer un nouvel environnement virtuel, vous aurez besoin de ré-effectuer la dernière partie de l'étape "Configurer l'environnement Python" (activer l'environnement puis installer les dépendances).

Ce qui est déjà fait / ce qu'il reste à faire
----------------------------------------------

- Dans son état actuel, l'exécutable permet d'importer une interface de CAA (Communication Alternative et Augmentée) provenant de l'éditeur WebSoKeyTo. Le design de l'interface est pleinement pris en charge et permet d'afficher l'interface telle qu'elle a été réalisée sur l'éditeur.
  
  Une archive d'interface WebSoKeyTo contient des fichiers **.ui**. Le format d'un fichier **.ui** correspond à un fichier XML et la structure de celui-ci a été imaginée par les développeurs de Qt afin de permettre d'importer efficacement des designs au sein du code. Dans une archive .zip, le fichier **App.ui** décrit le comportement graphique de la fenêtre principale de l'interface et les autres fichiers **.ui** décrivent le comportement graphique des différentes pages que l'on peut afficher sur cette même fenêtre principale.
    
  - Possibilité d'afficher des boutons avec à la fois du texte et des images (texte soit centré, soit en dessous de l'image, soit au dessus de l'image)
  - Les boutons affichés respectent toutes les propriétés définies dans l'éditeur (police de texte, position, couleur de fond, taille d'image, etc...)
  - L'interface respecte également les propriétés définies dans l'éditeur (résolution, etc...)

- L'exécutable gère un import partiel des actions définies dans l'éditeur. Actuellement, les actions capables d'être effectuées sur l'exécutable sont :
    
  - Le changement de page : Lors du clic sur le bouton, permet d'afficher une autre page sur la fenêtre principale

  - Lien internet : Le clic du bouton renvoie vers une page internet choisie

  Les actions qu'il reste à implémenter sont :

  - Écriture de message : Cela écrira un message

  - Lancement d'application : Le clic du bouton lancera une application

  - Domotique : Permettra d'effectuer une action de domotique sur des objets connectés via l'API de communication

  - Cependant, il y a des actions comme "macro" ou "ambigue" dont je ne connais pas la spécificité

- L'exécutable permet de prononcer des messages assignés à l'appui des boutons.
  
  Lorsque l'utilisateur appuie sur un bouton, une synthèse vocale prononce le message vocal correspondant.

- L'exécutable permet une gestion des paramètres de l'interface. Lorsque l'utilisateur change des paramètres, ceux-ci sont mis à jour dans le fichier **Src/settings.json** pour être réassignés lors de la prochaine réouverture. Cependant, lors de l'exécution de l'interface de CAA, un bon nombre de ces paramètres ne sont pas pris en compte.

  Paramètres pris en compte :
    
  - Chargement du fichier sélectionné par l'utilisateur dans l'onglet **Interfaces** et affichage de son interface

  - Couleur de fond de l'interface (Onglet **Visuel**)

  Tous les paramètres non pris en compte lors de l'exécution de l'interface CAA :

  - Onglet Interaction

    - Pointage 

      - A la pression

      - Au relâchement

      - Répétition

      - Délai d'activation

      - Intervalle de temps

    - Temporisé 

      - Validation

      - Délai

      - Répétition

    - Balayage

      - Intervalle de balayage (Nombre, Option 0, Option 1)

      - Validation balayage (Pression, Relâchement)

      - Options pause (Nombre, Invisibilité de l'interface)

      - Modalité de répétition (Maintien, Période, Nombre)
        
  - Onglet Visuel

    - Couleur de sélection de touche

    - Zoom des touches (Agrandissement si > 100%)

    - Opacité de l'interface (Si curseur hors de l'interface)

    - Affichage premier plan

    - Plein écran

  - Onglet Son

    - Synthèse vocale

    - Mots

    - Phrases

    - Touche courante

    - Liste de touches

  - Onglet Options Avancées

    - Activité enregistrée

    - Français

    - English
