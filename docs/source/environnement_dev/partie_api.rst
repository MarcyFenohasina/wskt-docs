Partie API de communication
=============================

.. _partie_api:

L'API de communication a pour objectif de simplifier les échanges de l'exécutable et de l'éditeur vers OpenHab en adaptant les requêtes d'OpenHab pour le cas d'utilisation de WebSoKeyTo.

Cette API a été programmée en python, avec la bibliothèque **Click**, qui a permis d'implémenter facilement une aide à la commande, et qui a pour objectif de permettre aux nouveaux
contributeurs de comprendre rapidement comment l'utiliser.


Installation et exécution
---------------------------

- Effectuez ``pip install -r requirements.txt`` pour installer les paquets nécessaires à l'API.

- Écrivez ``python main.py <arguments>`` pour exécuter l'API avec la requête \<arguments\>.


Explication des commandes
---------------------------

L'API est divisée en deux catégories de commandes :

- Les commandes avec le préfixe **'get'** : Elles permettent d'obtenir des informations sur les things d'OpenHab (**get things** par exemple) ou sur les items.


- Les commandes avec le préfixe **'exec'** : Elles permettent de mettre à jour l'état d'un item, ou d'envoyer une commande.

*Exemples :*

.. code-block:: bash

    python main.py get things data --id <thing_id>
    python main.py get things
    python main.py exec send-command --id <item_name> --command <command_to_send>

Liste des commandes
--------------------

- **get**
    
    - **things** \
    └── *Récupérer la liste de tous les objets (Things)*
    
    - **thing**
        
        - **data** *\-\-id \<thing_id\>* \

        └── *Récupérer les données sur un objet (Thing) spécifique*

        - **status** *\-\-id \<thing_id\>* \

        └── *Récupérer le status d'un objet (Thing) spécifique*
        
        - **actions** *\-\-id \<thing_id\>* \

        └── *Récupérer les actions associées à objet (Thing) spécifique*

            */!\\ La commande actions ne fonctionne pas*

    - **items** \

    └── *Récupérer la liste de tous les items*

    - **item** 

        - **data** *\-\-itemname \<item_name\>* \

        └── *Récupérer les données d'un item spécifique*

        - **state** *\-\-itemname \<item_name\>* \

        └── *Récupérer l'état d'un item spécifique*

- **exec**

    - **send-command** *\-\-itemname \<item_name\> \-\-command \<command_to_send\>* \

    └── *Envoyer une commande à un item spécifique*

    - **update-state** *\-\-itemname \<item_name\> \-\-state \<new_state\>* \

    └── *Mettre à jour l'état d'un item spécifique*


Ce qu'il reste à implémenter
-----------------------------

Actuellement, la direction que doit prendre cette API est assez imprécise et difficile à imaginer.
En effet, l'API n'est pas encore capable de retourner une liste d'actions disponibles pour un objet ciblé.
Cela impliquerait donc de revoir la manière dont les actions des objets seraient définies sur OpenHab, afin d'avoir une commande **get actions** fonctionnelle qui permettrait l'obtention de ces actions.