# Le Guide Ultime du Shell Scripting : De Zéro à Héros

<!-- TOC -->
- [Le Guide Ultime du Shell Scripting : De Zéro à Héros](#le-guide-ultime-du-shell-scripting--de-zéro-à-héros)
  - [TL;DR](#tldr-résumé-rapide)
  - [Bonnes pratiques essentielles](#bonnes-pratiques-essentielles)
  - [Introduction](#introduction)
    - [Qu'est-ce qu'un Shell ?](#quest-ce-quun-shell-)
    - [Votre Premier Script](#votre-premier-script)
    - [Commentaires](#commentaires)
  - [Les Bases](#les-bases)
    - [Variables et Types de Données](#variables-et-types-de-données)
    - [Opérations de Base](#opérations-de-base)
    - [Structures de Contrôle](#structures-de-contrôle)
    - [Boucles](#boucles)
  - [Fonctions](#fonctions)
    - [Syntaxe de Base](#syntaxe-de-base)
    - [Arguments](#arguments)
    - [Retour de Valeurs](#retour-de-valeurs)
    - [Portée des Variables](#portée-des-variables)
  - [Manipulation de Fichiers et Répertoires](#manipulation-de-fichiers-et-répertoires)
    - [Vérifications](#vérifications)
    - [Lecture/Écriture](#lectureécriture)
    - [Opérations sur les Fichiers](#opérations-sur-les-fichiers)
    - [Permissions](#permissions)
  - [Expressions Régulières et Traitement de Texte](#expressions-régulières-et-traitement-de-texte)
    - [Grep](#grep)
    - [Sed](#sed)
    - [Awk](#awk)
    - [Exemples Pratiques](#exemples-pratiques)
  - [Bonnes Pratiques et Gestion des Erreurs](#bonnes-pratiques-et-gestion-des-erreurs)
    - [Structure de Base](#structure-de-base)
    - [Gestion des Erreurs](#gestion-des-erreurs)
    - [Logging et Debugging](#logging-et-debugging)
    - [Tests et Validation](#tests-et-validation)
  - [Sécurité](#sécurité)
    - [Protection des Données](#protection-des-données)
    - [Gestion des Permissions](#gestion-des-permissions)
    - [Prévention des Injections](#prévention-des-injections)
    - [Bonnes Pratiques de Sécurité](#bonnes-pratiques-de-sécurité)
  - [Patterns Avancés et Optimisation](#patterns-avancés-et-optimisation)
    - [Optimisation des Performances](#optimisation-des-performances)
    - [Traitement Parallèle](#traitement-parallèle)
    - [Gestion des Ressources](#gestion-des-ressources)
    - [Patterns de Débogage](#patterns-de-débogage)
  - [TL;DR et Bonnes Pratiques](#tldr-et-bonnes-pratiques)
    - [TL;DR](#tldr)
    - [Bonnes Pratiques Essentielles](#bonnes-pratiques-essentielles)
<!-- /TOC -->

## TL;DR (Résumé Rapide)

Le shell scripting est un outil puissant pour automatiser des tâches sous Unix/Linux. Points essentiels :
- Commencer par #!/bin/bash
- Utiliser des variables avec $
- Gérer les erreurs avec set -e
- Documenter son code
- Tester avant de déployer
- Sécuriser les entrées utilisateur

## Bonnes Pratiques Essentielles

1. Structure et Organisation
   - Toujours inclure un shebang (#!/bin/bash)
   - Organiser le code en fonctions
   - Utiliser des noms explicites pour les variables et fonctions
   - Commenter le code de manière pertinente

2. Sécurité
   - Ne jamais stocker de données sensibles en clair
   - Toujours valider les entrées utilisateur
   - Utiliser des guillemets autour des variables
   - Définir des permissions restrictives sur les fichiers sensibles

3. Débogage et Maintenance
   - Utiliser set -e pour arrêter le script en cas d'erreur
   - Implémenter un système de logging
   - Tester le script avec des données variées
   - Documenter les dépendances et prérequis

4. Performance
   - Éviter les appels externes inutiles
   - Utiliser les commandes internes quand possible
   - Optimiser les boucles
   - Nettoyer les ressources temporaires

5. Portabilité
   - Éviter les dépendances non standard
   - Spécifier les chemins complets
   - Tester sur différents environnements
   - Documenter les hypothèses système

## Introduction

Le shell scripting est un moyen puissant d'automatiser des tâches sur les systèmes Unix/Linux. Ce guide vous accompagnera des concepts les plus basiques aux techniques avancées.

## Qu'est-ce qu'un Shell ?

Le shell est l'interpréteur de commandes qui fait l'interface entre l'utilisateur et le système d'exploitation. Il permet d'exécuter des commandes et d'automatiser des tâches via des scripts.

## Votre Premier Script

Pour créer votre premier script shell, vous avez besoin d'un éditeur de texte. Commençons par le célèbre "Hello World" :

```bash
#!/bin/bash
echo "Hello World!"
```

Explications :
- La première ligne (#!) s'appelle le "shebang". Elle indique quel interpréteur utiliser
- 'echo' est une commande qui affiche du texte

Pour exécuter ce script :
1. Sauvegardez-le avec l'extension .sh (exemple: hello.sh)
2. Rendez-le exécutable avec la commande :
```bash
chmod +x hello.sh
```
3. Exécutez-le :
```bash
./hello.sh
```

## Commentaires

Les commentaires sont essentiels pour documenter votre code :

```bash
# Ceci est un commentaire sur une ligne

: '
Ceci est un commentaire
sur plusieurs lignes
'
```

## Variables : Les Bases

Les variables permettent de stocker des données temporairement :

```bash
# Déclaration de variable
nom="Alex"
age=25

# Utilisation des variables
echo "Bonjour $nom, vous avez $age ans"

# Attention : pas d'espace autour du =
# Correct :
ville="Paris"
# Incorrect :
ville = "Paris"    # Ceci causera une erreur
```

### Types de Variables Simples

1. Chaînes de caractères :
```bash
message="Bonjour tout le monde"
```

2. Nombres :
```bash
age=25
prix=19.99
```

3. Booléens (simulés) :
```bash
est_actif=1    # vrai
est_inactif=0  # faux
```

### Afficher des Variables

Plusieurs façons d'afficher des variables :

```bash
nom="Alex"
# Méthode simple
echo $nom
# Méthode avec accolades (recommandée)
echo ${nom}
# Avec du texte autour
echo "Bonjour ${nom}!"
```

### Saisie Utilisateur

Pour rendre vos scripts interactifs :

```bash
echo "Quel est votre nom ?"
read nom_utilisateur
echo "Bonjour ${nom_utilisateur}!"
```

## Opérations de Base

### Opérations Arithmétiques

```bash
# Addition
resultat=$((5 + 3))
# Soustraction
difference=$((10 - 5))
# Multiplication
produit=$((4 * 3))
# Division
quotient=$((15 / 3))
# Modulo (reste de la division)
reste=$((17 % 5))
```

### Concaténation de Chaînes

```bash
prenom="Alex"
nom="Martin"
nom_complet="${prenom} ${nom}"
echo $nom_complet    # Affiche : Alex Martin
```

## Structures de Contrôle

### Les Conditions (if/then/else)

Les conditions permettent à ton script de prendre des décisions. La syntaxe de base est :

```bash
# Structure simple
if [ condition ]; then
    # code à exécuter si vrai
fi

# Avec else
if [ condition ]; then
    # code si vrai
else
    # code si faux
fi

# Avec elif (else if)
if [ condition1 ]; then
    # code si condition1 est vraie
elif [ condition2 ]; then
    # code si condition2 est vraie
else
    # code si aucune condition n'est vraie
fi
```

Exemples pratiques :

```bash
# Vérifier si un fichier existe
if [ -f "config.txt" ]; then
    echo "Le fichier config.txt existe"
else
    echo "Le fichier config.txt n'existe pas"
fi

# Vérifier un âge
age=25
if [ $age -lt 18 ]; then
    echo "Mineur"
elif [ $age -lt 60 ]; then
    echo "Adulte"
else
    echo "Senior"
fi
```

### Opérateurs de Comparaison

Pour les nombres :
```bash
- -eq : égal à                      # equal
- -ne : différent de                # not equal
- -lt : inférieur à                 # Inferior To
- -le : inférieur ou égal à         # Inferior or equal to
- -gt : supérieur à                 # Greater than
- -ge : supérieur ou égal à         # Greater or Equal to
```

Pour les chaînes :
- = : égal à
- != : différent de
- -z : chaîne vide
- -n : chaîne non vide

Exemple :
```bash
nombre=42
if [ $nombre -gt 10 ] && [ $nombre -lt 50 ]; then
    echo "Le nombre est entre 10 et 50"
fi

nom="Alex"
if [ "$nom" = "Alex" ]; then
    echo "Bonjour Alex!"
fi
```

## Les Boucles

### Boucle For

La boucle for permet de répéter une action un nombre défini de fois :

```bash
# Boucle simple
for i in 1 2 3 4 5; do
    echo "Nombre: $i"
done

# Boucle avec séquence
for i in {1..5}; do
    echo "Itération $i"
done

# Boucle sur des fichiers
for fichier in *.txt; do
    echo "Traitement de $fichier"
done
```

### Boucle While

La boucle while s'exécute tant qu'une condition est vraie :

```bash
# Compteur simple
compteur=1
while [ $compteur -le 5 ]; do
    echo "Compteur: $compteur"
    ((compteur++))
done

# Lecture d'un fichier ligne par ligne
while read ligne; do
    echo "Ligne lue: $ligne"
done < fichier.txt
```

### Boucle Until

La boucle until s'exécute jusqu'à ce qu'une condition soit vraie :

```bash
nombre=1
until [ $nombre -gt 5 ]; do
    echo "Nombre: $nombre"
    ((nombre++))
done
```

## Break et Continue

- break : sort de la boucle
- continue : passe à l'itération suivante

Exemple :
```bash
for i in {1..10}; do
    if [ $i -eq 5 ]; then
        continue    # Saute l'itération 5
    fi
    if [ $i -eq 8 ]; then
        break       # Sort de la boucle à 8
    fi
    echo "Nombre: $i"
done
```

## Case (Switch)

Le case permet de gérer plusieurs conditions de manière élégante :

```bash
fruit="pomme"
case $fruit in
    "pomme")
        echo "C'est une pomme"
        ;;
    "banane"|"orange")
        echo "C'est un fruit jaune ou orange"
        ;;
    *)
        echo "Fruit inconnu"
        ;;
esac
```

## Les Fonctions

Les fonctions permettent d'organiser ton code en blocs réutilisables. Elles rendent ton script plus modulaire et plus facile à maintenir.

### Syntaxe de Base

Il existe deux façons de déclarer une fonction :

```bash
# Méthode 1
function dire_bonjour() {
    echo "Bonjour!"
}

# Méthode 2
dire_aurevoir() {
    echo "Au revoir!"
}

# Appel des fonctions
dire_bonjour
dire_aurevoir
```

### Arguments dans les Fonctions

Les fonctions peuvent recevoir des arguments :

```bash
function saluer() {
    local nom=$1    # Premier argument
    local age=$2    # Deuxième argument
    echo "Bonjour $nom, tu as $age ans!"
}

# Appel avec arguments
saluer "Alex" 25
```

Variables spéciales dans les fonctions :
- $1, $2, etc. : arguments positionnels
- $# : nombre d'arguments
- $@ : tous les arguments sous forme de liste
- $* : tous les arguments sous forme de chaîne

### Retour de Valeurs

Les fonctions peuvent retourner des valeurs avec 'return' :

```bash
function additionner() {
    local a=$1
    local b=$2
    return $((a + b))
}

# Utilisation
additionner 5 3
resultat=$?    # $? contient la valeur de retour
echo "Résultat : $resultat"
```

Note : 'return' ne peut renvoyer que des nombres entre 0 et 255.
Pour retourner des chaînes ou des valeurs plus complexes :

```bash
function obtenir_info() {
    echo "Ceci est le résultat"    # Echo pour "retourner" une chaîne
}

resultat=$(obtenir_info)    # Capture la sortie de la fonction
```

## Manipulation de Fichiers et Répertoires

### Vérifications de Base

```bash
# Vérifier si un fichier existe
if [ -f "config.txt" ]; then
    echo "Le fichier existe"
fi

# Vérifier si un répertoire existe
if [ -d "/tmp/mon_dossier" ]; then
    echo "Le répertoire existe"
fi

# Vérifier les permissions
if [ -r "fichier.txt" ]; then    # Lecture
    echo "Fichier lisible"
fi
if [ -w "fichier.txt" ]; then    # Écriture
    echo "Fichier modifiable"
fi
if [ -x "script.sh" ]; then      # Exécution
    echo "Fichier exécutable"
fi
```

### Lecture et Écriture de Fichiers

```bash
# Lire un fichier ligne par ligne
while IFS= read -r ligne; do
    echo "Lu: $ligne"
done < "fichier.txt"

# Écrire dans un fichier
echo "Nouvelle ligne" > fichier.txt    # Écrase le contenu
echo "Autre ligne" >> fichier.txt      # Ajoute à la fin

# Créer un fichier avec plusieurs lignes
cat << EOF > nouveau_fichier.txt
Ligne 1
Ligne 2
Ligne 3
EOF
```

### Manipulation de Répertoires

```bash
# Créer un répertoire
mkdir -p dossier/sous_dossier    # -p crée les parents si nécessaire

# Se déplacer dans un répertoire
cd dossier

# Obtenir le chemin actuel
chemin_actuel=$(pwd)

# Lister les fichiers
for fichier in *; do
    if [ -f "$fichier" ]; then
        echo "Fichier trouvé: $fichier"
    fi
done
```

### Opérations sur les Fichiers

```bash
# Copier des fichiers
cp source.txt destination.txt
cp -r dossier_source/ dossier_destination/    # Récursif pour les dossiers

# Déplacer/renommer
mv ancien.txt nouveau.txt

# Supprimer
rm fichier.txt
rm -r dossier/    # Récursif pour les dossiers

# Créer un lien symbolique
ln -s fichier_source lien_symbolique
```

## Expressions Régulières (Regex) et Traitement de Texte

Les regex sont des motifs de recherche puissants pour manipuler du texte. En shell, elles sont principalement utilisées avec grep, sed et awk.

### Grep : Recherche de Motifs

#### Les Bases de Grep

```bash
# Recherche simple
grep "motif" fichier.txt

# Options courantes
grep -i "motif" fichier.txt    # Insensible à la casse
grep -v "motif" fichier.txt    # Inverse la recherche
grep -r "motif" .              # Recherche récursive
grep -l "motif" *.txt          # Liste uniquement les fichiers
grep -n "motif" fichier.txt    # Affiche les numéros de ligne
```

#### Motifs Regex de Base

```bash
# Début et fin de ligne
grep "^debut" fichier.txt    # Lignes commençant par "debut"
grep "fin$" fichier.txt      # Lignes finissant par "fin"

# Caractères spéciaux
grep "ch[aeiou]t" fichier.txt    # chat, chet, chit, etc.
grep "n[0-9]" fichier.txt        # n suivi d'un chiffre
grep "bo*n" fichier.txt          # bn, bon, boon, etc.
```

### Sed : Éditeur de Flux

#### Remplacement de Texte

```bash
# Remplacer la première occurrence
sed 's/ancien/nouveau/' fichier.txt

# Remplacer toutes les occurrences sur chaque ligne
sed 's/ancien/nouveau/g' fichier.txt

# Remplacer et sauvegarder dans le fichier
sed -i 's/ancien/nouveau/g' fichier.txt

# Remplacer avec backup
sed -i.bak 's/ancien/nouveau/g' fichier.txt
```

#### Opérations Avancées avec Sed

```bash
# Supprimer des lignes
sed '/motif/d' fichier.txt           # Supprime les lignes contenant "motif"
sed '2d' fichier.txt                 # Supprime la ligne 2
sed '2,5d' fichier.txt              # Supprime les lignes 2 à 5

# Ajouter du texte
sed '2i\Nouvelle ligne' fichier.txt  # Insère avant la ligne 2
sed '2a\Nouvelle ligne' fichier.txt  # Insère après la ligne 2

# Multiple commandes
sed -e 's/ancien/nouveau/' -e 's/autre/nouveau/' fichier.txt
```

### Awk : Traitement de Texte Avancé

#### Bases d'Awk

```bash
# Structure de base
awk '{print $1}' fichier.txt         # Affiche première colonne
awk '{print $1, $3}' fichier.txt     # Affiche colonnes 1 et 3
awk -F: '{print $1}' /etc/passwd     # Spécifie le séparateur

# Avec conditions
awk '$3 > 100 {print $1}' fichier.txt    # Lignes où colonne 3 > 100
```

#### Exemples Pratiques d'Awk

```bash
# Calculer la somme d'une colonne
awk '{sum += $1} END {print sum}' fichier.txt

# Compter les occurrences
awk '{count[$1]++} END {for (word in count) print word, count[word]}' fichier.txt

# Formater la sortie
awk '{printf "Nom: %-20s Age: %d\n", $1, $2}' fichier.txt
```

### Exemples Pratiques Combinés

#### Script de Traitement de Logs

```bash
#!/bin/bash

# Exemple de traitement de logs Apache
function analyser_logs() {
    echo "Top 5 des adresses IP :"
    awk '{print $1}' access.log | sort | uniq -c | sort -nr | head -n 5

    echo -e "\nRequêtes HTTP avec erreur 404 :"
    grep "HTTP/1.1\" 404" access.log | cut -d'"' -f2 | sort | uniq -c | sort -nr
}

# Extraction d'emails d'un fichier
function extraire_emails() {
    grep -E -o "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" "$1"
}

# Nettoyage de données
function nettoyer_donnees() {
    # Supprime les lignes vides et les commentaires
    sed '/^$/d; /^#/d' "$1" |
    # Convertit en minuscules
    tr '[:upper:]' '[:lower:]' |
    # Supprime les espaces en début/fin de ligne
    sed 's/^[ \t]*//; s/[ \t]*$//'
}
```

#### Validation de Données

```bash
#!/bin/bash

# Validation d'un numéro de téléphone (format français)
function valider_telephone() {
    if [[ $1 =~ ^0[1-9]([-. ]?[0-9]{2}){4}$ ]]; then
        echo "Numéro valide"
    else
        echo "Numéro invalide"
    fi
}

# Validation d'une adresse email
function valider_email() {
    if [[ $1 =~ ^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$ ]]; then
        echo "Email valide"
    else
        echo "Email invalide"
    fi
}
```

## Bonnes Pratiques et Gestion des Erreurs

### Structure de Base d'un Script Robuste

```bash
#!/bin/bash
set -e          # Arrête le script si une commande échoue
set -u          # Erreur si variable non définie
set -o pipefail # Erreur si une commande dans un pipe échoue

# Définition des variables globales
readonly CONFIG_FILE="/etc/app/config.yml"
readonly LOG_DIR="/var/log/monapp"

# Fonction de logging
log() {
    local level=$1
    shift
    echo "[$(date +'%Y-%m-%d %H:%M:%S')] [$level] $*" >> "${LOG_DIR}/app.log"
}

# Fonction de nettoyage
cleanup() {
    log "INFO" "Nettoyage en cours..."
    # Actions de nettoyage ici
}

# Gestion des erreurs
trap cleanup EXIT
trap 'log "ERROR" "Ligne $LINENO: Commande \"$BASH_COMMAND\" échouée avec code $?"' ERR
```

### Gestion des Erreurs

#### Vérification des Entrées

```bash
function verifier_arguments() {
    if [ $# -lt 2 ]; then
        echo "Erreur: Nombre insuffisant d'arguments"
        echo "Usage: $0 <source> <destination>"
        exit 1
    fi
}

function verifier_fichier() {
    local fichier=$1
    if [ ! -f "$fichier" ]; then
        log "ERROR" "Le fichier $fichier n'existe pas"
        exit 1
    fi
    if [ ! -r "$fichier" ]; then
        log "ERROR" "Le fichier $fichier n'est pas lisible"
        exit 1
    fi
}
```

#### Codes de Retour

```bash
# Définition des codes d'erreur
readonly E_SUCCESS=0
readonly E_ARGS=1
readonly E_FILE=2
readonly E_PERM=3
readonly E_CONFIG=4

function traiter_fichier() {
    local fichier=$1
    
    # Vérifications
    [ -z "$fichier" ] && return $E_ARGS
    [ ! -f "$fichier" ] && return $E_FILE
    [ ! -r "$fichier" ] && return $E_PERM
    
    # Traitement
    if grep -q "pattern" "$fichier"; then
        return $E_SUCCESS
    else
        return $E_CONFIG
    fi
}
```

### Logging et Debugging

#### Système de Logging Avancé

```bash
# Niveaux de log
declare -r DEBUG=0
declare -r INFO=1
declare -r WARN=2
declare -r ERROR=3

function log() {
    local level=$1
    local message=$2
    local timestamp=$(date +'%Y-%m-%d %H:%M:%S')
    
    case $level in
        $DEBUG) level_str="DEBUG" ;;
        $INFO)  level_str="INFO"  ;;
        $WARN)  level_str="WARN"  ;;
        $ERROR) level_str="ERROR" ;;
    esac
    
    echo "[$timestamp] [$level_str] $message" >> "$LOG_FILE"
}

# Utilisation
log $INFO "Démarrage du script"
log $ERROR "Échec de l'opération"
```

#### Mode Debug

```bash
# Activation du mode debug
DEBUG=false

function debug() {
    if [ "$DEBUG" = true ]; then
        echo "DEBUG: $*" >&2
    fi
}

function verbose_execution() {
    if [ "$DEBUG" = true ]; then
        set -x
    fi
    "$@"
    if [ "$DEBUG" = true ]; then
        set +x
    fi
}
```

### Tests et Validation

#### Tests Unitaires Simples

```bash
function test_fonction() {
    local resultat
    local attendu
    
    # Test 1
    resultat=$(ma_fonction "test")
    attendu="résultat attendu"
    if [ "$resultat" != "$attendu" ]; then
        echo "Test 1 échoué: obtenu '$resultat', attendu '$attendu'"
        return 1
    fi
    
    echo "Tous les tests ont réussi"
    return 0
}
```

### Documentation

#### En-tête de Script

```bash
#!/bin/bash
#
# Nom: mon_script.sh
# Description: Description courte du script
# Usage: ./mon_script.sh [options] <arguments>
#
# Options:
#   -h, --help     Affiche l'aide
#   -v, --verbose  Mode verbeux
#   -d, --debug    Mode debug
#
# Auteur: Ton Nom
# Date: $(date +'%Y-%m-%d')
# Version: 1.0
```

### Exemple de Script Complet

```bash
#!/bin/bash
set -euo pipefail

# Configuration
readonly SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
readonly CONFIG_FILE="${SCRIPT_DIR}/config.yml"
readonly LOG_FILE="/var/log/monapp/app.log"

# Initialisation
function init() {
    if [ ! -d "$(dirname "$LOG_FILE")" ]; then
        mkdir -p "$(dirname "$LOG_FILE")"
    fi
    
    if [ ! -f "$CONFIG_FILE" ]; then
        log $ERROR "Fichier de configuration manquant"
        exit $E_CONFIG
    fi
}

# Point d'entrée principal
function main() {
    log $INFO "Démarrage du script"
    init
    
    # Logique principale ici
    
    log $INFO "Script terminé avec succès"
}

# Exécution
main "$@"
```

## Sécurité et Meilleures Pratiques Avancées

### Sécurisation des Scripts

#### Protection des Données Sensibles

```bash
# NE JAMAIS faire ça
PASSWORD="mon_mot_de_passe"    # Dangereux !

# À la place, utiliser des variables d'environnement
echo "Entrez le mot de passe : "
read -s PASSWORD    # -s pour masquer la saisie

# Ou utiliser un fichier de configuration sécurisé
source /chemin/vers/config.secret
chmod 600 /chemin/vers/config.secret
```

#### Gestion des Permissions

```bash
# Restreindre les permissions des fichiers sensibles
umask 077    # Seul le propriétaire peut lire/écrire les nouveaux fichiers

# Vérifier les permissions avant l'exécution
function verifier_permissions() {
    if [ -g "$1" ] || [ -G "$1" ]; then
        echo "Erreur: Le fichier ne doit pas avoir de permissions groupe"
        exit 1
    fi
}
```

### Injection de Commandes

#### Prévention

```bash
# DANGEREUX
nom_fichier="$1"
rm $nom_fichier    # Vulnérable à l'injection

# SÉCURISÉ
rm -- "$nom_fichier"    # -- empêche l'interprétation des options

# Validation des entrées
function valider_entree() {
    local input=$1
    if [[ ! $input =~ ^[a-zA-Z0-9_.-]+$ ]]; then
        echo "Entrée invalide"
        exit 1
    fi
}
```

### Meilleures Pratiques Avancées

#### Modularisation du Code

```bash
# Structure recommandée
project/
├── bin/
│   └── main.sh
├── lib/
│   ├── logger.sh
│   ├── config.sh
│   └── utils.sh
├── conf/
│   └── settings.conf
└── tests/
    └── test_utils.sh

# Dans main.sh
#!/bin/bash
source "$(dirname "$0")/../lib/logger.sh"
source "$(dirname "$0")/../lib/config.sh"
```

#### Gestion de la Configuration

```bash
# config.sh
declare -A CONFIG

function charger_config() {
    local config_file=$1
    while IFS='=' read -r key value; do
        # Ignorer les commentaires et lignes vides
        [[ $key =~ ^[[:space:]]*# ]] && continue
        [[ -z $key ]] && continue
        
        # Nettoyer et stocker
        key=$(echo "$key" | sed 's/^[[:space:]]*//;s/[[:space:]]*$//')
        value=$(echo "$value" | sed 's/^[[:space:]]*//;s/[[:space:]]*$//')
        CONFIG[$key]=$value
    done < "$config_file"
}
```

#### Gestion des Processus

```bash
# Gestion des processus en arrière-plan
function demarrer_service() {
    local pid_file="/var/run/monapp.pid"
    
    # Vérifier si déjà en cours
    if [ -f "$pid_file" ]; then
        if kill -0 "$(cat "$pid_file")" 2>/dev/null; then
            echo "Service déjà en cours"
            return 1
        fi
    fi
    
    # Démarrer le service
    mon_service.sh &
    echo $! > "$pid_file"
}

# Gestion du nettoyage
function arreter_service() {
    local pid_file="/var/run/monapp.pid"
    if [ -f "$pid_file" ]; then
        kill "$(cat "$pid_file")"
        rm "$pid_file"
    fi
}
```

#### Verrouillage de Fichiers

```bash
# Implémentation d'un verrou
LOCK_FILE="/tmp/monapp.lock"

function obtenir_verrou() {
    if ! mkdir "$LOCK_FILE" 2>/dev/null; then
        echo "Une autre instance est en cours"
        exit 1
    fi
    trap 'rm -rf "$LOCK_FILE"' EXIT
}

# Utilisation
obtenir_verrou
# ... code principal ...
```

#### Monitoring et Performance

```bash
function monitorer_ressources() {
    local debut=$SECONDS
    local mem_debut=$(free -m | awk 'NR==2{print $3}')
    
    # Exécution de la commande
    "$@"
    local statut=$?
    
    # Calcul des métriques
    local duree=$((SECONDS - debut))
    local mem_fin=$(free -m | awk 'NR==2{print $3}')
    local mem_utilisee=$((mem_fin - mem_debut))
    
    log $INFO "Durée: ${duree}s, Mémoire: ${mem_utilisee}MB"
    return $statut
}
```

## Patterns Avancés et Optimisation en Shell Scripting

### Optimisation des Performances

#### Utilisation des Commandes Internes

Les commandes internes sont plus rapides que les commandes externes :

```bash
# À ÉVITER
if [ $(echo "Bonjour" | grep -c "B") -eq 1 ]; then
    echo "Trouvé"
fi

# PRÉFÉRER
if [[ "Bonjour" == *B* ]]; then
    echo "Trouvé"
fi
```

#### Éviter l'Utilisation Inutile de cat

```bash
# À ÉVITER
cat fichier.txt | grep "motif"

# PRÉFÉRER
grep "motif" fichier.txt
```

### Traitement Parallèle

```bash
# Traitement séquentiel classique
for fichier in *.txt; do
    traiter_fichier "$fichier"
done

# Traitement parallèle avec xargs
ls *.txt | xargs -n 1 -P 4 traiter_fichier
```

### Patterns de Débogage

```bash
# Activation du mode debug
DEBUG=true

function debug() {
    if [ "$DEBUG" = true ]; then
        echo "DEBUG: $*" >&2
    fi
}

# Mode verbose pour le débogage
function execution_verbose() {
    if [ "$DEBUG" = true ]; then
        set -x
    fi
    "$@"
    if [ "$DEBUG" = true ]; then
        set +x
    fi
}
```

### Gestion des Ressources

```bash
# Utilisation d'un verrou pour éviter les exécutions simultanées
LOCK_FILE="/tmp/mon_script.lock"

function obtenir_verrou() {
    if ! mkdir "$LOCK_FILE" 2>/dev/null; then
        echo "Une autre instance est en cours"
        exit 1
    fi
    trap 'rm -rf "$LOCK_FILE"' EXIT
}

# Surveillance des ressources
function surveiller_ressources() {
    local debut=$SECONDS
    local mem_debut=$(free -m | awk 'NR==2{print $3}')
    
    "$@"
    local statut=$?
    
    local duree=$((SECONDS - debut))
    local mem_fin=$(free -m | awk 'NR==2{print $3}')
    echo "Durée: ${duree}s, Mémoire: $((mem_fin - mem_debut))MB"
    return $statut
}
```

### Manipulation Efficace des Chaînes

```bash
# À ÉVITER
resultat=$(echo "Bonjour Monde" | sed 's/Monde/Shell/')

# PRÉFÉRER
texte="Bonjour Monde"
resultat=${texte/Monde/Shell}
```

### Optimisation des Tests Conditionnels

```bash
# Utilisation de [[ pour les tests
if [[ "$variable" == "valeur" && "$autre" != "test" ]]; then
    echo "Condition remplie"
fi

# Tests d'existence de fichiers optimisés
if [[ -f "$fichier" && -r "$fichier" ]]; then
    echo "Fichier existe et est lisible"
fi
```