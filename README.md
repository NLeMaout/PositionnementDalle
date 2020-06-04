# PositionnementDalle
IA permettant de déterminer la position d'une dalle de façon optimum, connaissant l'emplacement de ses voisines
Le fichier contentant les entrées et sorties pour l'apprentissage peuvent se télécharger ici :
https://u.pcloud.link/publink/show?code=XZJjd6kZq8UqUl6gnDLfQRQM8bN9D0g6Dl37
(216 Mo, zippé)

Il s'agit de déterminer la position optimum d'une dalle dans l'espace 3D, en fonction des plaques voisines.
J'ai une base de donnée conséquente sur des "bonnes" positions de dalle en fonction de ses voisines.
J'ai donc généré environ 1 millions de données d'entrées et des sorties pour entraîner le modèle.
Les 1er résultat sont pas mals mais je souhaiterais améliorer la prédiction.

Les données d'entrées sont générés comme ceci :
X11, Y11, Y11, X12, Y12, Z12, X13, Y13, Z13, X14, Y14, Z14, Normal1X, Normal1Y, Normal1Z, X21, Y21, Y21,..., Znm,NormalnX, NormalnY, NormalnZ,...
avec 
  n = le numéro de la plaque (15 dalles en tout)
  et m, le numéro du coin de la dalle (4 coins)
 exemple :
  X11 = Coordonnées X du coin 1 de la dalle 1
  Y21 = Coordonnées Y du coin 1 de la dalle 2
  Z34 = Coordonnées Z du coin 4 de la dalle 3
  Normal1X = composante X de la normale de la dalle 1
  ...
Les données d'entrées ont donc 225 données par ligne (15 dalles * ((3 coords * 4 coins) + 3 composantes normal) = 15 * (12+3) = 225.
J'ai inclus les normales de chaque dalle car je sais que c'est une données importante pour résoudre le problème.

Et les sorties sont les coordonnées des 4 coins de la dalle à positionner :
X1, Y1, Y1, X2, Y2, Z2, X3, Y3, Z3, X4, Y4, Z4
donc 4 * 3 = 12 données de sortie

Donc le reseau à 225 entrées et 12 sorties.
Les valeurs des coordonnées et des composantes des normales varient entre -1 et +1.
