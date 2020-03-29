ATTENTION : Avant de lancer le programme, je vous invite à changer l’adresse des deux fichier .txt présents à la 9eme et 13eme ligne de la classe Sibra (main).

UTILISATION :
Une fois le programme lancé, vous serez guidé. Il suffira de lire et de répondre aux instructions.
Premièrement, la liste des arrêts sera affichée. Chaque arrêt se verra attribuer un numéro. 
- On vous demandera alors de taper le numéro de l’arrêt duquel vous souhaitez partir. 
- Validez.
- On vous demandera ensuite le numéro de l’arrêt vers lequel vous voulez aller.
- Validez.
- On vous demandera a quelle heure vous voulez partir (pas nécessairement une heure correspondante à un horaire de bus). Ecrivez le sous la forme h :mm ou hh :mm (ces instructions vous seront rappelées). Exemple : 7 :32 ou 18 :43.
- Validez.
Il va alors s’afficher la liste des arrêts que vous allez devoir parcourir. Pour chacun de ces arrêts, il sera affiché son heure de départ, et l’heure d’arrivée dans l’arrêt d’après. 
Le programme est fait de sorte à ce que vous arriviez à destination le plus vite possible.


CODE :
Presque chaque ligne du code est commentée. Nous expliquerons ici son fonctionnement global. Pour analyser en détail comment chaque action se produit, veuillez vous référer au code et à ses commentaires.

On possède deux documents textes, correspondant chacun aux horaires d’une ligne de bus.
-	On prend le premier document texte.

-	On lit la première ligne, il s’agit de la liste des noms des arrêts. On récupère cette liste et créé un objet de type Arret pour chaque arrêt. 

-	Il y a une ligne vide, puis chaque ligne contient les horaires du trajet allez d’un arrêt. Pour chaque arrêt, on récupère ces horaires et les entre dans l’objet de type Arret correspondant (sous forme de liste de String).

-	Il y a une seconde ligne vide, puis chaque ligne contient les horaires du trajet retour d’un arrêt. On fait la même chose, en stockant les horaires dans une liste différente.

-	On prend le deuxième document texte.

-	On réitère le processus.

-	On a fini de lire les fichiers texte.

-	On crée une liste générale qui réunit les arrêts des deux liste précédentes (c’est-à-dire des deux fichiers textes).

-	Dans chacune des deux premières listes d’arrêts, on va créer les arcs entre les arrêts qui formeront le graphe. (Pour cela on met en relation les horaires d’un arrêt et de celui d’après pour la liste des horaires à l’allez, et d’un arrêt et celui d’avant pour la liste des horaires au retour).

-	On rassemble les arcs des deux listes dans la liste générale en faisant attention à bien les disposer sur les bons arrêts. Notre graphe est alors formé. 
Détail : On remarque dans le code qu’on n’a pas pu copier les arrêts de chaque liste dans la liste générale car dans les deux listes, un même arrêt est désigné par un objet différent. On recrée donc chaque arrêt mais on n’y entre pas ses horaires. Nous n’en avons pas besoin car nous récupérons les arcs qui forment le graphe juste après.
De même pours les arcs, on les copie mais on prend soin de changer leur destination par le nouvel objet (c’est-à-dire un arrêt de type Arret) correspondant.
-	Maintenant que le graphe est fait, on le parcourt de manière récursive. Pour éviter les boucles, on a une liste qui contient tous les arrêts par lesquels on a déjà essayé de passer (à ce niveau de récursivité ou même plusieurs déplacements auparavant). Cela fonctionne car les arc sont triés par ordre croissant de leurs horaires, donc inutile d’essayer un chemin si on l’a déjà essayé à une heure plus tôt). 





