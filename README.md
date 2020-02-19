# TP2_BURDET_CHENIOUR

### Exercice 1. Variables d’environnement

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

## Programmation Bash

```mkdir script```
```PATH=$PATH:/$HOME/script``` ajouter le chemin vers script dans PATH

### Exercice 2. Contrôle de mot de passe

```touch testpwd.sh```
```vim testpwd.sh```
```chmod u+x testpwd.sh```
```./testpwd.sh```
Le script : 
```
#!/bin/bash
PASSWORD="pa33word";
read -s -p "Entrer votre mot de passe:" userpass
if [ $PASSWORD = $userpass ]
then
    echo -e "\nSuper\n"
else
    echo -e "\nPerdu\n"
fi
```

### Exercice 3. Expressions rationnelles

```touch isnumber.sh```
```vim isnumber.sh```
```chmod u+x isnumber.sh```
```./isnumber.sh 1.1```
Le script
```
#!/bin/bash
function is_number()
{
    re='^[+-]?[0-9]+([.][0-9]+)?$'
    if ! [[ $1 =~ $re ]] ; then
        echo "ok"
        return 1
    else
        echo "no"
        return 0
    fi
}

is_number $1
echo $?
```

### Exercice 4. Contrôle d’utilisateur

```touch usertest.sh```
```vim usertest.sh```
```chmod u+x usertest.sh```
```./usertest.sh serveur```
Le script
```
#!/bin/bash
if [ $1 != "" ]
then
    if getent passwd $1 > /dev/null 2>&1; then
        echo "Il existe"
    else
        echo "Il n'existe pas"
    fi
else
    echo "Utilisation: $0 nom_utilisateur"
fi
```

### Exercice 5. Factorielle

```touch facto.sh```
```vim facto.sh```
```chmod u+x facto.sh```
```./facto.sh 5```
Le script
```
#!/bin/bash
n=$1
res=1
while [ $n -gt 0 ]
do
    res=$((res*n))
    n=$((n-1))
done
echo $res
```

### Exercice 6. Le juste prix

```touch justeprix.sh```
```vim justeprix.sh```
```chmod u+x justeprix.sh```
```./justeprix.sh```
Le script
```
#!/bin/bash
r=$(( ( RANDOM % 1000 )  + 1 ))
val=0

while [ $val -ne $r ]
do
    read -p "Entrez une valeure entre 1 et 1000 : " val
    if [ $val -lt $r ]
    then
        echo "C’est plus !"
    elif [ $val -gt $r ]
    then
        echo "C’est moins !"
    fi
done
echo "Gagné !"
```

### Exercice 7. Statistiques

1. et 2.
```touch statistiques.sh```
```vim statistiques.sh```
```chmod u+x statistiques.sh```
```./statistiques.sh 100 200 9```
Le script
```
#!/bin/bash
declare -a tab

i=0
while [ "$1" != "" ]
do
    tab[$i]=$1
    shift
    i=$((i+1))
done

moy=0
min=${tab[0]}
max=${tab[0]}

j=0
while [ $j -lt $i ]
do
    moy=$((moy+${tab[$j]}))
    
    if [ $min -gt ${tab[$j]} ]
    then
        min=${tab[$j]}
    fi
    if [ $max -lt ${tab[$j]} ]
    then
        max=${tab[$j]}
    fi
    j=$((j+1))
done

moy=$((moy/i))

echo -e "Moyenne : $moy\nMaximum : $max\nMinimum : $min"
```

3.