
# Unix - séance 2

# Objectifs
- **Révisions séance 1** : shell & arborescence, accéder au contenu d'un fichier, éditer un fichier, aide, historique et rappel de commandes, rédirections, git, bonnes pratiques
- **Extraction et flux de données** : Recherche de fichiers et extraction de contenus de fichiers (find, grep, cut, head, sort, uniq, wc), enchainement de commandes avec `|`
- **Expressions régulières** : Notions de base sur les expressions régulières et initiation à `sed`
- **Compression et archivage** : commade `tar` et commandes de compression
- **Travail à distance** : accéder à une machine distance et transférer des données


# Accéder aux tutoriels
- [Extraction et flux de données](01-flux.md)
- [Expressions régulières](02-regex.md)
- [Compression et archivage](03-tar.md)
- [Travail à distance (ssh & scp)](04-ssh_scp.md)

# Partie 2.1 : Recherche de fichiers ou de contenus

## Objectifs

- Recherche de fichiers avec `find`
- Extraction de contenus de fichiers (`grep`, `cut`, `head`, `sort`, `uniq`, `wc`)
- Enchainement de commandes avec `|`

## Recherche de fichier : find
 
La commande `find` permet de rechercher des fichiers de manière récursive dans
un chemin à partir d'un motif.

Un motif est ici une expression ou une chaine de caractères correspondant au 
nom ou une partie du nom du fichier recherché

**Syntaxe** : `find [chemin] -name <MOTIF>`  

**Question 1** : Aller dans le répertoire `study-cases` (situé dans le 
répertoire `~/dubii`) et rechercher tous les
fichiers au format bed (i.e. dont l'extension est `.bed`)

> **Solution :**: 
> > ```bash
> > $ find . -name "*.bed"
> > ./Escherichia_coli/bacterial-regulons_myers_2013/data/ChIP-seq/FNR1_vs_input1_cutadapt_bowtie2_macs2.bed
> > ./Escherichia_coli/bacterial-regulons_myers_2013/data/ChIP-seq/FNR1_vs_input1_cutadapt_bowtie2_homer.bed
> > ```
{:.answer}

## Recherche de contenu dans un fichier : grep  

La commande `grep` permet de rechercher et afficher les lignes contenant un
motif donné en argument dans un ou des fichiers donnés en argument.

Un motif est ici une expression ou une chaine de caractères correspondant à
l'élément recherché (un nom de gène, de protéine,...etc).

**Syntaxe** : `grep [options] <MOTIF> <FICHIERS>`

La commande grep a beaucoup d'options très utiles, par exemple :  

- `-i` : ignore les distinctions de casse dans le motif
- `-v` : sélectionne les lignes NE contenant PAS le motif
- `-n` : préfixe chaque ligne de sortie avec son numéro de ligne
- `-c` : affiche uniquement le nombre total de lignes contenant le motif  

**Question 2** : rechercher toutes les occurences du gène 'oriC' en affichant le
numéro de ligne de chaque occurence dans le fichier 
Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chromosome.Chromosome.gff3**

> **Solution :**: 
> > ```bash
> >  grep -ni "oric" Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chromosome.Chromosome.gff3
> >  4859:Chromosome    ena gene    1028404 1028721 .   -   .   ID=gene:b0966;Name=hspQ;biotype=protein_coding;description=heat shock protein involved in degradation of mutant DnaA%3B hemimethylated oriC DNA-binding protein;gene_id=b0966;logic_name=ena
> >  8256:Chromosome    ena gene    1704949 1705164 .   +   .   ID=gene:b1625;Name=cnu;biotype=protein_coding;description=nucleoid-associated oriC-binding protein%3B H-NS and StpA stabilizing factor;gene_id=b1625;logic_name=ena
> >  18950:Chromosome   ena_rep_origin  biological_region   3925744 3925975 .   +   .   external_name=oriC%3B origin of chromosomal DNA replication%2C bidirectional%3B oriC%3B b4489%3B ECK3735%3B JWS0001;logic_name=ena_rep_origin
> >  22228:Chromosome   ena gene    4634441 4635310 .   -   .   ID=gene:b4396;Name=rob;biotype=protein_coding;description=right oriC-binding transcriptional activator%2C AraC family;gene_id=b4396;logic_name=ena
> >  
> > ```
{:.answer}

# Partie 2.2 : Extraction des données d'un fichier 

## cut  

La commande `cut` permet d'extraire une ou plusieurs colonnes d'un fichier.

L'option `-c` permet d'utiliser *les positions des caractères* dans le fichier
(cad dire les numéro des colonnes).

Exemple : extraction des caractères 1 à 10 d'un fichier

```bash
$ cut -c 1-10 <FILE>
```

L'option `-f` permet de spécifier *les positions des champs (fields)* dans le fichier. 
Le délimitateur par défaut est la tabulation, on peut le changer avec l'option `-d`.

Exemple : extraction de la deuxième colonne d'un fichier au format csv

```bash
$ cut -d "," -f 2 <CSV_FILE>
```

**Question 3** : Rendez-vous dans le répertoire `Escherichia_coli/bacterial-regulons_myers_2013/data/RNA-seq`.
Extraire de deux manières différentes la colonne Geneid du fichier `cutadapt_bwa_featureCounts_all.tsv`**

> **Solution :**   
> > ```bash
> > $ cut -f 1 cutadapt_bwa_featureCounts_all.tsv 
> > [...]
> > b4400
> > b4401
> > b4402
> > b4403
> > $ cut -c 1-6 cutadapt_bwa_featureCounts_all.tsv
> > [...]
> > b4400
> > b4401
> > b4402
> > b4403
> > ```
{:.answer}


## sort  

La commande `sort` permet de trier les lignes du ou des fichiers donnés en argument  
**Attention**: le tri par défaut est selon le code ASCII et pas selon 
l'ordre numérique.
Pour faire un tri numérique, utiliser l'option `-g` (plus polyvalente que l'option `-n` habituellement préconisée).

**Question 4** : Extraire la 2ème colonne 'WT1' du fichier `cutadapt_bwa_featureCounts_all.tsv`
en redirigeant le résultat dans un fichier de sortie 'cutadapt_bwa_featureCounts_WT1.tsv'.
Trier ensuite les valeurs de ce fichier par ordre croissant et écrire le résultat
dans le fichier `cutadapt_bwa_featureCounts_WT1_sorted.tsv`.

> **Solution :**  
> > ```bash  
> > cut -f 2 cutadapt_bwa_featureCounts_all.tsv > cutadapt_bwa_featureCounts_WT1.tsv
> > sort -g cutadapt_bwa_featureCounts_WT1.tsv > cutadapt_bwa_featureCounts_WT1_sorted.tsv
> > ```
{:.answer}


## uniq  

La commande `uniq` permet d'éliminer les lignes identiques *et consécutives* d'un fichier.
Pour éliminer les lignes répétées sur l'ensemble d'un fichier, il est donc nécessaire
de trier le fichier avant d'utiliser la commande `uniq`.

Les options les plus couramment utilisées de `uniq` sont :  

- `-c` pour afficher le nombre d'occurences de chaque ligne,
- `-d` pour afficher les lignes dupliquées,
- `-i` pour ignore la casse.

**Question 5** : Éliminer les lignes dupliquées du fichier `cutadapt_bwa_featureCounts_WT1_sorted.tsv`
et écrire le résultat dans le fichier `cutadapt_bwa_featureCounts_WT1_sorted_uniq.tsv`    

> **Solution :**  
> > ```bash  
> > $ uniq cutadapt_bwa_featureCounts_WT1_sorted.tsv > cutadapt_bwa_featureCounts_WT1_sorted_uniq.tsv
> > ```
{:.answer}


## wc

La commande `wc` (*word count*) permet de compter le nombre de lignes, de mots
et de caractères du fichier ou des fichiers donnés en argument.

**Question 6** : Comment afficher uniquement le nombre de lignes d'un fichier ?
Combien de lignes y a-t-il dans les fichiers `cutadapt_bwa_featureCounts_WT1_sorted.tsv` 
et `cutadapt_bwa_featureCounts_WT1_sorted_uniq.tsv` ?

> **Solution :** 
> > ```bash  
> > $ wc -l cutadapt_bwa_featureCounts_WT1_sorted.tsv
> > 4498 cutadapt_bwa_featureCounts_WT1_sorted.tsv
> > 
> > $ wc -l cutadapt_bwa_featureCounts_WT1_sorted_uniq.tsv
> > 1357 cutadapt_bwa_featureCounts_WT1_sorted_uniq.tsv
> > ```
{:.answer}


# Partie 2.3 : redirection des flux d'entrée et sortie et "|"

## Sauver le résultat d'une commande Linux dans un fichier : notion de redirection

La possibilité de redirection de l'entrée ou de la sortie standard est une
notion fondamentale du système d'exploitation Linux.

Par défaut tout programme Linux a trois flots de direction :

- une **entrée standard**, appelée `stdin` par défaut associée au **clavier**
- une **sortie standard**, appelée `stdout`, par défaut associée à **l'écran**
- une **erreur standard** appelée `stderr`, par défaut associée à **l'écran**

Une redirection est une modification de l’une de ces associations.
Elle est valable uniquement le temps de la commande sur laquelle elle porte.

Pour modifier l'entrée standard d'une commande en lisant les données d'un
fichier `infile` on utilise `< infile`.

Pour modifier la sortie standard d'une commande et écrire les résultats dans un
fichier `outfile` on utilise `> outfile` ou `>> outfile`

Pour modifier l'erreur standard d'une commande et écrire les messages d'erreurs
dans un fichier `errfile` on utilise : `2> errfile`.

En résumé toute commande Linux peut s'écrire
`$cmd < infile > outfile 2> errfile`

**Question 7**: rediriger le résultat de la commande `cat` sur le fichier
`ChIP-seq/FNR1_vs_input1_cutadapt_bowtie2_homer.bed` dans le fichier `test.txt`.
Que contient le fichier `test.txt` ?

> **Réponse**
> > ```bash
> > $ cat ChIP-seq/FNR1_vs_input1_cutadapt_bowtie2_homer.bed > test.txt
> > ```
> `cat` affiche le contenu de `ChIP-seq/FNR1_vs_input1_cutadapt_bowtie2_homer.bed`.
> `>` redirige la sortie de la commande vers le fichier `test.txt`.
> Finalement, le fichier `test.txt` contient le contenu du fichier `ChIP-seq/FNR1_vs_input1_cutadapt_bowtie2_homer.bed`.
{:.answer}

## Le pipe `|`

Le `|` est une manière simple et élégante d'enchainer des commandes sous Unix.
Nous avons déjà vu qu'il est possible de rediriger l'entrée, ou la sortie standard,
ou la sortie erreur d'une commande vers un fichier de son choix.

Le `|` permet rediriger la sortie d'une commande vers l'entrée d'une autre commande.
On peut enchainer un nombre pratiquement illimité de commandes grâce à des pipes.

**Question 8** : Comment afficher page par page le nombre d'occurences de chaque
valeur de la colonne `WT1` du fichier `cutadapt_bwa_featureCounts_all.tsv` en 1 seule commande ?**

> **Solution :** 
> > ```bash 
> > $ cut -f 2 cutadapt_bwa_featureCounts_all.tsv | sort -g | uniq -c | less
> > ```
{:.answer}


**Question 9** : Utiliser le `|` et les commandes précédentes pour déterminer le nombre de gènes uniques dans le fichier `Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chromosome.Chromosome.gff3`  
Le fichier est dans le répertoire `~/bioinfo/bioinformatique_2023/data/study-cases/Escherichia_coli`  

Indication : les noms de gènes se trouvent dans la 9ème colonne du fichier gff3

> **Solution :**     
>>
>> ```bash
>> $ cut -f 9 ~/Documents/2024/cours/bioinformatique_2023/data/study-cases/Escherichia_coli/Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chromosome.Chromosome.gff3 | cut -d ";" -f 1 | grep "ID=gene" | sort -u | wc -l
>>  4497
>>  ```   
{:.answer}


# Partie 2.2 : Notions sur les expressions régulières

## Objectifs

- Notions de base sur les expressions régulières
- Initiation à `sed`

## Les expressions de bases  

Une expression régulière (en anglais *Regular Expression*) 
est une chaîne de caractères décrivant un ensemble de chaîne de
caractères.

On appelle également une expression regulière "regex" ou "motif"
(*pattern* en anglais).

De nombreux programmes utilisent les expressions régulières
(par exemple `sed`, `grep`, `vi`, ...) mais il est important 
de noter que leur syntaxe peut varier d'un programme à l'autre.

Le design d'expressions régulières peut rapidement s'avérer complexe et nécessite un savoir-faire certain.

Cette possibilité illustre cependant la puissance de l'environnement Unix 
pour spécifier des recherches et actions complexes en utilisant des lignes 
de commande concises.  

Les expressions régulières vont se baser sur des caractères spéciaux ou métacaractères :

- `.` correspond à n'importe quel caractère  
- `*` correspond à une répétition de 0 à n occurences (déconseillé) 
- `+` correspond à une répétition de 1 à n occurences 
- les caractères entre crochets (`[ ]`) correspondent à un ensemble de valeurs possibles (intervale ou explicites par exemple `[A-D]` est équivalent à [A,B,C,D]
- `^` indique une recherche d'un motif en début de ligne  
- `$` indique une recherche d'un motif en fin de ligne  

**Question :** Rechercher tous les noms de gènes nommés dnaA, dnaB, dnaC
et dnaD dans le fichier
`Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chromosome.Chromosome.gff3`

> **Solution :**  
> > ```bash 
> > $ grep -e "dna[A-D]" Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chromosome.Chromosome.gff3 
> > ```
{:.answer}


Pour aller plus loin :
- Tutorial sur les expressions régulières :  https://librarycarpentry.org/lc-data-intro/04-regular-expressions/  
- Site pour tester une expression régulère : https://regex101.com  

## sed  

`sed` (stream editor) est éditeur de texte non interactif permettant de filtrer et transformer les lignes du ou des fichier donnés en argument. La commande ne modifie pas le(s) fichier(s) traité(s)et écrit le résultat sur la sortie standard.  
La commande `sed` est très utile car elle permet de réaliser des commandes complexes sur des gros fichiers en utilisant des expressions régulières.  

**Syntaxe** : `sed [expression] <fichier-a-traiter>`

La partie `expression` peut contenir des fonctions de filtrage ou de transformation des lignes du fichier-a-traiter  
Nous ne verrons ici que quelques cas d'utilisation très courants en bioinformatique.  

### Exemple 1 : Remplacer toutes les occurences d'une chaine de caractères dans un fichier  
Remplaçons toutes les occurences de `Chromosome` par `chr` dans le fichier Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chromosome.Chromosome.gff3   
Pour cela on utilise la fonction de subsitution *s*  
`sed 's/Chromosome/chr/g' Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chromosome.Chromosome.gff3 > Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chr.gff3`

### Exemple 2 : Supprimer toutes les occurences d'une chaine de caractères dans un fichier  
Supprimons toutes les lignes contenant le nom `oriC` dans le fichier Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chromosome.Chromosome.gff3  
Pour cela on utilise la fonction de suppression *d*  
`sed '/oriC/d' Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chromosome.Chromosome.gff3  > Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chromosome.Chromosome_wo_oriC.gff`


# Partie 2.3 : Espace de stockage, compression et archivage des données

Il est de plus en plus facile d'obtenir de plus en plus de données.
Il est important d'être conscient des capacités de stockage de sa machine d'une part,
et du fait qu'un trop grand nombre de fichiers sur une machine peut engendrer
un crash pur et simple du système.

## Objectifs

- comment savoir si un disque est plein (`df`),
- comment connaître la quantité d'espace disque occupé par un fichier/dossier (`du`),
- comment trouver les fichiers volumineux sur un disque (`find`),
- comment réduire la quantité d'espace disque occupé (`gzip`),
- comment réduire le nombre de fichiers présents sur un disque (`tar`).


## Connaître la quantité d'espace disque occupée et disponible sur un disque

La commande `df` permet de connaître les quantités d'espace occupé et disponible
pour tous les disques du système.

**Question**: Quelle est la quantité d'espace disque disponible sur votre machine ?

> **Solution**
> > La commande à utiliser est `df -h`, l'option `-h` signifiant "human readable".
> > Autrement dit, cette option donne le résultat en M, G, T et non en B (défaut).
{:.answer}


## Connaître la quantité d'espace disque occupé par un fichier/dossier.

Comme vu précédemment, la commande pour connaître la taille des fichiers présents
dans un dossier est `ls -lh`.

**Question**: Rendez-vous dans le dossier `~/bioinfo/bioinformatique_2023/data/study-cases/Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016`.
Quelle est la quantité d'espace disque occupée par chacun des fichiers présents
dans ce répertoire ? Trier les fichiers du plus volumineux au moins volumineux.

> **Solution:**
> >```
> >$ cd study-cases/Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016
> >
> >$ # Afficher la taille des fichiers
> >$ ls -lh
total 24M
> >-rw-rw-r-- 1 ezechiel ezechiel 1,6M avril  4 20:47 12870_2016_726_MOESM10_ESM.tsv
> >-rw-rw-r-- 1 ezechiel ezechiel 1,4M avril  4 20:47 12870_2016_726_MOESM10_ESM.xlsx
> >-rw-rw-r-- 1 ezechiel ezechiel  37K avril  4 20:47 12870_2016_726_MOESM12_ESM.xlsx
> >-rw-rw-r-- 1 ezechiel ezechiel  18K avril  4 20:47 12870_2016_726_MOESM13_ESM.xlsx
> >-rw-rw-r-- 1 ezechiel ezechiel  20K avril  4 20:47 12870_2016_726_MOESM14_ESM.xlsx
> >-rw-rw-r-- 1 ezechiel ezechiel  17K avril  4 20:47 12870_2016_726_MOESM15_ESM.xlsx
> >-rw-rw-r-- 1 ezechiel ezechiel  16K avril  4 20:47 12870_2016_726_MOESM16_ESM.xlsx
> >-rw-rw-r-- 1 ezechiel ezechiel  17K avril  4 20:47 12870_2016_726_MOESM17_ESM.xlsx
> >-rw-rw-r-- 1 ezechiel ezechiel  30K avril  4 20:47 12870_2016_726_MOESM18_ESM.xlsx
> >-rw-rw-r-- 1 ezechiel ezechiel  15K avril  4 20:47 12870_2016_726_MOESM19_ESM.tsv
> >-rw-rw-r-- 1 ezechiel ezechiel  25K avril  4 20:47 12870_2016_726_MOESM19_ESM.xlsx
> >-rw-rw-r-- 1 ezechiel ezechiel  13M avril  4 20:47 12870_2016_726_MOESM1_ESM.tsv
> >-rw-rw-r-- 1 ezechiel ezechiel 4,6M avril  4 20:47 12870_2016_726_MOESM1_ESM.xlsx
> >-rw-rw-r-- 1 ezechiel ezechiel  18K avril  4 20:47 12870_2016_726_MOESM2_ESM.tsv
> >-rw-rw-r-- 1 ezechiel ezechiel  34K avril  4 20:47 12870_2016_726_MOESM2_ESM.xlsx
> >-rw-rw-r-- 1 ezechiel ezechiel  15K avril  4 20:47 12870_2016_726_MOESM3_ESM.tsv
> >-rw-rw-r-- 1 ezechiel ezechiel  34K avril  4 20:47 12870_2016_726_MOESM3_ESM.xlsx
> >-rw-rw-r-- 1 ezechiel ezechiel 1,9M avril  4 20:47 12870_2016_726_MOESM4_ESM.xlsx
> >-rw-rw-r-- 1 ezechiel ezechiel 386K avril  4 20:47 GSM1388555_WT_0.Gene.rpkm.txt.gz
> >-rw-rw-r-- 1 ezechiel ezechiel 385K avril  4 20:47 GSM1388556_WT_1.Gene.rpkm.txt.gz
> >-rw-rw-r-- 1 ezechiel ezechiel 385K avril  4 20:47 GSM1388557_WT_8.Gene.rpkm.txt.gz
> >-rw-rw-r-- 1 ezechiel ezechiel  729 avril  4 20:47 README.mdcd ../
> >```
{:.answer}

Pour connaître la quantité d'espace disque occupée par un dossier, utiliser
la commande `du`, encore une fois avec l'option `-h`.

**Question**: Afficher la taille des sous-dossiers du dossier `study-cases`.


> **Solution**:
> > ```
> > # Taille des sous-dossiers du dossier study-cases
> > $ du -h ~/bioinfo/bioinformatique_2023/data/study-cases
> > 8,0K	./Escherichia_coli/genome-sequence_allue-guardia_2019
> > 96K	./Escherichia_coli/bacterial-regulons_myers_2013/data/RNA-seq
> > 236K	./Escherichia_coli/bacterial-regulons_myers_2013/data/ChIP-seq
> > 336K	./Escherichia_coli/bacterial-regulons_myers_2013/data
> > 344K	./Escherichia_coli/bacterial-regulons_myers_2013
> > 736K	./Escherichia_coli/genome-metabolome_fuhrer_2017
> > 3,6M	./Escherichia_coli
> > 24M	./Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016
> > 580K	./Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables
> > 2,5M	./Arabidopsis_thaliana/metabo_proteo_Strehmel_2017
> > 27M	./Arabidopsis_thaliana
> > 30M	.
> > ```
{:.answer}



Noter que `find -size` permet de trouver les fichiers en fonction de
leur taille :

```bash
# Trouver les fichiers de plus de 1M
$ find . -size +1M
./.git/objects/pack/pack-ebb930741581bed736361ee821e968dc10c0abef.pack
./Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/data sheet 1.pdf
./Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM10_ESM.tsv
./Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM1_ESM.xlsx
./Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM10_ESM.xlsx
./Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM1_ESM.tsv
./Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM4_ESM.xlsx
```


## Réduire la quantité d'espace disque occupée par un fichier

Il s'agit de compresser un fichier.
Plusieurs outils de compression existent, le plus courant sous unix étant `gzip`
et l'outil de décompression associé `gunzip`.

**Question**: Quelle est la taille du fichier `~/bioinfo/bioinformatique_2023/data/study-cases/Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM1_ESM.tsv` ?
Le compresser avec `gzip`. Quelle est la taille du fichier compressé ?

> **Solution** :
> > ```
> > $ cd ~/Documents/2024/cours/bioinformatique_2023/data/study-cases/Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016
> > $ # Taille du fichier 12870_2016_726_MOESM1_ESM.tsv
> > $ ls -lh 12870_2016_726_MOESM1_ESM.tsv
> > -rw-rw-r-- 1 ezechiel ezechiel 13M avril  4 20:47 12870_2016_726_MOESM1_ESM.tsv
> > $ # Le fichier fait 13M.
> >
> > $ # Compression du fichier.
> > $ # Attention : par défaut, gzip compresse directement le fichier sans créer de copie
> > $ # On utilise l'option -c pour écrire la sortie sur la sortie standard et > pour rédiriger la sortie standard dans un fichier.
> > $ gzip -c 12870_2016_726_MOESM1_ESM.tsv > 12870_2016_726_MOESM1_ESM.tsv.gz
> >
> > $ # Taille du fichier compressé
> > $ ls -lh 12870_2016_726_MOESM1_ESM.tsv.gz
> > -rw-rw-r-- 1 ezechiel ezechiel 2.5M Feb  1 15:44 12870_2016_726_MOESM1_ESM.tsv.gz
> > $ # Le fichier fait 2.5M, soit un taux de compression de 80%.
> > ```
{:.answer}

## Réduire le nombre de fichiers présents sur un disque et compression d'un dossier.

Réduire le nombre de fichiers présents sur un disque consiste à créer une *archive*
d'un dossier.
Cette archive va contenir, en un seul fichier, tous les fichiers présents initialement
dans le dossier.

### Création d'une archive

La commande pour créer une archive est `tar`.

**Syntaxe**: `tar cvf <TARNAME> <SOURCE>`.

`tar` est une commande un peu spéciale puisque certaines options sont accessibles
sans utiliser le caractère `-`.

Voici la signification des options utilisées :

- `c` mode création d'archive
- `f <OUTPUT>` nom du fichier de sortie

Il est également possible d'utiliser l'option `-z` (`tar czf`) pour compresser
l'archive à la volée.

**Exemple**:

```bash
$ # Création d'une archive pour le dossier Arabidopsis_thaliana
$ tar cf Arabidopsis_thaliana.tar Arabidopsis_thaliana

$ # Idem mais en compressant l'archive à la volée.
$ tar czf Arabidopsis_thaliana.tar.gz Arabidopsis_thaliana
```

On peut également utiliser l'option (`-v, --verbose`) pour afficher le nom des
fichiers au fur et à mesure qu'ils sont ajoutés à l'archive) :

```bash
$ # Idem mais en compressant l'archive à la volée.
$ tar cvzf Arabidopsis_thaliana.tar.gz Arabidopsis_thaliana
Arabidopsis_thaliana/
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised Suppl Table S4 Root exudate proteome.xlsx
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised_Suppl_Table_S4_Root_exudate_proteome.tsv
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised Suppl Table S2 Root Exudates JL140617.xlsx
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised Suppl Table S3 Analytical Characterization.xlsx
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised_Suppl_Table_S1_Roots.tsv
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised_Suppl_Table_S3_Analytical_Characterization.tsv
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised Suppl Table S1 Roots.xlsx
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised_Suppl_Table_S2_Root_Exudates_JL140617.tsv
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/README.md
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/data sheet 1.pdf
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM2_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM19_ESM.tsv
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM14_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM10_ESM.tsv
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/README.md
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM1_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM16_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM15_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM17_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM3_ESM.tsv
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/GSM1388555_WT_0.Gene.rpkm.txt.gz
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM12_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM13_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM18_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/GSM1388557_WT_8.Gene.rpkm.txt.gz
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM10_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM2_ESM.tsv
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM1_ESM.tsv
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/GSM1388556_WT_1.Gene.rpkm.txt.gz
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM4_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM19_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM3_ESM.xlsx
```

Par ailleurs, l'option `--exclude <PATTERN>` permet d'exclude certains fichiers de l'archive.

**Exemple:**

```bash
$ # Création d'une archive du répertoire study-cases en ne tenant pas compte du dossier .git
$ tar cvzf ~/study-cases.tar.gz --exclude ".git" ~/study-cases
```

### Extraction d'une archive

On utilise également l'outil `tar` pour extraire le contenu d'une archive.

**Syntaxe**: `tar xvf <TARNAME> <SOURCE>`.

Ici, on utilise l'option `-x` (*extract*) à la place de l'option `-c` (*create*).
Si l'archive est compressée, on utilise l'option `-z` pour indique au programme
qu'il faudra décompresser l'archive.

**Exemple**:

```bash
# Extraction d'une archive compressée en mode verbeux (verbose)
$ tar xvzf Arabidopsis_thaliana.tar.gz
Arabidopsis_thaliana/
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised Suppl Table S4 Root exudate proteome.xlsx
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised_Suppl_Table_S4_Root_exudate_proteome.tsv
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised Suppl Table S2 Root Exudates JL140617.xlsx
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised Suppl Table S3 Analytical Characterization.xlsx
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised_Suppl_Table_S1_Roots.tsv
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised_Suppl_Table_S3_Analytical_Characterization.tsv
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised Suppl Table S1 Roots.xlsx
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/Strehmel revised suppl tables/Revised_Suppl_Table_S2_Root_Exudates_JL140617.tsv
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/README.md
Arabidopsis_thaliana/metabo_proteo_Strehmel_2017/data sheet 1.pdf
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM2_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM19_ESM.tsv
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM14_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM10_ESM.tsv
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/README.md
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM1_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM16_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM15_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM17_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM3_ESM.tsv
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/GSM1388555_WT_0.Gene.rpkm.txt.gz
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM12_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM13_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM18_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/GSM1388557_WT_8.Gene.rpkm.txt.gz
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM10_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM2_ESM.tsv
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM1_ESM.tsv
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/GSM1388556_WT_1.Gene.rpkm.txt.gz
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM4_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM19_ESM.xlsx
Arabidopsis_thaliana/transcripto_proteo_metabo_Liang_2016/12870_2016_726_MOESM3_ESM.xlsx
```
