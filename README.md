# Introduction à la programmation en bioinformatique

## 1. Intaller UBUNTU 22.04 LTS sous Windows 10+

* Pour Windows 10. Vous pouvez installer très rapidement un shell Linux. Voici quelques liens pour y arriver :
  * [Installer le shell Bash Linux sous Windows 10 avec WSL](https://www.youtube.com/watch?v=CyG16N3GJWo), 2020.
  * How to install Windows Subsystem for Linux (WSL) on Windows 10, 2019.
  * [Everything You Can Do With Windows 10’s New Bash Shell](https://www.howtogeek.com/265900/everything-you-can-do-with-windows-10s-new-bash-shell/), 2018.
  ### 1.1. Installez Bash pour Windows en suivant les instructions
 ```
 sudo apt update && sudo apt upgrade -y
 ```
 
```bash
 sudo apt install python3 python3-pip python3-dev python3-setuptools
```

### 1.2. Installez Jupyter Notebook en exécutant la commande suivante

```bash
sudo pip3 install jupyter
```
### 1.3. Vérifiez que l'installation a réussi en exécutant la commande suivante 

```bash
jupyter notebook
```
### 1.4.  Installer le kernel bash

```bash
pip install bash_kernel
python3 -m pip install --upgrade pip
python3 -m pip install bash_kernel
```

```bash
jupyter notebook
```

## 2. installer Cygwin sous Windows

Vous pouvez installer Cygwin sous Windows en suivant ces étapes :

    1. Téléchargez le fichier d'installation de **Cygwin** depuis le site web de Cygwin à l'adresse https://cygwin.com/install.html.

    2. Double-cliquez sur le fichier d'installation pour lancer l'assistant d'installation.

    3. Choisissez un répertoire d'installation pour **Cygwin**. Par défaut, il est installé dans C:\cygwin.

    4. Choisissez un serveur de miroir **Cygwin** pour télécharger les paquets. Il est recommandé de choisir un serveur proche de votre emplacement géographique.

    5. Sélectionnez les paquets à installer en utilisant le bouton "Sélectionner les paquets" dans l'assistant d'installation. Il est recommandé de sélectionner les paquets de base, tels que bash, gcc, make et openssh.

    6. Cliquez sur le bouton "Installer" pour démarrer le processus d'installation.

    7. Une fois l'installation terminée, lancez le terminal Cygwin en cliquant sur le raccourci "Cygwin Terminal" sur le bureau ou dans le menu Démarrer.


##  Installation de Jupyter Notebook sous Cygwin
    Installer Jupyter Notebook sur Cygwin en suivant ces étapes :
    1. Assurez-vous que Python est installé sur votre système Cygwin en exécutant la commande `python` dans le terminal.
    
### Installez pip en exécutant la commande suivante dans le terminal :
    
```bash 
curl -k https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py
# /usr/bin/python3.9.exe -m pip install --upgrade pip
```
PS : Lancer cette commande si et seulement si la précedente commande ne marche pas
<span style="color:red">**/usr/bin/python3.9.exe -m pip install --upgrade pip**</span>

### Installez Jupyter en exécutant la commande suivante dans le terminal :

```bash
pip install --no-binary :all: jupyter
# Installez un noyau Bash en exécutant la commande suivante :
pip install bash_kernel
# Exécutez la commande suivante pour ajouter le noyau Bash à Jupyter : 
python -m bash_kernel.install
```
PS: le repertoire partagé entre Windows et Cygwin est **/cygdrive/c/Users/votre-nom-utilisateur/Documents**

### Exécutez Jupyter Notebook en utilisant la commande suivante dans le terminal :

```bash
jupyter notebook
# Accédez à Jupyter Notebook en utilisant un navigateur web à l'adresse `http://localhost:8888/`.
```
## Les commandes de base de LINUX

Vous avez [ici](https://github.com/Ezechiel-Tibiri/GNU-LINUX/blob/main/cmd_linux.md)
 les commandes de bases LINUX
