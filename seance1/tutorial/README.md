# Objectifs

- **Répertoires** : Afficher le chemin du répertoire courant. Afficher le contenu d'un répertoire. Changer de répertoire. Créer un répertoire.
- **Aborescence Linux** : Distinguer la notion de chemin absolu et relatif. Utiliser les raccourcis de l'arborescence Linux (`.`, `..`, `~`). Afficher l'arborescence Linux.
- **Espace disque** : Déterminer l'espace disque occupé par un fichier ou un répertoire.
- **Fichier texte** : Afficher le contenu d'un fichier texte, le modifier.
- **Aide** : Obtenir de l'aide et de la documentation sur une commande.
- **Historique** : Afficher l'historique des commandes. Rappeler une commande de l'historique.
- **Redirection** : Sauver le résultat d'une commande dans un fichier.


## Partie 1 : Exploration de fichiers et de répertoires

Lancez un terminal pour obtenir un *shell*.

Ensuite :

- Créez le répertoire `bioinfo`
- Déplacez-vous dans ce nouveau répertoire.
- Affichez le chemin du répertoire courant.
- Vérifiez que vous obtenez un chemin du type `/home/ezechiel/bioinfo` où `ezechiel` est remplacé par votre nom d'utilisateur.

> **Aide**
> > Le caractère `$` au début de chaque ligne est un repère qui représente votre invite de commande. 
> > Il ne faut pas entrer ce caractère dans votre ligne de commande.
> > 
> > Le caractère `~` est un raccourci pour désigner le répertoire personnel de l'utilisateur.
> > ```bash
> > $ cd ~
> > $ mkdir bioinfo
> > $ cd bioinfo
> > $ pwd
> > ```
> > Vous devriez obtenir un chemin du type `/home/ezechiel/bioinfo` où `ezechiel` est remplacé par votre nom d'utilisateur.
{:.answer}

Téléchargez ensuite les fichiers des jeux de données du DUBii avec la commande :

```bash
$ git clone git@github.com:Ezechiel-Tibiri/bioinformatique_2023.git
```

Remarques :

1. Le caractère `$` au début d'une ligne de commande est un repère visuel qui représente votre invite de commande. Il ne faut pas entrer ce caractère dans votre ligne de commande.
2. La commande à exécuter est assez longue et complexe. Pour éviter de faire des erreurs et aller plus vite, utilisez le copier/coller. Voici deux méthodes :

   a. Sélectionnez la commande en la surlignant avec le clic gauche de votre souris. Puis dans votre *shell*, cliquez sur le bouton du milieu de votre souris.
   
   b. Sélectionnez la commande en la surlignant avec le clic gauche de votre souris. Appuyez ensuite sur les touches <kbd>Ctrl</kbd> + <kbd>C</kbd> (c'est-à-dire les touches <kbd>Control</kbd> et <kbd>C</kbd> pressées en même temps). Dans votre *shell*, appuyez sur les touches <kbd>Ctrl</kbd> + <kbd>Maj</kbd> + <kbd>V</kbd> (c'est-à-dire les touches <kbd>Control</kbd>, <kbd>Majuscule</kbd> et <kbd>V</kbd> pressées en même temps).

Patientez quelques instants que les données soient téléchargées.


**Question 1.1** : Déplacez-vous dans le répertoire `study-cases` nouvellement créé.

> **Réponse**
> > ```bash
> > $ cd bioinformatique_2023/data/study-cases
> > ```
{:.answer}

Utilisez la commande `tree` pour visualiser l'arborescence qui représente l'organisation des répertoires, sous-répertoires et fichiers.

```bash
$ tree
```

**Question 1.2** : Déplacez-vous maintenant dans le répertoire `Escherichia_coli/bacterial-regulons_myers_2013/data/ChIP-seq`

Astuce : utilisez la touche <kbd>Tab</kbd> (*Tabulation*) pour compléter les noms des répertoires qui peuvent être très longs et ainsi éviter les erreurs.

> **Réponse**
> > ```bash
> > $ cd Escherichia_coli/bacterial-regulons_myers_2013/data/ChIP-seq
> > ```
{:.answer}


**Question 1.3** : Combien de fichiers `.bed` y a-t-il dans ce répertoire ?

> **Réponse**
> > ```bash
> > $ ls
> > FNR1_vs_input1_cutadapt_bowtie2_homer.bed  FNR_200bp.wig
> > FNR1_vs_input1_cutadapt_bowtie2_macs2.bed  input_200bp.wig
> > ```
> >
> > Ou plus directement, avec `*bed` qui signifie tous les fichiers se terminant par *bed* :
> > ```bash
> > $ ls *bed
> > FNR1_vs_input1_cutadapt_bowtie2_homer.bed  FNR1_vs_input1_cutadapt_bowtie2_macs2.bed
> > ```
> > Il y a deux fichiers avec l'extension `.bed`
{:.answer}


**Question 1.4** : En restant dans le même répertoire, déterminez le nombre de fichiers présents dans le répertoire `RNA-seq` qui est au même niveau que le répertoire `ChIP-seq` ?

> **Réponse**
> > ```bash
> > $ ls ../RNA-seq
> > cutadapt_bwa_featureCounts_all.tsv
> > ```
> > Il y a un seul fichier.
{:.answer}

## Partie 2 : Espace disque

### Connaître le taux d'occupation des espaces disques d'un poste de travail

La commande `df` (pour *disk free*) permet de connaître les quantités d'espace occupé et disponible pour tous les disques du système. L'option `-h` permet d'afficher ces valeurs *human readable*, c'est-à-dire avec les unités ko, Mo, Go, To ...

```bash
$ df -h
```

### Connaître la quantité d'espace disque occupé par un fichier/dossier.

La commande pour connaître la taille des fichiers présents dans un dossier est `ls -lh`.

**Question 2.1** : Utilisez la commande `ls` avec les options `l` et `h` pour afficher le contenu du répertoire courant, puis déterminez la taille du fichier `FNR_200bp.wig`.

> **Réponse**
> > ```bash
> > $ ls -lh
> > total 232K
> > -rw-rw-r-- 1 ezechiel ezechiel 8,9K avril  4 20:30 FNR1_vs_input1_cutadapt_bowtie2_homer.bed
> > -rw-rw-r-- 1 ezechiel ezechiel  45K avril  4 20:30 FNR1_vs_input1_cutadapt_bowtie2_macs2.bed
> > -rw-rw-r-- 1 ezechiel ezechiel  80K avril  4 20:30 FNR_200bp.wig
> > -rw-rw-r-- 1 ezechiel ezechiel  90K avril  4 20:30 input_200bp.wig
> > ```
> > Le fichier `FNR_200bp.wig` a une taille d'environ 80 Ko.
{:.answer}


Pour connaître la quantité d'espace disque occupée par un dossier, utilisez la commande `du` (*disk usage*), encore une fois avec l'option `-h`. On peut aussi afficher la version résumé avec l'option `-s`.

**Question 2.2** : Déterminez la taille du répertoire `study-cases`.

Rappel : si vous avez bien suivi les instructions depuis le début, le répertoire `study-cases` est normalement dans le répertoire `dubii` dans votre repertoire personnel.

> **Réponse**
> > Le chemin du répertoire `study-cases` depuis le répertoire personnel (représenté par `~`) est donc `~/dubii/study-cases`.
> > ```bash
> > $ du -sh ~/Documents/2024/cours/bioinformatique_2023/data/study-cases
 30M	/home/ezechiel/Documents/2024/cours/bioinformatique_2023/data/study-cases
> > ```
> > Le dossier `study-cases` a une taille totale de 30 Mo.
{:.answer}

## Partie 3 : Afficher le contenu d'un fichier texte

Sous Linux, on dispose de plusieurs commandes pour afficher tout ou partie du contenu de fichiers texte.
`head`; ` tail`; `less`; `more`; `cat`...

### cat

La commande `cat` affiche et concatène le contenu du ou des fichiers donnés en arguments
(ou de l'entrée standard) sur la sortie standard (à l'écran).

**Question 3.1** : Affichez le contenu du fichier `cutadapt_bwa_featureCounts_all.tsv` situé
dans le répertoire `RNA-seq` (qui est au même niveau que le répertoire `ChIP-seq`).

> **Réponse**
> > On suppose que vous êtes toujours dans le répertoire `ChIP-seq`.
> > ```bash
> > $ cat ../RNA-seq/cutadapt_bwa_featureCounts_all.tsv
> > Geneid  WT1 WT2 dFNR1   dFNR2
> > b0001   70  98  72  63
> > b0002   23421   33092   32156   20749
> > b0003   7538    10350   9596    6490
> > b0004   8263    11927   11042   7145
> > b0005   121 156 104 62
> > b0006   177 224 287 209
> > b0007   138 116 68  50
> > b0008   2964    3971    4211    2823
> > b0009   213 205 196 128
> > [...]
> > b4400   82  42  37  35
> > b4401   3349    4692    2619    1609
> > b4402   201 318 224 128
> > b4403   82  116 87  68
> > ```
{:.answer}
