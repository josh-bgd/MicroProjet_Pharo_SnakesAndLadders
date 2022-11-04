# MicroProjet_Pharo_SnakesAndLadders
Il s'agit de mon premier projet de programmation. Voir le dépot de mon professeur pour installer l'AppMaker : https://github.com/bouraqadi/PharoMisc

Description du projet Pharo

Introduction : 

Mon projet consistait en la reproduction du fameux jeu Snakes and Ladders. J’ai décidé d’ajouter une petite nouveauté afin d’apporter un peu de fraicheur à cet ancêtre des jeux. Le principe de base est assez simple : un serpent rampant sur une sol – de taille fixe - dont la taille croît au fur et à mesure qu’il mange (des pommes, oui un serpent qui mange des pommes : Welcome to 2022). 

Trois difficultés : 
1 - le serpent ne peut pas se manger lui-même = pas de collision avec son propre-corps,
2 - sa vitesse augmente avec sa taille,
3 - le sol n’est pas extensible (grille de taille fixe).
Ainsi plus il grandit, plus il faut être minutieux dans ses choix de déplacements tout en y accordant de moins en moins de temps.

L’ajout apporté au jeu est un « Bad fruit ». Un fruit qui, s’il est mangé par le serpent, le fait rétrécir (d’une taille). Il peut s’avérer utile lorsque le serpent devient trop grand. Ce fruit-là n’engendre ni de perte ni gain de point, il ne sert qu’à rendre la partie plus intéressante. La concurrence entre les joueurs ne se limite plus qu’à la taille de la grille (une fois le serpent « trop » grand il n’y a plus de place pour se déplacer) sur laquelle ils jouent mais sur leur façon de gérer la taille de leur serpent.

Documentation : 

	Les règles du jeu

0)	Aller dans la classe EzApp, puis dans la sous classe EzMicroProjetApp, lancer la démo dans Class Side.
1)	Pour commencer à jouer, appuyer sur la barre espace.
2)	Les déplacements se font avec les quatre flèches du clavier. 
3)	Vous pouvez choisir de recommencer la partie en choisissant « oui » avec les flèches du clavier et appuyer sur espace. Vous pouvez tout simplement arrêter de jouer, en choisissant « non ».





Les méthodes 

Protocole d’initialisation « initialization » : s’y trouvent les méthodes d’initialisions (sans blagues), donc de création des fruits (initFruit), bad fruits (initBadFruit), du serpent (initSnake), mais aussi de la grille (initMap)* qui est une succession alternée de vide et de carrés de bordure grise et de même couleur que le fond de la fenêtre. L’« initSnake » possède un thread pour l’exécution en parallèle de l’avancée régulière du serpent ainsi que des commandes données par le joueur. Enfin, l’« initialize » pour  tout regrouper sur une même fenêtre.

Protocole « Action » : s’y trouvent les méthodes accordant les actions à exécuter par le programme, attribuées aux différentes touches du clavier.

Protocole « Collision » : s’y trouvent les méthodes créant les effets qu’ont les collisions avec un « good fruit », « Bad fruit » et bien évidemment avec soi-même « collisionSelf ». La méthode « fruitBadCollsion » est reliée à la méthode « removeSquare » elle-même liée au GameOver le cas échéant.

Protocole « Game » : s’y trouvent les méthodes du fonctionnement global du jeu.

-	« GamePlay » : regroupe les méthodes de mouvements du serpent (du protocole « Move ») ainsi que les différentes vérifications à faire à chaque pas du serpent, permettant de vérifier s’il y a collision ou non.

-	« GameOver » : comme son nom l’indique, fait passer le booléen GameOver à vrai lorsqu’une condition de fin de partie est remplie.


-	« GameRestart » : pour recommencer le jeu sans relancer la fenêtre EzDrawingBoard .

Protocole « Setter » : contenant la méthode grilSize pour initialiser le nombre de carreau par grille pour toute la partie.

Protocole « squares » : s’y trouvent les méthodes d’ajout de carré à la suite de la chaîne ou de retrait en fonction de s’il s’agit d’un good ou bad fruit qui est mangé. Dans la méthode « removeSquare » il y’a une condition pour que la taille du serpent ne soit pas déjà égale à 1, auquel cas la partie se termine (bad fruit à consommer avec modération !). Les « addSquareLeft » « -Right » « -Up » etc. Sont faites pour que l’ajout de carré à la suite du serpent ne crée pas de collision avec ce dernier en fonction de la direction dans laquelle il avance.

Lien YouTube de la vidéo « démonstration » du jeu : 

https://youtu.be/XuCmBHpG1BE


*J’ai voulu créer une Map à la main à l’aide de la classe EzBox déjà implémentée d’abord pour avoir accès aux origines de chaque carreau de la grille (pratique pour déplacer le serpent), mais aussi pour pouvoir modifier le nombre de carreau, leur taille en fonction de celle de la fenêtre et leur couleur (on essaye de garder un certain coté esthétique derrière toute cette technique).
![image](https://user-images.githubusercontent.com/106586037/200013512-ec4f148e-532d-49a7-af0a-757d3bebfb88.png)

