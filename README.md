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

    Lancement de Scanmem :
        Exécutez scanmem en tant que super utilisateur pour accéder aux régions de mémoire du processus.

    Attacher à un processus :
        Utilisez la commande pid <PID> pour attacher à l'exécutable du jeu (dans ce cas, le PID est 109615).

![image](https://github.com/user-attachments/assets/94c240a8-c3bb-4f90-bf42-a7a2f0f9bc39)

    Recherche de la valeur :
        On identifie la valeur que vous souhaitez modifier (dans ce cas, le score actuel du jeu 340) et on entre cette valeur dans scanmem.
        
![image](https://github.com/user-attachments/assets/22d6b964-efec-4bd2-a70a-007f41af3052)

il retouve 23 match, on va jouer pour augmenter le score et on va retaper une autre valeur afin de voir la valeur de l'adresse qui a changé : 

![image](https://github.com/user-attachments/assets/cefdb4ca-3902-4f77-99a1-1d1626563ca5)

Ici on retrouve un seul et unique match, on fait list pout le visualiser et on a obtenu dans notre cas comme vous pouvez le voir dans l'image: 0x580160531c48


    Modification de la valeur :
        Une fois que la valeur est trouvée, on peux la modifier directement dans grace à GDB.
    On lance gdb avec li PID associé :
![image](https://github.com/user-attachments/assets/4897c039-2d95-4a70-9103-0eaf2e3871da)


    Vérification des modifications :
        Lancez le jeu et vérifiez que la valeur a été correctement modifiée.

Résultats

Des captures d'écran du processus, y compris les commandes utilisées et le résultat final dans le jeu, seront ajoutées pour illustrer les étapes ci-dessus.
