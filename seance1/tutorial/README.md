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

**Question 3.3** : Quel inconvénient majeur voyez-vous à la commande `cat`?  

> **Réponse**
> > La commande `cat` affiche la totalité des fichiers ce qui rend la sortie
> > de la commande souvent illisible lorsque les fichiers sont très grands.
{:.answer}


### less

La commande `less` afficher le contenu d'un ou plusieurs fichiers
page par page, ce qui est très utile lorsqu'on manipule des fichiers de taille
importante.

Quelques raccourcis clavier :

- `barre d'espace` : se déplace dans le fichier page par page
- `flèche haut` : se déplace d'une ligne vers le haut
- `flèche bas` : se déplace d'une ligne vers le bas
- `g` : se déplace au début du fichier (également `<`)
- `G` : se déplace à la fin du fichier (également `>`)
- `/` : recherche les occurences d'un motif
- `n` : passe à l'occurence suivante du motif recherché
- `N` : passe à l'occurence précédente du motif recherché
- `:n` : passe au fichier suivant ('next file', si plusieurs fichiers en arguments)
- `:p` : passe au fichier précédent ('previous file', si plusieurs fichiers en arguments)
- `q` : quitte less  

**Question 3.4** : Affichez le contenu du fichier `../RNA-seq/cutadapt_bwa_featureCounts_all.tsv` avec `less`.

> **Réponse**
> > ```bash
> > less ../RNA-seq/cutadapt_bwa_featureCounts_all.tsv
> > ```
> > Pensez à utiliser la touche <kbd>Q</kbd> pour quitter `less`.
{:.answer}

### head

La commande `head` affiche uniquement le début du ou des fichier(s) passé(s) en argument.
Par défaut, `head` affiche les 10 premières lignes d'un fichier.  
L'option `-n <N>` permet d'afficher les `N` premières lignes d'un fichier.

**Question 3.5** : Affichez les 20 premières lignes du fichier `../RNA-seq/cutadapt_bwa_featureCounts_all.tsv`.

> **Réponse**
> > ```bash
> > $ head -n 20 ../RNA-seq/cutadapt_bwa_featureCounts_all.tsv
> > Geneid	WT1	WT2	dFNR1	dFNR2
> > b0001	70	98	72	63
> > b0002	23421	33092	32156	20749
> > b0003	7538	10350	9596	6490
> > b0004	8263	11927	11042	7145
> > b0005	121	156	104	62
> > b0006	177	224	287	209
> > b0007	138	116	68	50
> > b0008	2964	3971	4211	2823
> > b0009	213	205	196	128
> > b0010	184	193	130	74
> > b0011	44	13	13	10
> > b0013	18	6	7	3
> > b0014	10758	14747	15432	10243
> > b0015	1343	1667	1549	1045
> > b0016	261	326	252	141
> > b4412	0	0	0	0
> > b0018	7	0	2	1
> > b4413	1	0	1	1
> > b0019	714	944	1093	704
> > ```
{:.answer}

### tail

La commande `tail` affiche uniquement la fin du ou des fichier(s) passé(s) en argument.
Par défaut `tail` affiche les 10 dernières lignes d'un fichier.  
L'option `-n <N>` permet d'afficher d'afficher les `N` dernières lignes d'un fichier.

**Question 3.6** : Affichez les 20 dernières lignes du fichier `../RNA-seq/cutadapt_bwa_featureCounts_all.tsv`.

> **Réponse**
> > ```bash
> > $ tail -n 20 ../RNA-seq/cutadapt_bwa_featureCounts_all.tsv
> > b4384	846	1241	1173	751
> > b4385	205	224	145	84
> > b4386	243	233	192	106
> > b4387	164	197	142	98
> > b4388	409	489	404	264
> > b4389	712	785	615	350
> > b4390	421	535	471	316
> > b4391	2341	2740	2888	1913
> > b4392	538	601	717	464
> > b4393	203	258	202	137
> > b4394	256	292	243	167
> > b4395	404	591	422	309
> > b4396	903	1161	1055	709
> > b4397	235	280	242	143
> > b4398	210	251	178	122
> > b4399	166	115	122	101
> > b4400	82	42	37	35
> > b4401	3349	4692	2619	1609
> > b4402	201	318	224	128
> > b4403	82	116	87	68
> > ```
{:.answer}

## Partie 4 : L'éditeur de texte nano

Sous Linux, il existe beaucoup d'éditeurs de fichiers textes qui soient utilisables dans un terminal. Parmi les plus connus on trouve : `vi`, `emacs` et `nano`.

Nano est l'éditeur de texte le plus simple à utiliser.

**Question 4.1** : Qu'est-ce qu'un éditeur de texte ? Quelle différence avec un traitement de texte ?

> **Réponse**
> > Un éditeur de texte est un programme qui modifie des fichiers texte sans mise en forme.  
> > Un traitement de texte est un logiciel, le plus souvent avec une interface graphique, utilisé pour mettre en forme des documents
{:.answer}

Pour lancer l'éditeur de texte nano, il suffit de taper la commande `nano`, 
éventuellement suivi d'un nom de fichier à éditer.

Toutes les commandes possibles sont résumées dans le bandeau en bas de l'écran
Le symbole `^` signifie <kbd>Ctrl</kbd> (la touche *Contrôle* de votre clavier).

Voici les raccourcis les plus importants :
- <kbd>Ctrl</kbd> + <kbd>G</kbd> : afficher l'aide
- <kbd>Ctrl</kbd> + <kbd>K</kbd> : couper la ligne de texte (et la mettre dans le presse-papier)
- <kbd>Ctrl</kbd> + <kbd>U</kbd> : coller la ligne de texte que vous venez de couper
- <kbd>Ctrl</kbd> + <kbd>C</kbd> : afficher à quel endroit du fichier votre curseur est positionné (numéro de ligne)
- <kbd>Ctrl</kbd> + <kbd>W</kbd> : rechercher une chaine de caractères dans le fichier. N'utilisez pas ce raccourci avec un terminal dans Jupyter Hub, cela fermerait l'onglet de votre navigateur.
- <kbd>Ctrl</kbd> + <kbd>O</kbd> : enregistrer le fichier (écrire)
- <kbd>Ctrl</kbd> + <kbd>X</kbd> : quitter Nano.

Vous pouvez vous déplacer dans le fichier avec les flèches du clavier ainsi
qu'avec les touches <kbd>PageUp</kbd> et <kbd>PageDown</kbd> pour vous déplacer
de page en page (les raccourcis <kbd>Ctrl</kbd> +  <kbd>Y</kbd> et <kbd>Ctrl</kbd> + <kbd>V</kbd> fonctionnent aussi).

**Question 4.2** : 

1. Déplacez-vous dans le répertoire `~/bioinfo/bioinformatique_2023/data/study-cases/Escherichia_coli/`
2. Ouvrez avec l'éditeur `nano` le fichier `Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chromosome.Chromosome.gff3`
3. Supprimez les 4 lignes qui commencent par :
    ```
    Chromosome      ena     gene    190     255
    Chromosome      ena     mRNA    190     255
    Chromosome      ena     exon    190     255
    Chromosome      ena     CDS     190     255
    ```
4. Enregistrez le fichier sous le nom `Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chromosome.Chromosome_new.gff3` (la fin du nom du fichier est `Chromosome_new.gff3` au lieu de `Chromosome.gff3`).


> **Réponse**  
> > ```bash
> > $ cd ~/Documents/2024/cours/bioinformatique_2023/data/study-cases/Escherichia_coli
> > $ nano Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chromosome.Chromosome.gff3
> > ```
> > Rappel : pensez à utiliser la touche <kbd>Tab</kbd> pour compléter rapidement le nom du fichier à ouvrir avec nano.  
> >  
> > Dans nano, déplacez-vous sur la ligne 10. Utilisez le raccourci <kbd>Ctrl</kbd> + <kbd>C</kbd> pour connaitre le numéro de ligne courante.
> >  
> > Supprimez ensuite les lignes 10, 11, 12 et 13 avec le raccourci- <kbd>Ctrl</kbd> + <kbd>K</kbd>.
> >  
> > Au moment de sauvegarder le fichier avec la commande <kbd>Ctrl</kbd> + <kbd>O</kbd>, pensez à modifier le nom du fichier.  
> >
{:.answer}


## Partie 5 : Obtenir de l'aide sur une commande

Sous Linux toutes les commandes sont documentées de manière standardisée.

Il y a deux moyens d'accèder à l'aide d'une commande :

1. Via la commande `man <nom_commande>` (par exemple `man ls`) qui affiche le manuel,
c'est-à-dire la description complète de la commande page par page avec les facilités de
recherche d'un éditeur de texte. La touche <kbd>Q</kbd> permet de quitter ce manuel.

1. Via l'option `--help` de la commande (par exemple `ls --help`) qui affiche un résumé de la
documentation et des options.


**Question 5.1** : Quel signifie l'option `-N` de la commande `less` ?

> **Réponse**
> > ```text
> > $ man less
> > [...]
> >  -N or --LINE-NUMBERS
> >                   Causes a line number to be displayed at the beginning of each line in the display.
> > [...]
> > ```
> L'aide nous apprend que l'option `-N` affiche les numéros de lignes à gauche de chaque ligne.
{:.answer}

## Partie 6 : Répéter une commande, notion d'historique

Le *shell* garde en mémoire les commandes lancées par un utilisateur.

La liste des commandes lancées par un utilisateur est accessible via la commande
`history`.
Il est aussi possible de retrouver une commande en utilisant la commande `!`
Par exemple la commande `!?expression?` permet de relancer la dernière commande
utilisée contenant le mot `expression`.
La commande `!grep` permet de relancer la dernière commande utilisée commençant par 'grep'

**Question 6.1** : Lancez la commande `history`, puis essayer de deviner ce que fait la commande `!-4` ?

> **Réponse**
> > Cette commande permet d'exécuter la 4° dernière commande exécutée.
> > 
{:.answer}

On peut également retrouver les commandes déjà exécutées en naviguant dans
l'historique avec les flèches haut et bas du clavier.


## Partie 7 : Sauver le résultat d'une commande Linux dans un fichier

La possibilité de redirection de l'entrée ou de la sortie standard est une
notion fondamentale du système d'exploitation Linux.

Par défaut tout programme Linux a trois flux de données :

- une **entrée standard**, appelée `stdin` par défaut associée au **clavier**
- une **sortie standard**, appelée `stdout`, par défaut associée à **l'écran**
- une **erreur standard** appelée `stderr`, par défaut également associée à **l'écran**

Une redirection est une modification de l’une de ces associations.
Elle est valable uniquement le temps de la commande sur laquelle elle porte.

Pour modifier l'entrée standard d'une commande en lisant les données d'un
fichier `infile` on utilise `< infile`.

Pour modifier la sortie standard d'une commande et écrire les résultats dans un
fichier `outfile` on utilise `> outfile` ou `>> outfile`

Pour modifier l'erreur standard d'une commande et écrire les messages d'erreurs
dans un fichier `errfile` on utilise : `2> errfile`.

En résumé, dans le *shell*, un programme peut s'écrire :
```bash
$ program < infile > outfile 2> errfile
```

**Question 7.1** : 

- Déplacez-vous dans le répertoire `~/bioinfo/bioinformatique_2023/data/study-cases/Escherichia_coli/bacterial-regulons_myers_2013/data/ChIP-seq`
- Redirigez le résultat de la commande `cat` sur le fichier `FNR1_vs_input1_cutadapt_bowtie2_homer.bed` dans le fichier `test.txt`.
- Que contient le fichier `test.txt` ?
- Vérifiez votre réponse en utilisant la commande `diff` pour afficher les différences entre les deux fichiers :
    ```bash
    $ diff FNR1_vs_input1_cutadapt_bowtie2_homer.bed test.txt
    ```

> **Réponse**
> > ```bash
> > $ cd ~/Documents/2024/cours/bioinformatique_2023/data/study-cases/Escherichia_coli/bacterial-regulons_myers_2013/data/ChIP-seq
> > $ cat FNR1_vs_input1_cutadapt_bowtie2_homer.bed > test.txt
> > ```
> - `cat` affiche le contenu de `FNR1_vs_input1_cutadapt_bowtie2_homer.bed`.
> - `>` redirige la sortie de la commande `cat` vers le fichier `test.txt`.
> - Finalement, le fichier `test.txt` contient le contenu du fichier `FNR1_vs_input1_cutadapt_bowtie2_homer.bed`.
> 
> La commande `diff FNR1_vs_input1_cutadapt_bowtie2_homer.bed test.txt` ne renvoie rien car les deux fichiers sont bien identiques.
{:.answer}
