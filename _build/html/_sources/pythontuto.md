# Initiation à Python

Ce document présente une introduction à Python, couvrant les concepts de base, les types de données, les structures de contrôle, les fonctions, et l'importation de modules.

---

## 1. Qu'est-ce que Python ?

Python est un langage de programmation interprété, polyvalent et facile à apprendre. Il est largement utilisé pour :
- Le développement web.
- L'analyse de données.
- L'intelligence artificielle.
- Le calcul scientifique.

Python se distingue par sa syntaxe simple, qui facilite la lecture et la maintenance du code.

**Exemple** : Un programme simple pour afficher un message.  
``` python
print("Bienvenue dans l'apprentissage de Python!")
```

**Exercice** : Écrivez un programme Python pour afficher votre prénom.

---
## 2. Types de données primitifs

Les types de données primitifs en Python sont les types de base qui permettent de stocker et manipuler des valeurs fondamentales. Les principaux types primitifs incluent :  

1. **int** : utilisé pour représenter des nombres entiers, positifs ou négatifs.  
2. **float** : utilisé pour représenter des nombres décimaux (nombres à virgule flottante).  
3. **str** : utilisé pour représenter des chaînes de caractères.  
4. **bool** : utilisé pour représenter des valeurs booléennes, qui peuvent être soit `True` soit `False`.  

### Explications et exemples pour chaque type

#### **int (entiers)**
Un entier est un nombre sans partie décimale.  
**Exemple** :  
```python
x = 42  # int
print(x)           # Affiche : 42
print(type(x))     # Affiche : <class 'int'>
```

#### **float (nombres décimaux)**
Un float est un nombre contenant une partie décimale.  
**Exemple** :  
``` python
y = 3.14159  # float
print(y)             # Affiche : 3.14159
print(type(y))       # Affiche : <class 'float'>
```

#### **str (chaînes de caractères)**
Une chaîne de caractères est une séquence de lettres, chiffres ou symboles, encadrée par des guillemets simples ou doubles.  
**Exemple** :  
``` python
z = "Python est génial!"  # str
print(z)             # Affiche : Python est génial!
print(type(z))       # Affiche : <class 'str'>
```

#### **bool (valeurs booléennes)**
Une valeur booléenne représente une condition qui est soit vraie (`True`), soit fausse (`False`).  
**Exemple** :  
``` python
is_fun = True  # bool
print(is_fun)           # Affiche : True
print(type(is_fun))     # Affiche : <class 'bool'>
```

### Manipulation combinée des types primitifs

Il est possible d'utiliser différents types primitifs dans un même programme. Voici un exemple combinant les quatre types :  
``` python
# Déclaration des variables
x = 7                 # int
y = 2.5               # float
z = "Apprendre Python"  # str
is_valid = True       # bool

# Affichage des types et des valeurs
print(f"Valeur de x : {x}, Type : {type(x)}")
print(f"Valeur de y : {y}, Type : {type(y)}")
print(f"Valeur de z : {z}, Type : {type(z)}")
print(f"Valeur de is_valid : {is_valid}, Type : {type(is_valid)}")
```

### Exercice

1. Déclarez une variable pour chaque type de données primitif mentionné.
2. Affichez à la fois la valeur et le type de chaque variable.

---

## 3. Opérations mathématiques

Python prend en charge plusieurs opérations mathématiques de base et avancées, qui sont utilisées pour manipuler des nombres. Ces opérations incluent :  

1. **Addition (`+`)** : pour additionner deux nombres.  
2. **Soustraction (`-`)** : pour soustraire un nombre d'un autre.  
3. **Multiplication (`*`)** : pour multiplier deux nombres.  
4. **Division (`/`)** : pour diviser un nombre par un autre (retourne un float).  
5. **Modulo (`%`)** : pour obtenir le reste d'une division entière.  
6. **Puissance (`**`)** : pour élever un nombre à une puissance donnée.  
7. **Division entière (`//`)** : pour obtenir le quotient d'une division entière (sans le reste).  

### Explications et exemples

#### **Opérations de base**
**Exemple** :  
``` python
a = 10
b = 3

print(a + b)  # Addition : Affiche 13
print(a - b)  # Soustraction : Affiche 7
print(a * b)  # Multiplication : Affiche 30
print(a / b)  # Division : Affiche 3.3333333333333335
```

#### **Modulo et division entière**
**Exemple** :  
``` python
a = 10
b = 3

print(a % b)  # Modulo : Affiche 1 (reste de la division)
print(a // b) # Division entière : Affiche 3 (quotient entier)
```

#### **Puissance**
**Exemple** :  
``` python
a = 2
b = 5

print(a ** b)  # Puissance : Affiche 32 (2^5)
```

### Utilisation combinée des opérations

Les opérations peuvent être combinées pour effectuer des calculs complexes :  
``` python
x = 5
y = 2

# Calculs combinés
resultat = (x ** 2 + y) / (x - y)
print(f"Le résultat du calcul est : {resultat}")
```

### Exercice

1. Écrivez un programme pour demander deux nombres à l'utilisateur.
2. Calculez et affichez la somme, la différence, le produit, le quotient et le reste de leur division.



## 4. Types de données composites

Les types de données composites permettent de stocker et de manipuler des collections d'éléments. Python propose plusieurs types composites, chacun ayant ses propres caractéristiques :  

1. **list** : une collection ordonnée et modifiable.  
2. **tuple** : une collection ordonnée mais immuable.  
3. **dict** : une collection non ordonnée de paires clé-valeur.  
4. **set** : une collection non ordonnée d'éléments uniques.  

### Explications et exemples pour chaque type

#### **list (listes)**
Une liste est une collection ordonnée d'éléments. Les listes sont modifiables : vous pouvez ajouter, supprimer ou modifier des éléments.  
**Exemple** :  

``` python
# Déclaration d'une liste
ma_liste = [10, 20, 30, 40, 50]

# Accès aux éléments
print(ma_liste[0])    # Premier élément : Affiche 10
print(ma_liste[-1])   # Dernier élément : Affiche 50

# Modification d'un élément
ma_liste[2] = 35
print(ma_liste)       # Affiche : [10, 20, 35, 40, 50]

# Ajout d'un élément
ma_liste.append(60)
print(ma_liste)       # Affiche : [10, 20, 35, 40, 50, 60]
```

#### **tuple (tuples)**
Un tuple est une collection ordonnée comme une liste, mais il est immuable : ses éléments ne peuvent pas être modifiés après sa création.  
**Exemple** :  

``` python
# Déclaration d'un tuple
mon_tuple = (1, 2, 3, 4, 5)

# Accès aux éléments
print(mon_tuple[1])    # Deuxième élément : Affiche 2

# Tentative de modification (provoque une erreur)
# mon_tuple[1] = 10     # Erreur : TypeError
```

#### **dict (dictionnaires)**
Un dictionnaire est une collection de paires clé-valeur. Chaque clé doit être unique, et les valeurs peuvent être de tout type.  
**Exemple** :  

``` python
# Déclaration d'un dictionnaire
mon_dict = {"nom": "Python", "version": 3.10, "langage": "programming"}

# Accès à une valeur via une clé
print(mon_dict["nom"])        # Affiche : Python

# Modification d'une valeur
mon_dict["version"] = 3.11
print(mon_dict)               # Affiche : {'nom': 'Python', 'version': 3.11, 'langage': 'programming'}

# Ajout d'une nouvelle clé-valeur
mon_dict["créateur"] = "Guido van Rossum"
print(mon_dict)               # Affiche toutes les clés et leurs valeurs
```

#### **set (ensembles)**
Un ensemble est une collection non ordonnée contenant des éléments uniques. Les doublons sont automatiquement supprimés.  
**Exemple** :  

``` python
# Déclaration d'un ensemble
mon_set = {1, 2, 3, 4, 4, 5}

print(mon_set)   # Affiche : {1, 2, 3, 4, 5} (les doublons sont supprimés)

# Ajout d'un élément
mon_set.add(6)
print(mon_set)   # Affiche : {1, 2, 3, 4, 5, 6}

# Suppression d'un élément
mon_set.remove(3)
print(mon_set)   # Affiche : {1, 2, 4, 5, 6}
```

### Comparaison des types composites

| Type    | Ordonné | Modifiable | Doublons autorisés | Exemple                              |
|---------|---------|------------|--------------------|--------------------------------------|
| `list`  | Oui     | Oui        | Oui                | `[1, 2, 3]`                          |
| `tuple` | Oui     | Non        | Oui                | `(1, 2, 3)`                          |
| `dict`  | Non     | Oui        | Non (pour les clés) | `{"a": 1, "b": 2}`                   |
| `set`   | Non     | Oui        | Non                | `{1, 2, 3}`                          |

### Exercices

1. Créez une liste contenant cinq nombres entiers et calculez leur somme.  
2. Créez un tuple contenant les noms de trois de vos matières préférées. Essayez d'accéder au deuxième élément.  
3. Déclarez un dictionnaire avec trois clés : `"nom"`, `"âge"`, et `"ville"`. Ajoutez une quatrième clé `"pays"` avec une valeur de votre choix.  
4. Créez un ensemble avec des nombres de 1 à 10, mais incluez des doublons. Affichez l'ensemble après la déclaration.  
## 5. Bloc `if`, `else`, `elif`

Les blocs conditionnels permettent d'exécuter du code en fonction de certaines conditions logiques. Ils sont basés sur des expressions qui évaluent à `True` ou `False`.

### Structure générale
La structure d'un bloc conditionnel en Python est la suivante :  
- Le mot-clé `if` vérifie une première condition.
- Le mot-clé `elif` (optionnel) permet de vérifier des conditions alternatives.
- Le mot-clé `else` (optionnel) exécute un bloc si aucune condition précédente n'est vraie.

### Syntaxe
Chaque bloc doit être indenté pour indiquer les instructions associées.

**Syntaxe générale** :  

``` python
if condition1:
    # Bloc exécuté si condition1 est vraie
elif condition2:
    # Bloc exécuté si condition1 est fausse et condition2 est vraie
else:
    # Bloc exécuté si aucune condition n'est vraie
```

### Exemple 1 : Vérification de la nature d'un nombre

``` python
x = 10

if x > 0:
    print("x est positif")
elif x == 0:
    print("x est zéro")
else:
    print("x est négatif")
```

### Exemple 2 : Vérification d'une catégorie d'âge
``` python
age = 25

if age < 18:
    print("Mineur")
elif 18 <= age <= 65:
    print("Adulte")
else:
    print("Sénior")
```

### Comparateurs et opérateurs logiques
Les blocs conditionnels utilisent des comparateurs et opérateurs pour formuler des conditions :  
- **Comparateurs** :  
  - `==` : égal à  
  - `!=` : différent de  
  - `<`, `>`, `<=`, `>=` : comparaisons numériques  

- **Opérateurs logiques** :  
  - `and` : toutes les conditions doivent être vraies.  
  - `or` : au moins une condition doit être vraie.  
  - `not` : inverse la valeur logique d'une condition.

**Exemple avec plusieurs conditions** :  
``` python
score = 85

if score > 90:
    print("Excellent")
elif score > 70 and score <= 90:
    print("Bon")
else:
    print("Peut mieux faire")
```

### Exercices

1. Écrivez un programme qui vérifie si un nombre entier est **pair** ou **impair**.  
2. Demandez à l'utilisateur son âge et affichez un message pour indiquer s'il est **mineur**, **adulte**, ou **sénior**.  
3. Écrivez un programme qui prend une note (sur 100) et affiche :  
   - "A" si la note est supérieure ou égale à 90,  
   - "B" si elle est entre 80 et 89,  
   - "C" si elle est entre 70 et 79,  
   - "F" sinon.  

## 6. Boucles `for` et `while`

Les boucles permettent de répéter l'exécution d'un bloc de code tant que certaines conditions sont remplies ou pour un nombre déterminé d'itérations. Python propose principalement deux types de boucles : `for` et `while`.

### Boucle `for`

La boucle `for` est utilisée pour itérer sur des éléments d'une séquence, comme une liste, un tuple, une chaîne de caractères ou une plage de nombres. La structure de base est la suivante :

**Syntaxe générale** :  
``` python
for variable in séquence:
    # Bloc de code à exécuter pour chaque élément de la séquence
```

**Exemple** :  
``` python
for i in range(5):
    print(i)
```
Cet exemple utilise la fonction `range(5)`, qui génère les nombres de 0 à 4. La boucle `for` itère sur ces valeurs et les affiche successivement.

### La fonction `range()`
La fonction `range()` est utilisée pour générer une séquence de nombres. Elle peut être utilisée de différentes manières :
- `range(stop)` : génère de 0 à `stop-1`.
- `range(start, stop)` : génère de `start` à `stop-1`.
- `range(start, stop, step)` : génère de `start` à `stop-1`, en incrémentant de `step`.

**Exemple** :  
``` python
for i in range(2, 10, 2):
    print(i)
```
Cet exemple affiche les nombres pairs de 2 à 8.

### Boucle `while`

La boucle `while` continue de s'exécuter tant que la condition spécifiée est `True`. Elle est utile pour les situations où le nombre d'itérations n'est pas connu à l'avance.

**Syntaxe générale** :  
``` python
while condition:
    # Bloc de code à exécuter tant que la condition est vraie
    instruction(s) de modification de la condition
```

**Exemple** :  
``` python
n = 0
while n < 5:
    print(n)
    n += 1
```
Cet exemple initialise `n` à 0 et incrémente `n` à chaque itération. La boucle continue jusqu'à ce que `n` atteigne 5, moment où la condition `n < 5` devient `False` et la boucle s'arrête.

### Utilisation de la boucle `while` avec une condition de sortie

Il est possible d'utiliser des instructions comme `break` pour quitter la boucle prématurément et `continue` pour passer à l'itération suivante sans exécuter le reste du code dans la boucle.

**Exemple avec `break`** :  
``` python
x = 0
while x < 10:
    if x == 5:
        break  # Arrête la boucle lorsque x est égal à 5
    print(x)
    x += 1
```

**Exemple avec `continue`** :  
``` python
for i in range(6):
    if i % 2 == 0:
        continue  # Passe à l'itération suivante si i est pair
    print(i)
```

### Exercices

1. Utilisez une boucle `for` pour afficher les carrés des nombres de 1 à 10.
2. Écrivez un programme qui utilise une boucle `while` pour afficher les valeurs de 10 à 1 en décrémentant de 1 à chaque itération.
3. Créez un programme qui affiche tous les nombres pairs de 0 à 20 en utilisant une boucle `while`.

## 7. Fonctions

Les fonctions en Python permettent de regrouper des blocs de code afin de les rendre réutilisables et modulaires. Elles facilitent la structuration du code et la réduction de la duplication.

### Déclaration d'une fonction
Pour définir une fonction en Python, on utilise le mot-clé `def` suivi du nom de la fonction, des parenthèses et de deux points. Les instructions de la fonction sont indentées.

**Syntaxe générale** :  
``` python
def nom_fonction(paramètre1, paramètre2, ...):
    # Bloc de code
    return résultat
```

### Exemple : Fonction simple
``` python
def carre(x):
    return x ** 2

print(carre(5))  # Affiche 25
```
La fonction `carre` prend un paramètre `x` et retourne son carré. Le mot-clé `return` permet de renvoyer un résultat à l'appelant de la fonction.

### Types de fonctions

#### 1. Fonction sans paramètres
Une fonction qui ne prend aucun paramètre peut être définie pour exécuter un bloc de code de manière autonome.

**Exemple** :  
``` python
def salutation():
    print("Bonjour, bienvenue dans le monde de Python!")

salutation()  # Affiche "Bonjour, bienvenue dans le monde de Python!"
```

#### 2. Fonction avec paramètres
Les fonctions peuvent prendre un ou plusieurs paramètres qui sont utilisés à l'intérieur de la fonction.

**Exemple** :  
``` python
def addition(a, b):
    return a + b

print(addition(3, 4))  # Affiche 7
```

#### 3. Fonction avec valeur de retour
Une fonction peut retourner un résultat à l'aide du mot-clé `return`. Cela permet de capturer le résultat dans une variable ou de l'utiliser directement.

**Exemple** :  
``` python
def multiplication(x, y):
    return x * y

resultat = multiplication(4, 5)
print(resultat)  # Affiche 20
```

#### 4. Fonction avec paramètres par défaut
Il est possible de spécifier des valeurs par défaut pour certains paramètres. Si ces paramètres ne sont pas fournis lors de l'appel de la fonction, les valeurs par défaut sont utilisées.

**Exemple** :  
``` python
def saluer(nom="inconnu"):
    print(f"Bonjour, {nom}!")

saluer("Alice")  # Affiche "Bonjour, Alice!"
saluer()         # Affiche "Bonjour, inconnu!"
```

#### 5. Fonction avec paramètres variables
Pour accepter un nombre variable d'arguments, Python utilise les symboles `*args` pour les arguments positionnels et `**kwargs` pour les arguments nommés.

**Exemple avec `*args`** :  
``` python
def somme(*args):
    return sum(args)

print(somme(1, 2, 3, 4))  # Affiche 10
```

**Exemple avec `**kwargs`** :  
``` python
def afficher_détails(**kwargs):
    for clé, valeur in kwargs.items():
        print(f"{clé}: {valeur}")

afficher_détails(nom="Alice", age=25, ville="Paris")
# Affiche :
# nom: Alice
# age: 25
# ville: Paris
```

### Utilisation de la fonction `lambda`
Les fonctions lambda sont des fonctions anonymes définies à l'aide du mot-clé `lambda`. Elles peuvent prendre plusieurs arguments mais n'ont pas de nom et ne contiennent généralement qu'une seule expression.

**Exemple** :  
``` python
carre_lambda = lambda x: x ** 2
print(carre_lambda(6))  # Affiche 36
```

### Appel de la fonction
Pour appeler une fonction, il suffit de spécifier son nom et de passer les arguments requis.

**Exemple** :  
``` python
def saluer(nom):
    print(f"Bonjour, {nom}!")

saluer("Bob")  # Affiche "Bonjour, Bob!"
```

### Exercice

1. Écrivez une fonction qui prend un nom comme paramètre et affiche un message de bienvenue.
2. Créez une fonction qui calcule la factorielle d'un nombre donné.
3. Écrivez une fonction qui prend une liste de nombres en paramètres et retourne la somme des nombres pairs de cette liste.
4. Utilisez une fonction lambda pour créer une fonction qui double un nombre et testez-la avec quelques valeurs.

## 8. Importation de modules

L'importation de modules en Python permet d'étendre les fonctionnalités du langage et d'utiliser des bibliothèques de fonctions et de classes déjà développées. Cela permet d'accéder à des outils puissants pour le calcul, la manipulation de données, la création de graphiques, etc.

### Importation de modules standards

Python est livré avec une bibliothèque standard qui contient de nombreux modules intégrés, tels que `math`, `random`, `datetime`, etc. Pour utiliser ces modules, il suffit de les importer à l'aide de la commande `import`.

**Syntaxe générale** :  
``` python
import nom_du_module
```

### Exemple d'importation et d'utilisation de `math`

Le module `math` fournit des fonctions mathématiques avancées, comme la racine carrée, les fonctions trigonométriques et les constantes mathématiques telles que `math.pi`.

**Exemple** :  
``` python
import math

print(math.sqrt(16))  # Affiche 4.0, la racine carrée de 16
print(math.pi)        # Affiche la valeur de pi (approximativement 3.14159)
```

### Importation de fonctions spécifiques

Pour importer une fonction spécifique d'un module, on peut utiliser la syntaxe `from ... import ...`. Cela permet de ne pas avoir à préfixer le nom du module à chaque utilisation de la fonction.

**Syntaxe générale** :  
``` python
from nom_du_module import fonction
```

**Exemple** :  
``` python
from math import sqrt, pi

print(sqrt(25))  # Affiche 5.0
print(pi)        # Affiche 3.14159
```

### Importation avec alias

Il est possible d'importer un module sous un alias pour simplifier son utilisation, surtout lorsqu'il a un nom long ou lorsqu'on souhaite éviter des conflits de noms.

**Syntaxe générale** :  
``` python
import nom_du_module as alias
```

**Exemple** :  
``` python
import numpy as np

# Utilisation de la fonction `array` de `numpy`
tableau = np.array([1, 2, 3, 4])
print(tableau)  # Affiche [1 2 3 4]
```

### Exemple d'importation de modules tiers

Python permet également d'importer des modules tiers qui ne font pas partie de la bibliothèque standard. Ces modules doivent être installés à l'aide de `pip`, le gestionnaire de paquets de Python.

**Installation avec `pip`** :  
``` bash
pip install nom_du_module
```

**Exemple** : Importation du module `pandas` pour la manipulation de données.
``` python
import pandas as pd

# Création d'un DataFrame simple
data = {'Nom': ['Alice', 'Bob', 'Charlie'], 'Age': [25, 30, 35]}
df = pd.DataFrame(data)
print(df)
```

### Importation de tous les éléments d'un module

Il est possible d'importer tous les éléments d'un module en utilisant la syntaxe `from ... import *`, mais cette pratique est déconseillée car elle peut entraîner des conflits de noms et rendre le code moins lisible.

**Syntaxe** :  
``` python
from nom_du_module import *
```

**Exemple** :  
``` python
from math import *

print(sqrt(49))  # Affiche 7.0
print(factorial(5))  # Affiche 120
```

### Exercice

1. Importez le module `random` et utilisez-le pour générer un nombre aléatoire entre 1 et 100.
2. Importez la fonction `sin` du module `math` et affichez le sinus de 45 degrés (en radians).
3. Utilisez le module `datetime` pour afficher la date et l'heure actuelles.

---










