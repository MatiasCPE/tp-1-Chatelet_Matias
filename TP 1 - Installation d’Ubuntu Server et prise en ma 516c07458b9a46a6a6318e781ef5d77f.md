# TP 1 - Installation d’Ubuntu Server et prise en main du shell

# Exercice 2:

## Manuel

1. La commande `WHICH` permet de localiser un fichier comme l’indique le manuel avec `man which` , elle prend en paramètre un nom de fichier 
    
    `wich nom_de_fichier`
    
2. On peut rechercher un terme dans une page manuel en faisant `/"terme"`
3. On peut quitter une page manuel en tapant `q`
4. On peut afficher la première page de la section 6 avec la commande `man 6 intro`
    
    Cette section parle de jeux
    

## Navigation dans l’arborescence des fichiers

1. Déplacement dans le dossier /var/log avec `cd /var/log`
2. Déplacement dans le dossier /var avec le chemin relatif `cd ../`
3. Retour dans le dossier personnel avec `cd`
4. Pour retournez dans `/var` sans chemin il faut utiliser `cd -`
5. Accès au dossier `/root` avec `cd /root`,l’accès est refusé.
6. Lorsque l’on tape la commande `sudo cd /root`, cela nous renvoie une erreur en nous disant que la commande cd est une commande 
7. On peut créer des dossiers avec la commande `mkdir “nom_dossier”`
    
    Pour les fichiers il suffit d’utiliser `touch “nom_fichier”`
    
8. On peut supprimer le fichier `“Fichier1”` avec `rm Dossier1/Fichier1`
    
    Pour le dossier “Dossier1” on utilise `rm Dossier1` cependant cela ne marche pas car c’est un dossier
    
9. Pour supprimer un dossier il faut utiliser `rmdir “nom_dossier”`
10. Cette commande ne marche pas sur le dossier “Dossier2” car le dossier n’est pas vide
11. Pour supprimer le dossier dossier “Dossier2” et ses fichiers il faut utiliser la commande
    
     `rm -r Dossier 2`
    

### Commandes importantes

1. Pour afficher l’heure il suffit d’utiliser la commande `date`, la commande `time`
utilisée pour exécuter une commande et imprime un résumé du temps réel, du temps CPU de l’utilisateur et du temps CPU du système
2. Les fichiers commençant par un `.` sont des fichiers cachés pour les afficher, il suffit d’utiliser `la` ou `ls -a`
3. `ls` se trouve dans `/usr/bin/ls` comme l’indique la commande `which ls`
4. `ll` est un alias de la commande `ls -l`, elle permet d’afficher les fichiers avec un nom d’affichage long et donc obtenir plus d’information sur les fichiers
5. `ls /bin` permet d’afficher tous les fichiers contenus dans le dossier `/bin`

 6. `ls ..` permet d’afficher tous les fichiers du dossier parents.

1. `pwd` donne le chemin complet du dossier courant
2. La commande `echo 'bip' > plop` exécutée 2 fois, créer le fichier “plop” écrit une première fois le mot ‘bip’ dans le fichier “plop”, puis lors de la deuxième exécution, elle écrase le contenu de “plop” pour y écrire de nouveau ‘bip’
3. La commande `echo 'bip' >> plop` exécutée deux fois, ajoute à la fin du fichier “plop” ‘bip’ sans écraser le contenu d’avant.
4. La commande `sleep 10 | echo 'toto’` va afficher ‘toto’ dans le terminal puis endormir le processus pendant 10 secondes.
5. La commande `file` permet de déterminer le type d’un fichier.
6. On crée le fichier “original” qui contient ‘Hello Toto !’ avec la commande `echo 'Hello Toto !' > original`. On crée un lien vers le fichier “original” qu’on appelle “lien_phy” avec la commande `ln original lien_phy`. Lorsque qu’on modifie “original”, “lien_phy” sera aussi modifier. Cependant, si on supprime “original”, “lien_phy” ne sera pas supprimer.
7. On crée à présent un lien symbolique “lien_sym” sur “lien_phy” avec la commande `ln -s lien_phy lien_sym`. Quand on modifie un l’autre sera également modifier. Si on supprime “lien_phy”, “lien_sym” sera également supprimé.
8. Le raccourci `Ctrl + s` permet d’interrompre le défilement d’un fichier trop volumineux et `Ctrl + q` permet de reprendre le défilement.
9. La commande **`head -5 /var/log/syslog`** pour afficher les 5 premières lignes et **`tail -15 /var/log/syslog`** pour afficher les 15 dernières lignes et enfin un mélange des deux pour afficher les lignes de 10 à 20 **`tail -0 /var/log/syslog | head -20 /var/log/syslog`.**
10. La commande **`dmesg |less`** permet d'afficher le contenu du buffer du noyau
11. On peut afficher le contenu du fichier avec la commande `cat /etc/passwd` contient les noms d'utilisateurs, les mots de passes cryptés et le numéro d'identification d'utilisateur. Pour afficher la page man, il suffit de taper la commande `man passwd` .
12. La commande `sudo awk < /etc/passwd -F: '{ print $1 | "sort -r"}’` permet d'afficher seulement la première colonne triée par ordre alphabétique inverse. 
13. La commande `wc -l passwd` affiche le nombre de lignes du ficher `passwd` donc le nombre d’utilisateurs.
14. La commande **`m**an -k conversion | wc -l` permet d’afficher le nombre de pages man contenant le mot conversion dans leur section description.
15. La commande `find / -name 'passwd'` permet d’afficher tous les fichiers se nommant `passwd`
16. La commande `find / -name passwd 1> ~/list_passwd_files.txt 2> /dev/null` permet d’enregistrer la liste dans le fichier l`ist_passwd_files.txt` et de rediriger les erreurs vers le fichier spécial `/dev/null`
17. La commande `grep -r "alias ll"`  permet de chercher où est défini l’alias ll vu
précédemment.
18. La commande `locate history.log` permet de trouver le fichier history.log
19. J’utilise `touch text.txt` pour créer un fichier. Cependant, la commande `locate` ne permet pas de le trouver, car il n’est encore pas indexé à la base de données.

# Exercice 3 :

1. `cp /var/log/syslog log.txt` permet de copier le fichier sous le nom log.txt, puis `nano log.txt` pour l’ouvrir avec l’éditeur nano
2. On utilise Ctrl + W, *Ctrl + R*, chercher le mot kernel + *Entrée*, mettre le mot noyau + *Entrée*, A pour remplacer toutes les occurrences.
3. On sélectionne les 10 premières lignes avec *Maj.Gauche* + *Flèche du bas*, puis *Ctrl + K* pour couper ces lignes et ensuite, on va à la fin du fichier puis fait *Ctrl + U* pour coller le résultat.
4. Pour annuler cette action, il faut utiliser *Alt + U*.
5. Pour quitter et enregistrer le fichier, il faut utiliser *Ctrl + S* et ensuite *Ctrl + X .*

# Exercice 4 :

1. On crée une copie du fichier `~/.bashrc` avec `cp ~/.bashrc .bashrc_bak` 
2. Il faut décommenter la ligne « **force_color_prompt=yes** » puis enregistrer et quittez le fichier nano avec *Ctrl + X* et ensuite *Y*.
3. Personnalisation :

![prompt.png](TP%201%20-%20Installation%20d%E2%80%99Ubuntu%20Server%20et%20prise%20en%20ma%20516c07458b9a46a6a6318e781ef5d77f/prompt.png)