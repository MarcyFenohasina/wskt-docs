Bienvenue sur la documentation de WebSoKeyTo !
===============================================

La plateforme WebSoKeyTo est un environnement en ligne pour la conception et l'adaptation d'aides techniques de CAA (communication améliorée et alternative), qui peut être facilement utilisée sans compétences techniques spécifiques. La plateforme WebSoKeyTo est basée sur SoKeyTo (connaissances antérieures de l'IRIT - Institut de Recherche en Informatique de Toulouse)

.. note::

   Ce projet est en cours de développement.


Le projet WebSoKeyTo comprend deux solutions logicielles, à savoir un éditeur d'interfaces, et un exécuteur d'interfaces.

L'éditeur d'interface est une solution en ligne permettant de concevoir une interface spécifique et de définir des actions correspondant aux besoins d'un utilisateur.

L'exécuteur d'interface est une solution exécutée par l'utilisateur lui même, permettant d'afficher une interface précédemment définie dans l'éditeur et de pouvoir ainsi exécuter les actions définies pour l'utilisateur.
Cette solution comprend également (**#A IMPLEMENTER#**) une interaction contextuelle par rapport à la localisation de l'utilisateur, adaptant l'interface selon la pièce où il se trouve.


Ces deux solutions permettent l'interaction avec des objets connectés, grâce à la communication avec OpenHab, une plateforme open-source de domotique qui permet de contrôler et d'automatiser divers appareils et systèmes dans une maison intelligente.


Dans cette documentation vous trouverez :

- Un manuel d'utilisation expliquant l'installation et la configuration du matériel, l'explication des configurations appropriées dans OpenHab ainsi que l'utilisation des deux solutions logicielles

- Une documentation permettant la compréhension de l'environnement de développement


Contents
--------

.. .. toctree::

   
..    environment
..    config
..    partie_editeur
..    partie_exec
..    api
..    code
..    usage

.. toctree::
   manuel_utilisation/manuel_utilisation
   environnement_dev/environment_dev