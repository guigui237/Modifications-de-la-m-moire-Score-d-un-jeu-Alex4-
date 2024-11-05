# Modifications-de-la-m-moire-Score-d-un-jeu-Alex4-
Ce projet illustre comment utiliser des outils de manipulation de mémoire pour modifier des valeurs dans un jeu (Alex4) en cours d'exécution. Les étapes suivantes ont été suivies pour changer le score du jeu appelé "Alex4".

Outils utilisés

    Scanmem : Un outil en ligne de commande pour rechercher et modifier des valeurs en mémoire.
    GameConqueror : Une interface graphique pour scanmem qui simplifie la recherche et la modification des valeurs en mémoire.
    GDB : Un débogueur qui peut être utilisé pour inspecter et modifier la mémoire d'un programme en cours d'exécution.
    
  # Bash 
  sudo apt install scanmem gameconqueror
  sudo apt install gbd

Étapes de la procédure

Scan des PID 

![image](https://github.com/user-attachments/assets/312c30ad-31c8-4ca8-8ca5-ee731c30a7e5)

Lancement de Scanmem :
        On execute scanmem en tant que super utilisateur pour accéder aux régions de mémoire du processus.
Attachement à un processus :
        Utilisation de la commande pid <PID> pour attacher à l'exécutable du jeu (dans ce cas, le PID est 109615).

![image](https://github.com/user-attachments/assets/94c240a8-c3bb-4f90-bf42-a7a2f0f9bc39)

Recherche de la valeur :
        On identifie la valeur qu'on souhaite modifier (dans notre cas, le score actuel du jeu 340) et on entre cette valeur dans scanmem.
        
![image](https://github.com/user-attachments/assets/22d6b964-efec-4bd2-a70a-007f41af3052)

il retouve 23 match, on va jouer pour augmenter le score et on va retaper une autre valeur afin de voir la valeur de l'adresse qui a changé : 

![image](https://github.com/user-attachments/assets/cefdb4ca-3902-4f77-99a1-1d1626563ca5)

Ici on retrouve un seul et unique match, on fait list pout le visualiser et on a obtenu dans notre cas comme vous pouvez le voir dans l'image: 0x580160531c48


Modification de la valeur :
        Une fois que la valeur est trouvée, on peux la modifier directement dans grace à GDB.
    On lance gdb avec li PID associé :
![image](https://github.com/user-attachments/assets/877bfddb-2a9d-41fa-8992-98f163b2c4fe)

On modifie ensuite la valeur de l'adresse associé avec la commande : 

    # Bash 
    (gdb) set *(int*)0x580160531c48 = 340
    detach

![image](https://github.com/user-attachments/assets/a072b1b7-7357-458f-bcdf-f64a99e55e8b)

On remarque le changement du score à 5900 qui est la valeur entrée. 
La valeur a été correctement modifiée, l'opération est réussi !!! 

Conclusion

Ce projet démontre comment les outils de manipulation de mémoire, tels que Scanmem et GameConqueror, peuvent être utilisés pour modifier des valeurs dans un jeu en cours d'exécution. En utilisant ces techniques, nous avons pu manipuler avec succès le score du jeu "Alex4", ce qui met en évidence les possibilités et les implications de la rétro-ingénierie logicielle.

Il est important de noter qu'on pouvais modifier n'importe quelle variable du jeu en utilisant la même méthode.
    
Les étapes de recherche et de modification de la mémoire ont révélé non seulement la flexibilité de ces outils, mais aussi l'importance de comprendre comment les applications gèrent la mémoire. Ce type de connaissance peut être précieux dans le cadre de la sécurité informatique, où la compréhension des vulnérabilités des logiciels et des méthodes d'exploitation est essentielle.

Ce projet ouvre également la voie à d'autres explorations, comme la recherche de vulnérabilités dans d'autres applications et le développement d'outils personnalisés pour automatiser ces tâches. Les résultats obtenus montrent que, bien que ces techniques puissent être utilisées à des fins ludiques, elles soulèvent également des questions éthiques et légales qui doivent être prises en compte par les développeurs et les chercheurs.
