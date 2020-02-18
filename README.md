# TP2_BURDET_CHENIOUR

## Exercice 1. Variables d’environnement

1. ```/home/serveur/.bash_history``` est le dossier bash on l'on trouve les commandes tapées par l’utilisateur.
2. ```$HOME``` est la variable qui permet à la commande ```cd``` de nous ramener dans notre répertoire personnel.
3. 
```$LANG``` détermine la langue que les logiciels utilisent pour communiquer avec l'utilisateur.
```$PWD``` Le répertoire de travail courant de l'interpréteur de commande.
```$SHELL``` L'interpréteur de commande préféré de l'utilisateur tel qu'il est défini dans le fichier « /etc/passwd » . 
```$OLDPWD``` contient le chemin de la dernière commande ```cd```.
```_``` contient le chemin « /usr/bin/printenv » .
4. ```MY_VAR="ls";``` et pour vérifier qu'elle existe, nous pouvons l'afficher ```echo $MY_VAR```
5. ```bash``` est un interpréteur de langage de commande compatible sh qui exécute les commandes lues à partir de l'entrée standard ou d'un fichier. bash intègre également des fonctionnalités utiles des shells Korn et C (ksh et csh).
```echo $MY_VAR``` n'affiche rien car MY_VAR n'existe pas car nous ne sommes plus dans la session initiale. 
Pour y revenir utiliser ```exit```
6. ```export MY_VAR="ls";``` et pour vérifier qu'elle existe, nous pouvons l'afficher ```printenv $MY_VAR```
Puis en tapant ```bash```, notre variable MY_VAR existe toujours.
7. ```export NOMS="BURDET CHENIOUR";``` ```printenv NOMS``` la valeur est correct
8. ```echo "Bonjour à vous deux, $NOMS !"```
9. ```unset``` détruit la variable alors que donner une valeur vide met juste une valeur vide dans la variable.
10. ```echo "\$HOME = $HOME"```

