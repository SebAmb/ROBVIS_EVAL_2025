# Sujet Evaluation vision par ordinateur UV RobVis 2025

Ce sujet de 2h00 comporte deux volets.

Dans le premier volet, il s'agit de détecter et de compter les petis dragibus par couleur.

Dans le second volet (Etape 1 à 3), il s'agit de développer le script python capable de détecter les **objets présents** 
dans une séquence d'images prise à partir la caméra de surveillance d'un carrefour et de les classer en 3 classes (voiture/piéton).

Pour cela, vous vous appuierez très majoritairement sur les codes que vous avez testés durant les séances de TP précédentes et tout particulièrement
ce qui vous a été montré en matière de segmentation et de détection d'objets. Tout est possible sauf l'usage de ChatGPT ou tout autre modèle génératif.
Vous avez le droit à tous les codes que vous avez réalisés.  

Vous ferez tous vos tests du volet 2 sur la vidéo que je vous ai fournie (***carrrefour640x360.mp4***) et qui est dans le zip téléchargeable :

![](carrefour.gif)

Attention c'est un travail individuel. Il est question d'évaluer ce que chacun d'entre vous a retenu de cette partie de l'UV.
Veillez bien à répondre à chaque étape afin que je puisse vous évaluer de manière progressive et respectez bien le nom des fichiers .py
que je vous demande de produire. **Vous nous remettrez tous les scripts .py dans une archive compressée nommée prenom.nom.zip que vous m'enverrez (sebastien.ambellouis@imt-nord-europe.fr)**.

## Volet 1 : Détection des dragibus

Voici l'image que vous traiterez :

![](dragibus.jpg)

Sur cette image, vous observez un nombre de bonbons de différentes couleur. Je vous propose de produire deux scripts :
1) volet1_script1.py : vous permettra de détecter tous les bonbons et d'en déterminer leur nombre.
2) volet1_script2.py : vous permettra de déterminer le nombre de bonbons par couleur.

*IMPORTANT* : je ne vous demande pas de déterminer de manière automatique les classes de couleur. A vous de régler les seuils
qui vous permettront de segmenter toutes les formes.
 
## Volet 2

### Etape 1

Afin de détecter les objets présents dans une image *t* de la séquence, un moyen simple est de faire la différence entre cette image *t* et une image du "fond" vide i.e. acquise lorsqu'aucun objet n'y est présent. Dans le cadre de ce carrefour, l'image de fond est (***bg640x360.png***). Pour faire une différence entre deux images vous utilserez la fonction ```cv.absdiff(im1,im2)``` qui calcule la valeur absolue de la différence de deux images : *diff* pour faire la différence et *abs* pour en faire la valeur absolue et éviter les valeur négative. Il est assez facile d'imaginer qu'elle sera le résultat d'une telle différence.

Dans cette première étape je vous demande donc de produire le script python *volet2_script1.py* qui réalise les actions suivantes :

- le chargement de l'image de fond ;
- l'ouverture et la lecture de chaque image de la vidéo ;
- la différence entre l'image de fond et chaque image de la vidéo ;
- l'affichage (dans deux fenêtres différentes) de l'image de la vidéo et de l'image différence.

Contrairement au volet 1, vous opèrerez sur des images en niveau de gris donc il faudra veiller à convertir les images.

### Etape 2

Dans l'étape 1, vous avez réalisé la détection des objets présents dans la scène. Dans cette deuxième étape, je vous demande d'écrire le script *volet2_script2.py* qui vous permettra finalement d'afficher les contours du masque de chaque objet présent dans la scène. Vous combinerez de manière judicieuse les étapes suivantes :
- de procéder (par binarisation) à la création du masque de chaque objet ;
- de nettoyer (supprimer les petites régions, le bruit etc.) ce masque avec des opérateurs morpholgiques (filtre médian, dilatation, fermeture etc.). Veillez à bien remplir toutes les formes ainsi détectées  ;
- de segmenter ce masque en plusieurs régions de pixels connexes ; 
- d'afficher tous les contours de ces régions en vert sur l'image.

### Etape 3

Je vous demande de modifier la partie du code de l'étape 2 afin de produire le script *volet2_script3.py* capable finalement de compter dans chaque image les instances des deux classes considérées (voiture, piéton). Pour cela vous pourrez extraire des caractéristiques de forme sur les ensembles connexes trouvés précédemment. Vous pourrez, si nécessaire, choisir une ou plusieurs caractéristiques qui permettrons de modéliser le mieux ces deux classes. 

Afin d'illustrer le résultat de votre algorithme,vous dessinerez le contour des véhicules motorisés en rouge et celui des piétons en vert sur chaque image de la vidéo.

### Etape 4

Dans cette dernière étape, proposez un algorithme de comptage des objets qui traversent le milieu du carrefour de gauche à droite ou de droite à gauche. Vous ferez ce comptage pour chaque classe (*volet2_script4.py*).

Attention, pour réaliser ce comptage vous devrez mettre en place un algorithme de suivi simple de chaque objet détecté dans l'étape 3 afin de limiter le surcomptage et aussi de déterminer le sens de la traversée.

Afficher 4 compteurs : un compteur gauche/droite et un compteur droite/gauche pour chacune des deux classes.

**BON COURAGE A VOUS ET BONNE CONTINUATION !**
