# Gestionnaire de CV

![Illustration de l'auteur](./img/pharallaxe.png)

Cette application permet de centraliser et d'organiser des CVs. L'utilisateur doit créer un fichier Excel nommé `tableur_cv.xlsx` où il va inscrire les noms des entreprises et des prénoms dans les colonnes. Les personnes inscriront un "X" majuscule dans les cases qui correspondent à leur prénom et à la ligne de l'entreprise pour indiquer l'association.

L'application lit ce tableau et pour chaque entreprise, elle crée un dossier portant le nom de l'entreprise. Ensuite, elle copie les CV correspondants dans ce dossier et génère un fichier prenoms.txt listant les prénoms associés.

## Licence
Ce projet est sous licence [Apache](./LICENSE).

## Fonctionnalités

- **Création de dossiers** : Génère un dossier pour chaque entreprise mentionnée dans le fichier Excel.
- **Fichier `prenoms.txt`** : Crée un fichier `prenoms.txt` dans chaque dossier d'entreprise, listant les prénoms associés.
- **Copie des CVs** : Copie les fichiers CV dans les dossiers d'entreprises basés sur les prénoms marqués avec un `X` dans le fichier Excel.

## Prérequis

Avant de commencer, assurez-vous que vous avez les éléments suivants :

- **Python 3.x** : Vérifiez que Python est installé sur votre système. Vous pouvez le télécharger depuis le site officiel de Python.
- **Bibliothèque Python : `openpyxl`** : Cette bibliothèque est nécessaire pour manipuler des fichiers Excel.

## Installation de Python 3.x et `openpyxl`

### Étape 1 : Télécharger Python

1. **Visitez le site officiel de Python** :
   - Allez sur [python.org](https://www.python.org/downloads/) et téléchargez la dernière version de Python 3.x pour votre système d'exploitation (Windows, macOS, ou Linux).

### Étape 2 : Installer Python

#### Pour Windows :

1. **Exécutez l'installateur** :
   - Localisez le fichier téléchargé (généralement dans le dossier *Téléchargements*) et double-cliquez dessus.
   
2. **Configurer l'installation** :
   - Lors de l'installation, cochez la case "Add Python to PATH" pour faciliter l'accès à Python depuis la ligne de commande.
   
3. **Terminer l'installation** :
   - Cliquez sur "Install Now" et suivez les instructions à l'écran.

4. **Vérifier l'installation** :
   - Ouvrez une invite de commande et tapez `python --version` pour vous assurer que Python est installé correctement.

#### Pour macOS :

1. **Exécutez l'installateur** :
   - Double-cliquez sur le fichier .pkg téléchargé.

2. **Suivez les instructions** :
   - Acceptez les termes et conditions, puis cliquez sur "Installer".

3. **Vérifier l'installation** :
   - Ouvrez le Terminal et tapez `python3 --version` pour vérifier que Python est installé.

#### Pour Linux :

1. **Utiliser le gestionnaire de paquets** :
   - Ouvrez un terminal et exécutez les commandes suivantes selon votre distribution :
     - Pour Ubuntu/Debian :
       ```bash
       sudo apt-get update
       sudo apt-get install python3
       ```
     - Pour Fedora :
       ```bash
       sudo dnf install python3
       ```

2. **Vérifier l'installation** :
   - Tapez `python3 --version` dans le terminal.

### Étape 3 : Installer la bibliothèque `openpyxl`

Une fois Python installé, vous devez installer la bibliothèque `openpyxl`. Cela peut être fait en utilisant `pip`, qui est généralement installé avec Python.

1. **Ouvrir une invite de commande ou un terminal**.
2. **Exécuter la commande suivante** :
```bash
pip install openpyxl
```

## Structure des Dossiers
Avant d'exécuter le script, assurez-vous que votre structure de fichiers ressemble à ceci :

```bash
├── CV/
│   ├── Prenom1.pdf
│   ├── Prenom2.pdf
│   ├── Prenom3.pdf
├── tableur_cv.xlsx
└── script.py
```

Le dossier CV contient les fichiers CV, nommés suivant le format Prenom.pdf.
Le fichier tableur_cv.xlsx contient les informations d'entreprises et prénoms.


## Format du fichier Excel
Le fichier Excel tableur_cv.xlsx doit suivre ce format :

|                  | Prénom 1 | Prénom 2 | Prénom 3 |
|------------------|----------|----------|----------|
| **Entreprise 1** |    X     |          |          |
| **Entreprise 2** |          |    X     |     X    |
| **Entreprise 3** |    X     |          |     X    |
| **Entreprise 4** |    X     |    X     |     X    |


- Première colonne : Noms des entreprises.
- Première ligne : Prénoms.
- Cases avec X : Indiquent les CV à inclure pour l'entreprise correspondante.


## Utilisation
Placez le fichier Excel nommé tableur_cv.xlsx dans le répertoire du script. Ce fichier doit contenir les entreprises et les prénoms comme décrit ci-dessus.
Placez tous les CVs dans un dossier nommé CV avec des noms de fichiers correspondant au format Prenom.pdf ou Nom.pdf (en tout cas le même intitulé que dans l'en-tête de colonne du fichier Excel.)

Exécutez le script Python :
```bash
python script.py
```
Les dossiers des entreprises seront créés dans un répertoire Entreprises à la racine du projet. Chaque dossier contiendra un fichier prenoms.txt et les copies des CVs correspondants.
Exemple de structure après exécution
Après l'exécution du script, la structure des dossiers devrait ressembler à ceci :

```bash
├── Entreprises/
│   ├── Entreprise 1/
│   │   ├── prenoms.txt
│   │   ├── CV_Prénom1.pdf
│   │   └── CV_Prénom3.pdf
│   ├── Entreprise 2/
│   │   ├── prenoms.txt
│   │   ├── CV_Prénom2.pdf
│   │   └── CV_Prénom3.pdf
│   └── Entreprise 3/
│       ├── prenoms.txt
│       └── CV_Prénom1.pdf

``` 

## Notes
Assurez-vous que les noms des CVs correspondent au format Nom.pdf tel que décrit.
Le script vérifie l'existence des fichiers de CV avant de les copier et génère un message d'erreur si un fichier est introuvable.
