# Cours bioinformatique session 2024
Bienvenue au cours d'introduction à la Bioinformatique. Vous trouverez sur ce dépôt toutes les informations et ressources nécessaires. A noter que la présence physique à ce cours est plus que nécessaire voir obligatoire.
---
## Intervenants
* Ezechiel B. TIBIRI, INERA/CNRST, ezechiel.tibiri@ujkz.bf <br/> 

## Prérequis
Dans un premier temps, nous vous suggérons d'acquérir les bases de la biologie moléculaire ainsi que de la génomique et du séquençage d'ADN.

*Temps estimé : 4 heures.

---
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
  
 ```bash
sudo apt update && sudo apt upgrade -y
sudo apt install python3 python3-pip python3-dev python3-setuptools
sudo apt install git
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
---
## 2. Installation de Cygwin sous Windows
Si vous n'avez pas pu installer UBUNTU sous Windows, vous pouvez installer Cygwin pour exécuter les commandes Unix. Pour installer Cygwin, vous pouvez suivre les étapes suivantes :

2.1. Téléchargement et installation de Cygwin :

Téléchargez le fichier d'installation de Cygwin depuis le site web officiel de Cygwin à l'adresse https://cygwin.com/install.html. Double-cliquez sur le fichier d'installation pour lancer l'assistant d'installation. Choisissez un répertoire d'installation pour Cygwin. Par défaut, il est installé dans C:\cygwin. Choisissez un serveur de miroir Cygwin pour télécharger les paquets. Il est recommandé de choisir un serveur proche de votre emplacement géographique. Sélectionnez les paquets à installer en utilisant le bouton "Sélectionner les paquets" dans l'assistant d'installation. Il est recommandé de sélectionner les paquets de base, tels que `bash`, `gcc`, `make` et `openssh`. Cliquez sur le bouton "Installer".
