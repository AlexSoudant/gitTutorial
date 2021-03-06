####################################
####################################

# gitTutorial by Alex Soudant

# Ce tutorial propose les bases pour créer un repertoire git en local puis mettre à jour un repertoire github qui lui sera lié. 
# On abordera également comment faire une pull request depuis un repertoire forké.
# Les commandes de la console seront présentées sous Linux puis sous Windows.

####################################
####################################

# Avoir git d'installé (souvent il est installé par défaut)

# Configurer votre email et identité sous git
# ces informations seront attachées aux modifications que vous ferez à vos fichiers
# ce qui permet à plusieurs utilisateurs de voir qui a modifié les fichiers
# le mieux est de remettre email et nom d'utilisateur que vous avez configurez sous github
 
git config --global user.email "you@example.com"
git config --global user.name "Your Name"

# Allez à l'emplacement du repertoire que vous voulez créer

# LINUX
> cd /home/user/Documents

# Windows
> CD C:\Documents\

# Créer le repertoire (soit par ligne de commande soit manuellement en clic droit)

# LINUX
> mkdir monRepo

# Windows
> MKDIR monRepo

# Changez le chemin de votre console pour être à l'intérieur du repertoire créé

# LINUX
> cd /home/user/Documents/monRepo

# Windows
> CD C:\Documents\monRepo

####################################

# A partir de là, les commandes seront des commandes de git, donc pas de differences entre les OS!

# On initie un nouveau repertoire git qui va tracker TOUS les changements fait à l'intérieur de ce repertoire
> git init

# On peut à présent mettre des fichiers dans ce repertoire (copy/paste ou création de nouveaux fichiers sont possible)
# j'ai ajouté quatre fichiers : hello.py fichier1.txt fichier2.txt fichier3.txt

# J'indique à git que je ne veux enregistrer que les changements réalisés sur hello.py et fichier1.txt
> git add hello.py fichier1.txt 

# On peut voir que git va les trouver avec la commande:
> git status

#resultat:

#########################
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   fichier1.txt
	new file:   hello.py

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.hello.py.swp
	fichier2.txt
	fichier3.txt
	hello.py~
########################

# On voit que fichier2.txt et fichier3.txt sont dans la catégorie 'Untracked files' et ne seront pas pris en charge par git

# En revanche fichier1.txt et hello.py sont dans la catégorie 'Changes to be commited' et sont donc suivis par git

# Maintenant il faut dire à git que nous validons la création de ces fichiers (ou des modifications faites dans ces fichiers) par un 'commit'
> git commit -m "j'ai ajoute deux fichiers!"

# le message lié au commit permet pour vous et les autres utilisateurs de garder une trace des modifications effectuées

#resultat:

#########################
[master (root-commit) 4936cdc] add a lot of crapp!
 2 files changed, 2 insertions(+)
 create mode 100644 fichier1.txt
 create mode 100644 hello.py
#########################

# ces commits sont enregistrés dans un journal sous la commande 'log'
>  git log

#resultat:

#########################
commit 4936cdcdc92d50ccb97339a98b377c7b2a0dc68a
Author: asoudant <asoudant@homail.fr>
Date:   Thu Dec 8 15:10:40 2016 +0100
#########################

# On peut maintenant s'interesse aux branches d'un repertoire git.
# Une branche permet de garder une copie du repertoire principal (nommé master) et de faire des modifications qui ne seront
# enregistrées QUE sur cette branche. On peut donc faire des betises sans que cela n'affecte le travail fait avant.

# la commande git branch vous affiche vos branches (dans notre cas seul master est présent)
> git branch

#resultat:

#########################
* master
#########################

# Nous allons donc ajouter une branche supplémentaire
> git branch say-goodbye

# Nous la voyons a présent dans nos branches mais l'astérisque * indique que nous travaillons toujours sous master
> git branch

#resultat:

#########################
* master
  say-goodbye
#########################

# Nous allons indiquer que nous travaillons sur cette branche ci:
> git checkout say-goodbye

#resultat:

#########################
Switched to branch 'say-goodbye' 
#########################

# On va maintenant créer la connexion entre votre répertoire en local et sur github
# Pour cela, allez sous github, et créez un nouveau repertoire (bouton New dans l'onglet Repositories de votre profil)
# et copiez l'adresse qui est proposée dans le bouton vert 'Clone ou Download' une fois que le repertoire créé

> git remote add origin https://github.com/AlexSoudant/git-tuto.git

# On peut maintenant uploader nos fichiers sur github par la commande 'push'
> git push -u origin master
# On précise ici que l'on souhaite upload uniquement la branche master

# Git va vous demander de rentrer vos identifiants github:

Username for 'https://github.com': AlexSoudant
Password for 'https://AlexSoudant@github.com':

#resultat:

######################### 
Counting objects: 7, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (7/7), 486 bytes | 0 bytes/s, done.
Total 7 (delta 1), reused 0 (delta 0)
To https://github.com/AlexSoudant/git-tuto.git
 * [new branch]      master -> master
######################### 

# On peut également penser qu'un autre utilisateur ait modifié le repertoire github et donc vous souhaitez downloader
# ces modifications en local:
> git pull origin master

###########################################################

# Pour les repertoires forkés, on créé donc une copie d'un repertoire github vers un autre repertoire github
# On ne peut donc effectuer des modifications que sur notre copie github et notre copie locale mais non sur le repertoire d'origine

# il faut donc faire une 'new pull request' qui s'affiche sur la page du repertoire github 
# Github va comparer votre version avec la version d'origine
# vous pouvez également inverser le sens de la relation votreRepo -> sonRepo par votreRepo <- sonRepo
# en cliquant sur 'Try switching base'

# Vous aurez ensuite à cliquer sur 'Create pull request' et renseigner les boites d'écriture pour vos modifications apportées
# puis à nouveau cliquer sur 'Create pull request'

# si vous etes dans le sens votreRepo <- sonRepo vous pouvez cliquer sur 'Merge pull request' pour accceter les modifications
# sinon dans le sens votreRepo -> sonRepo vous n'avez plus qu'a attendre que la personne en charge du repertoire d'origine accepte 
# vos modifications.

###########################################################

Pour vous entrainez: 

- Créez un repertoire local
- Forkez mon repertoire github vers votre github
- faites le lien entre le repertoire local et votre repertoire github
- Ajoutez des modifications en local
- Pushez sur votre repertoire github
- Faites une pull request pour que j'accepte votre modification

Ajoutez moi un petit chat dans ce fichier pour prouver que vous avez suivi!

    /\__/\
   /`    '\
 === 0  0 ===
   \  --  /
  /        \
 /          \
|            |
 \  ||  ||  /
  \_oo__oo_/#######o Bon courage! 
