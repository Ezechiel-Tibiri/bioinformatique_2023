# Introduction à la programmation en bioinformatique
## installer Cygwin sous Windows
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
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py
```
### Installez Jupyter en exécutant la commande suivante dans le terminal :
```bash
pip install jupyter
# Installez un noyau Bash en exécutant la commande suivante :
pip install bash_kernel
# Exécutez la commande suivante pour ajouter le noyau Bash à Jupyter : 
python -m bash_kernel.install
```
### Exécutez Jupyter Notebook en utilisant la commande suivante dans le terminal :

```bash
jupyter notebook
# Accédez à Jupyter Notebook en utilisant un navigateur web à l'adresse `http://localhost:8888/`.
```
## Les commandes de base de LINUX
Vous avez [ici](https://github.com/Ezechiel-Tibiri/GNU-LINUX/blob/main/cmd_linux.md)
 les commandes de bases LINUX
