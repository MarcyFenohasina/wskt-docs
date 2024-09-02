Partie API de communication
=============================

L'API de communication a pour objectif de simplifier les échanges de l'exécutable et de l'éditeur vers OpenHab en adaptant les requêtes d'OpenHab pour le cas d'utilisation de WebSoKeyTo.

Cette API a été programmée en python, avec la bibliothèque **Click**, qui a permis d'implémenter facilement une aide à la commande, et qui a pour objectif de permettre aux nouveaux
contributeurs de comprendre rapidement comment l'utiliser.

Explication des commandes
---------------------------

L'API est divisée en deux catégories de commandes :

- Les commandes avec le préfixe **'get'** : Elles permettent d'obtenir des informations sur les things d'OpenHab (**get things** par exemple) ou sur les items
\ 

- Les commandes avec le préfixe **'exec'** : Elles permettent de mettre à jour l'état d'un item

Ce qui reste à implémenter
-----------------------------

Malheureusement, la direction que doit prendre cette API est assez imprécise et difficile à imaginer. \ 
En effet, l'API n'est pas encore capable de retourner une liste d'actions disponibles pour un objet ciblé. \ 
Cela impliquerait donc de revoir la manière dont les items seraient ajoutés sur OpenHab, afin d'avoir une commande **get actions** fonctionnelle qui permettrait l'obtention de ces actions.