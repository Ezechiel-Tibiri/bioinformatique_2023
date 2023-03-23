# Cours bioinformatique session 2023
Bienvenue au cours d'introduction à la Bioinformatique. Vous trouverez sur ce dépôt toutes les informations et ressources nécessaires. A noter que la présence physique à ce cours est plus que nécessaire voir obligatoire.

## Intervenants
* Ezechiel B. TIBIRI, INERA/CNRST, ezechiel.tibiri@ujkz.bf (responsable)
* Fidèle TIENDREBEOGO, INERA/CNRST, fidele.tiendrebeogo@wave-center.org (co-responsable)

## Prérequis
Dans un premier temps, nous vous suggérons d'apprendre les bases du dogme central de la biologie moléculaire, et de la génomique et séquençage d'ADN.

*Temps estimé : 4 heures.

Ensuite, nous vous demandons de lire le [cours en ligne](https://github.com/Ezechiel-Tibiri/bioinformatique_2023/blob/main/Cours_bioinfo_2023.pdf) qui sera mis à jour au fure et à mésure que le cours progresse.

*Temps estimé : 8 heures.


# Introduction à la programmation en bioinformatique

La programmation est devenue un élément indispensable dans le domaine de la bioinformatique pour l'analyse et la gestion des données biologiques. Dans ce cours, nous allons voir comment installer l'environnement de développement pour la programmation en bioinformatique sur Windows en utilisant Ubuntu 22.04 LTS ou Cygwin.

## 1. Intaller UBUNTU 22.04 LTS sous Windows 10+
### 1.1. Installez Bash pour Windows en suivant les instructions

La première étape consiste à installer Bash pour Windows. Vous pouvez le faire en suivant les instructions fournies dans les liens suivants :

* Pour Windows 10. Vous pouvez installer très rapidement un shell Linux. Voici quelques liens pour y arriver :
  * [Installer le shell Bash Linux sous Windows 10 avec WSL](https://www.youtube.com/watch?v=CyG16N3GJWo), 2020.
  * How to install Windows Subsystem for Linux (WSL) on Windows 10, 2019.
  * [Everything You Can Do With Windows 10’s New Bash Shell](https://www.howtogeek.com/265900/everything-you-can-do-with-windows-10s-new-bash-shell/), 2018.
  Ensuite, vous pouvez ouvrir Bash et exécuter la commande suivante pour mettre à jour et installer les packages Python nécessaires :
  
 ```
 sudo apt update && sudo apt upgrade -y
sudo apt install python3 python3-pip python3-dev python3-setuptools

 ```

### 1.2. Installation de Jupyter Notebook

Pour installer Jupyter Notebook, vous pouvez exécuter la commande suivante dans Bash :

```bash
sudo pip3 install jupyter
```
### 1.3. Vérification de l'installation

our vérifier que Jupyter Notebook a été installé avec succès, vous pouvez exécuter la commande suivante dans Bash :
```bash
jupyter notebook
```
### 1.4.  Installation du kernel bash

Enfin, vous pouvez installer le kernel bash en exécutant les commandes suivantes 

```bash
pip install bash_kernel
python3 -m pip install --upgrade pip
python3 -m pip install bash_kernel
```

```bash
jupyter notebook
```

## 2. Installation de Cygwin sous Windows
Si vous n'avez pas pu installer UBUNTU sous Windows, vous pouvez installer Cygwin pour exécuter les commandes Unix. Pour installer Cygwin, vous pouvez suivre les étapes suivantes :

2.1. Téléchargement et installation de Cygwin :

Téléchargez le fichier d'installation de Cygwin depuis le site web officiel de Cygwin à l'adresse https://cygwin.com/install.html. Double-cliquez sur le fichier d'installation pour lancer l'assistant d'installation. Choisissez un répertoire d'installation pour Cygwin. Par défaut, il est installé dans C:\cygwin. Choisissez un serveur de miroir Cygwin pour télécharger les paquets. Il est recommandé de choisir un serveur proche de votre emplacement géographique. Sélectionnez les paquets à installer en utilisant le bouton "Sélectionner les paquets" dans l'assistant d'installation. Il est recommandé de sélectionner les paquets de base, tels que `bash`, `gcc`, `make` et `openssh`. Cliquez sur le bouton "Installer".

## Les commandes de base de LINUX

### 1.1. Les commandes de gestion des répertoires et des fichiers
Dans le cadre de la bioinformatique, la maîtrise des commandes de base de Linux est cruciale pour effectuer des tâches courantes telles que la gestion de fichiers et de répertoires. Voici une liste des commandes les plus couramment utilisées

* `pwd` (affiche le chemin absolu du répertoire courant)
* `ls` (list, affiche les répertoires et les fichiers du répertoire actif)
* `ls` (affiche seulement les noms)
* `ls toto*` (affiche les fichiers commençant par toto)
* `ls -l` (affiche le format long : types + droits + Nbre de liens + ....)
* `cd` (change directory)
* `mkdir -p` (créer un répertoire)
* `touch` (créer un fichier vide, crée un fichier ou actualise la date de dernière modification)
* `cp` chemin (vers le répertoire dont le chemin absolu est donné)
* `cp` (copy)
* `cp -r` (copie permet de copier un repertoire)
* `mv` (move, renomme et déplace un fichier ou un repertoire)
* `rm` (remove, éfface!!!)
* `rm -R` (permet de suprimer un repertoir)

### 1.2. Les commandes d'édition

En plus des commandes de gestion de fichiers et de répertoires, il existe également des commandes d'édition de fichiers dans l'environnement de ligne de commande LINUX. Les commandes d'édition peuvent être utiles pour visualiser le contenu d'un fichier, rechercher des chaînes de caractères spécifiques dans un fichier, et même éditer des fichiers directement dans l'environnement de ligne de commande. Voici quelques-unes des commandes d'édition de fichiers les plus courantes

* `more` : Cette commande est utilisée pour afficher le contenu d'un fichier page par page sans possibilité de retour en arrière.
* `cat` : Cette commande permet d'afficher tout le contenu d'un fichier.
* `less` : Cette commande affiche le contenu d'un fichier page par page avec défilement arrière. En tapant la lettre "h", l'utilisateur peut accéder à l'aide contextuelle.
* `head` : Cette commande affiche les 10 premières lignes d'un fichier. L'utilisateur peut spécifier un nombre différent de lignes à afficher en utilisant l'option "-n".
* `tail` : Cette commande affiche les 10 dernières lignes d'un fichier. L'utilisateur peut également spécifier le nombre de lignes à afficher avec l'option "-n".
* `nano` : Cette commande permet d'éditer rapidement et facilement des fichiers texte dans l'environnement de ligne de commande.
* `gedit` : Cette commande permet d'éditer graphiquement un fichier.
* `grep` : Cette commande permet de rechercher une chaîne de caractères spécifique dans un fichier.
* `echo` : Cette commande répète simplement ce que l'utilisateur lui demande de répéter.

### 1.3. Les autres commandes

* `cal` (Affiche le calendrier)
* `date` (affiche la date, le mois, l'heure et l'année du jour. Les messages d'erreur et les e-mails sont toujours datés avec la date système)
* `wc` ("word & count", affiche le nombre de lignes + mots + caractères)
* `grep ` (cherche la chaîne de caractères **expression** à l'intérieur des fichiers ou des répertoires spécifiés et affiche les lignes correspondantes.)
* `spell` (programme de correction orthographique)ls
* `cat rapport.txt | spell > faute.txt`
* `read` (lit dans un script shell la ligne saisie à partir de l'entrée par défaut, le clavier)

## 2. Quelques commandes de l'administrateur
### 2.1. Les commandes de gestion des utilisateurs
* `w`(affiche les informations de connexion de l'utilisateur)
* `who`(affiche la liste des utilisateurs connectés)
* `whoami`(indique le "logon" de l'utilisateur)
* `id` (identité de l'utilisateur actif, UID, GID)
* `finger` (affiche des informations sur les utilisateurs)
* `adduser` (ajouter un compte utilisateur, les UID des utilisateurs commencent à partir du numéro 500)
* `useradd` (ajouter un compte utilisateur)
* `userdel` (supprimer un compte utilisateur)
* `usermod` (modifier les informations d'un compte utilisateur)

### 2.2. Modification des droits d'accès

Pour vérifier les propriétaires et les permissions actuelles d'un fichier, on peut utiliser la commande `ls -l`. Par exemple, pour afficher les informations sur le dossier `/home/ezechiel/bioinfo/exo1/` et le fichier tata.txt, on peut utiliser la commande suivante :

```
ls -l /home/ezechiel/bioinfo/exo1/
```
Cela va afficher les informations suivantes :

```diff
drwxrwxr-x 2 ezechiel ezechiel 4096 mars   3 11:54 exo4
-rw-rw-r-- 1 ezechiel ezechiel    0 mars   3 11:26 tata.txt
```
Dans cet exemple, "ezechiel" est le propriétaire actuel du fichier et les permissions sont "rwxrwxr-x". La signification des différentes lettres est la suivante :

   * <span style="color:red">**r**</span>: permission de lire
   * <span style="color:red">**w**</span>: premission d'ecrire et de suprimer
   * <span style="color:red">**x**</span>: permission d'execution
 

### 2.3. Quelques commande système

La gestion des paquets est une tâche importante pour les biologistes travaillant avec des outils informatiques. La commande `apt` ou `apt-get` est un outil couramment utilisé pour installer, mettre à jour et supprimer des paquets dans un système d'exploitation Ubuntu ou Debian. Cette commande prend en compte les dépendances, et peut télécharger les paquets nécessaires depuis une source réseau.

Les commandes les plus fréquentes sont `update`, qui met à jour la liste des paquets disponibles, `upgrade`, qui met à jour tous les paquets déjà installés, et `install` qui permet d'installer un ou plusieurs paquets. Il est également possible de supprimer des paquets avec la commande `remove`, et d'effacer les installateurs avec la commande `clean`.

Les options les plus courantes sont `-f`, qui permet de réparer un système dont les dépendances sont défectueuses, `-s` qui simule les actions à mener sans rien toucher au système, `-y` qui répond automatiquement oui à toutes les questions, et `-u` qui affiche les paquets mis à jour ou encore `--purge` pour supprimer tous les fichiers de configuration associés à un paquet.  
Il est important de noter que l'utilisation de la commande `sudo` est souvent nécessaire pour exécuter les commandes `apt` en tant qu'utilisateur super-utilisateur, car les modifications apportées par ces commandes peuvent avoir un impact significatif sur le système.

Exemples d'utilisation :
* `sudo apt update` (Met à jour la liste des paquets disponibles).
* `sudo apt upgrade` (Met à jour tous les paquets ​installés).
* `sudo apt install nom_paquet` (pour installer un paquets) 

## 3. Les opérateurs de redirection des Entrées/Sorties

La redirection de la sortie standard (l'écran) vers un fichier permet de consulter le résultat ultérieurement et de le conserver. La redirection de l'entrée standard (le clavier) est moins usitée .La redirection entre processus  (entre commande ou entre programme avec le tube ou le pipe) permet de créer des "pipelines", c'est à dire une seule ligne de commande constituée d'une succession de commandes avec la sortie de chacune redirigée vers l'entrée de la suivante.

* `|`(pipe **AltGr+6**, **Alt+6...**)
* `commande1 | commande2`
* ` grep "chaîne" [fichier] | wc -l`
* `>` redirection de la sortie standard, le fichier de destination écrase le précédent
* `commande > sortie`
* `echo "chaîne > fichier.txt`
* `commande 2> erreurs.txt` (redirige les erreurs de syntaxe, le flux "stden" vers un fichier)
* `commande < entrée> sortie`
* `<`(redirection de l'entré standard)
* `commande < fichier d'entrée`
* `>>`(redirection et concaténation en fin de fichier)
* `cat fichier1 fichier2 >> ensemble`

## 4. Les commandes d'archivage et de compression
* `tar`(tape archive ressource, pour archiver ou restaurer des "tar file" avec l'extension "**.tar**")
* `tar -cvf cible source` (archive la "source" dans la "cible")
* `tar -xvf archive.tar` (restaure le fichier "archive.tar" dans le répertoire courant)
* `tar -xvf archive.tar /tmp` (restaure le fichier "archive.tar" dans le répertoire "**/tmp**")
* `tar -xvof archive.tar`
* `compress` (compression de fichiers en un seul avec l'extension "**.Z**")
`compress fichier`
* `compress -v fichier`
* `compress fichier.tar` (compression en un fichier avec l'extension **"tar.Z"**)
* `uncompress`(décompression ou restauration des fichiers compressés avec l'extension "**.Z**")
* `uncompress fichier.Z`
* `uncompress fichier.tar.Z`
* `uncompress un.Z deux.Z`
* `gzip` (programme de compression GNU qui forme des fichiers compressés avec l'extension "**.gz**")
* `gunzip` (programme de décompression GNU (g "unzip")des fichiers compressés avec l'extension "**.gz**")
* `gunzip fichier.gz`
* `zcat`
* `zcat fichier.gz | more` (pour décompresser un fichier "**.gz**" et l'afficher sur la sortie standard (l'écran))
* `zgrep`
* `zgrep "disk" /répertoire/*.gz` (recherche le terme "**disk**" à l'intérieur de plusieurs fichiers compressés)

## 5.  Création et gestion d'un script bash
### 5.1. Création de script
* La création d'un script bash n'est pas très compliquée. Il suffit de créer un fichier vierge, de lui donner un nom, de l'ouvrir par un double-clic et enfin d'écrire la ligne suivante comme première ligne de ce fichier.
* sheband (prémière ligne de script)

```
#!/bin/bash
```
* Remarque : il n'est pas nécessaire d'indiquer une extension pour le nom du fichier, la première ligne du fichier est suffisante pour que le système Linux reconnaisse qu'il s'agit d'un script bash.

### 5.2. Édition d'un script

* On peut éditer le fichier qui contient un script en ligne de commande à l'aide d'une des lignes de commande suivantes :

```
gedit nom_du_script
nano nom_du_script
```
# Documentation 
Voici quelques sites pour plus de détails sur la programmation Bash :
* [Les scripts bash](http://www.unixmaniax.fr/wiki/index.php?title=Les_scripts_bash)
* [Documentation pour débutant](https://guidespratiques.traduc.org/guides/vf/Bash-Beginners-Guide/Bash-Beginners-Guide.html)
* [encore plus de la documentation](https://abs.traduc.org/abs-fr/)

Et sur des commandes utiles 

* [Les commandes Bash](http://www.unixmaniax.fr/wiki/index.php?title=Bash_-_les_commandes)
* [Commandes partie 1](http://www.softndesign.org/manuels/unix-1.html)
* [Commandes partie 2](http://www.softndesign.org/manuels/unix-2.html)
* [Commandes partie 3](http://www.softndesign.org/manuels/unix-3.html)

[Jupyter et ses notebooks](https://python.sdv.univ-paris-diderot.fr/18_jupyter/)
[Tutorielle sur l'utilisation de jupyter avec commande bash](https://www.youtube.com/watch?v=Xnlqw3TsY-w)

## Pour s'exercer plus
* [TP1](https://github.com/Ezechiel-Tibiri/GNU-LINUX/blob/main/exo.zip)
* [TP2](https://github.com/Ezechiel-Tibiri/GNU-LINUX/blob/main/TP1.zip)
* [TP3](https://github.com/Ezechiel-Tibiri/GNU-LINUX/blob/main/TP3.zip)
* Création de script (home work pour demain)
>* Créer un script nommé **script2.sh** qui va deplacer tous les fichiers _.fasta_ contenu dans `/home/.../formation_linux/`dans un nouveau repertoir appelé **FASTA**, puis les archiver.
>* Créer un script nommé **script3.sh** qui afficher dans le shell : `Je me nomme ..., de nationalité..., présentement inscrit en ...(Master/thèse)`

# Evaluation 1


Créer un <span style="color:red">jupyter notebook</span> nommé Nom-Prenom_evaluation1.ipynb où vous allez lancer les commande suivantes :
* 1. Creer un sous-repertoire appéllé _EVALUATION_ qui sera placé dans le repertoire _cours_linux_ (2pts)
* 2. Télécharger une séquence et la placer dans le repertoire _EVALUATION_ (créé précedement) en suivant le lien  https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/009/858/895/GCF_009858895.2_ASM985889v3/GCF_009858895.2_ASM985889v3_genomic.fna.gz, puis decomprésser le fichier **.gz** (2pts)
* 3. Afficher la première ligne du fichier **GCF_009858895.2_ASM985889v3_genomic.fna**, de quel organisme s'agit-il et quel est sont numéro d'accession genBank? Affichier la taille et le nombre de ligne du fichier en question. (2pts)
* 4. Donner le nombre de site de reconnaissance *BamH*I en <span style="color:red">`5'-GGATCC-3'`</span> et en <span style="color:red">`3'-CCTAGG-5'`</span> du fichier **GCF_009858895.2_ASM985889v3_genomic.fna**  (2pts)
* 5. Quels sont les différents attributs (droits ou permission) du fichier **GCF_009858895.2_ASM985889v3_genomic.fna** ? (Penser à l'<span style="color:red">*user*, *group*, *other*</span>) (2pts)
* 6. Attribuer la permission <span style="color:red">d'**execution**</span> et rien que cela à tous les utilisateurs (2pts)
* 7. Extraire les 17 premières lignes et les rediriger vers un nouveau fichier nommé <span style="color:red">**GCF_009858895.fasta**</span> (2pts)
* 8. Combien de `ATG` il y 'a dans le nouveau fichier <span style="color:red">**GCF_009858895.fasta**</span> (2pts)
* 9. Ajouter 20N (NNNNNNNNNNNNNNNNNNNN) à la fin du ficheir <span style="color:red">**GCF_009858895.fasta**</span> (2pts)
* 10. Deposer votre jupyter notebook sur ce [drive]()

```
                          Bon courage!
```
# Evaluation 2


Créer un <span style="color:red">jupyter notebook</span> nommé _Nom-Prenom_evaluation2.ipynb_ où vous allez lancer les commande suivantes :

* 1. Télécharger le fichier GFF et le placé dans le repertoire _EVALUATION_ (créé précedement) en suivant le lien https://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/000/999/975/GCA_000999975.1_ASM99997v1/GCA_000999975.1_ASM99997v1_genomic.gff.gz

* 2. Faire un clone (copie) du fichier **GCA_000999975.1_ASM99997v1_genomic.gff.gz**; le renommer **GCA_000999975.1_ASM99997v1_genomic1.gff.gz** et decomprésser le nouveau fichier **.gz**

* 3. Afficher dans un premier temps le nombre de lignes total du fichier puis uniquement la 850ème ligne **GCA_000999975.1_ASM99997v1_genomic1.gff**

* 4. Faire un trie alphanumerique en colonne **2** sur le fichier **GCA_000999975.1_ASM99997v1_genomic1.gff** et le rediriger vers un nouveau fichier appélé **GCA_000999975.1_ASM99997v1_genomic1_sort-k2.gff** puis compter le nombre de fois que le mot _gene_ apparait dans le nouveau fichier

* 5. Selectionne les lignes 1250 à 1350 du fichier **GCA_000999975.1_ASM99997v1_genomic1.gff** et les rediriger vers un nouveau fichier appelé **GCA_000999975.1_ASM99997v1_genomic1_sed.gff** puis compté le nombre de fois que CDS apparait dans le nouveau fichier

* 6. Deposer votre script en utilisant `scp` (*Nom-Prenom_evaluation1.ipynb*) sur le repertoire `/export/share` du cluster de l'Univesité Joseph Ki-Zerbo (UJKZ) via votre compte `formationX` 

**Attention la double utilisation d'un même compte n'est pas autorisé!!!**

```
                      BON COURAGE À TOUS.T.E.S
```
