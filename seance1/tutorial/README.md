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
> > $ cd study-cases
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
