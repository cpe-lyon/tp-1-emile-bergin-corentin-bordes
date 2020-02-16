# Compte rendu du TP 1 :


## Manuel :

1. A l’aide du manuel, identifiez le rôle de la commande which.

	 *commande : man which

2. Quand on consulte une page du manuel, comment peut-on rechercher un 	terme (par exemple, chercher le terme option dans la page de manuel de which ?

	 *1ére solution : man | grep option

	 *2ème solution : man which -f option
	 
	 *3ème solution : une fois dans le manuel, taper ! ou * option
	 
3.  Comment quitte-t-on le manuel ?

	 * commande : q
	 
4. Chaque section du manuel a une première page, qui présente le contenu de la section. Afficher la première page de la section 6 ; de quoi parle cette section ?

	 * commande : man 6 which, cette page n'a pas de contenu.
	 
## Navigation dans l’arborescence des fichiers :

1. allez dans le dossier /var/log

	 * commande : cd /var/log
	 
2. remontez dans le dossier parent (/var) en utilisant un chemin relatif

	 * commande : cd ..
	 
3. retournez dans le dossier personnel

	 * relatif : cd ../home/vmbb
	 
	 * absolu : cd /home/vmbb
	 
	 * commande  : cd ~
	 
4. revenez au dossier précédent *(/var)* __sans utiliser de chemin__

	 * commande : cd -
	 
5. essayez d’accéder au dossier */root* ; que se passe-t-il ?

	 * la permission ne nous est pas accordée.
	 
6. essayez la commande *sudo cd /root* ; que se passe-t-il ? Expliquez

	 * Premièrement, cd étant une commande et non un programme, sudo ne peut pas l'exécuter
	 
	 * Deuxièmement, une fois la commande effectuée en mode root grâce a sudo, nous nous retrouvons dans un document ou nous n'avons pas le droit de nous trouver, la commande ne s'éxécute donc pas.
	 
7. à partir de votre dossier personnel, créez l’arborescence suivante :
	 
	 * cd /home/vmbb
	 * mkdir Dossier1
	 * mkdir Dossier2
	 * cd Dossier1
	 * echo "" >> Fichier1
	 * cd ../Dossier2
	 * mkdir Dossier2.1
	 * mkdir Dossier2.2
	 * cd Dossier2.2
	 * echo "" >> Fichier2 
	 * echo "" >> Fichier3

8. revenez dans votre dossier personnel ; à l’aide de la commande rm, essayez de supprimer Fichier1, puis Dossier1 ; que se passe-t-il ?

	 * Cannot remove "Dossier1" : Is a directory
	   Cette commande sert a supprimer les fichiers et non les répertoires.
	   
9. quelle commande permet de supprimer un dossier ?

	 * commande : rm -d permet de supprimer un répertoire.
	 
10. que se passe-t-il quand on applique cette commande à Dossier2

	 * Cela ne fonctionne pas
	 
11. comment supprimer en une seule commande Dossier2 et son contenu ?

	 * commande : rm -r pour la récursivité et donc supprimer les documents dans Dossier2.
	 
	 
## Commandes importantes :

1. Quelle commande permet d’afficher l’heure ? A quoi sert la commande __time__ ?

	 * Cette commande donne trois informations relatives au temps d'exécution d'un programme : temps d'exécution réel, temps d'exécution système, et temps d'attente système.
	 
2. Dans votre dossier personnel, tapez successivement les commandes ls puis la ; que peut-on en déduire sur les fichiers commençant par un point ?

	 * Les fichiers commençant par un _"."_ sont des fichiers cachés.
	 la est un alias de ls -a
	 
3.  Où se situe le programme ls ?

	 * commande : which ls, ls est situé dans /usr/bin/ls
	 
4. Essayez la commande _ll_. Existe-t-il une entrée de manuel pour cette commande ? Utilisez les commandes _alias_ ou _alias_ pour en savoir plus sur la nature de cette commande.

	 * il n'existe pas d'entrée de manuel car _ll_ est un alias. en tapant : _alias_ on se rend compte que ll représente : ls -alF
	 
5. Quelle commande permet d’afficher les fichiers contenus dans le dossier _/bin_ ?

	 * commande : ls /bin
	 
6. Que fait la commande _ls .._ ?

	 * elle fait l'effet de la commande cd .. concaténée avec ls (affiche le contenu du dossier parent)

7. Quelle commande donne le chemin complet du dossier courant ?

	 * commande : pwd

8. Que fait la commande echo 'yo' > plop exécutée 2 fois ?

	 * elle écrit __"yo"__ dans le fichier plop une première fois puis écrase le premier __"yo"__

9. Que fait la commande echo 'yo' >> plop exécutée 2 fois ?

 	 * elle écrit __"yo"__ deux fois dans le même fichier plop

10. A quoi sert la commande file ? Essayez la sur des fichiers de types différents.

	 * la commande file [fichier] détermine le type du fichier.

11. Créez un fichier toto qui contient la chaîne Hello Toto ! ; créer ensuite un lien titi vers ce fichier avec la commande ln toto titi. Modifiez à présent le contenu de toto et affichez le contenu de titi : qu’observe-t-on ? Supprimez le fichier toto ; quelle conséquence cela a-t-il sur titi ?

	 * echo "Hello Toto !" > toto
	 * ln toto titi
	 * echo "Good Bye Toto !" > toto
	 * more titi
	 * Le fichier titi est modifié lui aussi, étant un __lien__
	 * rm toto
	 * Le fichier titi n'est pas modifié

12. Créez à présent un lien symbolique tutu sur titi avec la commande ln -s titi tutu. Modifiez le contenu de titi ; quelle conséquence pour tutu ? Et inversement ? Supprimez le fichier titi ; quelle conséquence cela a-t-il sur tutu ?

	 * ln -s titi tutu
	 * echo "yo" > tutu
	 * more titi
	 * echo "yop" > titi
	 * more tutu
	 * rm titi 
	 * Le lien fait que tutu n'est plus accessible après que titi soit suppprimé.

13. Affichez à l’écran le fichier /var/log/syslog. Quels raccourcis clavier permettent d’interrompre et reprendre le défilement à l’écran ?

	 * CTRL +S permet d'arreter le défilement, tandis que CTRL +L permet de reprendre.

14. Affichez les 5 premières lignes du fichier /var/log/syslog, puis les 15 dernières, puis seulement les
lignes 10 à 20.

	 * 5 premières lignes : head -n 5 var/log/syslog
	 * 15 dernières lignes : tail -n var/log/syslog
	 * lignes 10 à 20 : head -n 20 var/log/syslog | tail -n 10 

15. Que fait la commande dmesg | less ?

	 * Affiche dmesg à la manière de less, c'est à dire page par page

16. Affichez à l’écran le fichier /etc/passwd ; que contient-il ? Quelle commande permet d’afficher la page de manuel de ce fichier ?

	 * passwd contient les différents mot de passe, la commande est man 5 passwd

17. Affichez seulement la première colonne triée par ordre alphabétique inverse

	 * sort -r /etc/passwd

18. Quelle commande nous donne le nombre d’utilisateurs ayant un compte sur cette machine (pas seulement les utilisateurs connectés) ?

	 * commande : wc -l /etc/passwd
	 * commande : compgen -u 

19. Combien de pages de manuel comportent le mot-clé conversion dans leur description ?

	 * commande : man -f conversion | wc
	 * Il y a donc 4 pages.

20. A l’aide de la commande find, recherchez tous les fichiers se nommant passwd présents sur la machine

	 * commande : sudo find / -name "passwd" | wc

21. Modifiez la commande précédente pour que la liste des fichiers trouvés soit enregistrée dans le fichier ~/list_passwd_files.txt et que les erreurs soient redirigées vers le fichier spécial /dev/null

	 * commande : sudo find / -name "passwd" > ~/list_passwd_files.txt  2> /dev/null

22. Dans votre dossier personnel, utilisez la commande grep pour chercher où est défini l’alias ll vu précédemment

	 * commande : grep -r "ll="

23. Utilisez la commande locate pour trouver le fichier history.log.

	 * Une fois la commande installée, commande : locate history.log

24. Créer un fichier dans votre dossier personnel puis utilisez locate pour le trouver. Apparaît-il ? Pourquoi ?

	 * Il n'apparait pas car il ne s'est pas encore inscrit dans la database. Il faut donc la raffraichir avec updagedb.

