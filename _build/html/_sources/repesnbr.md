# Représentation des nombres en calcul scientifique
Dans ce chapitre, nous explorons comment les nombres sont représentés dans les ordinateurs, les impacts de ces représentations sur les calculs numériques, et les erreurs qu'elles peuvent générer. Les exemples pratiques en Python illustrent ces concepts.

```  python
# Importation des bibliothèques nécessaires
import numpy as np
import matplotlib.pyplot as plt
``` 

---

## Introduction : La représentation des nombres
Les ordinateurs utilisent des approximations pour représenter les nombres réels. Cette limitation est due à la capacité finie de la mémoire. Cela entraîne des erreurs d'arrondi, des pertes de précision, et parfois des résultats inattendus lors des calculs complexes.

- **Limite fondamentale** : Un nombre réel, en raison de sa nature infinie en base 10, est représenté de manière tronquée ou arrondie en base 2.
- **Conséquences** :
  - **Erreurs d'arrondi** : Lorsqu'un nombre ne peut être représenté exactement, il est arrondi à la valeur la plus proche.
  - **Erreurs d'annulation** : Ces erreurs se produisent lorsqu'on soustrait deux nombres presque égaux, ce qui amplifie l'effet des approximations.

**Exemple : Effet d'une erreur d'annulation**  
```  python
# Exemple d'erreur d'annulation
a = 1.0000000001
b = 1.0000000000
c = a - b
print(f"Résultat attendu : {1e-10}, Résultat calculé : {c}")
``` 

---

## Approximation des constantes mathématiques

### Le nombre d'Euler $e$
Le nombre d'Euler $e$ est défini par :

$$
e = \lim_{n \to \infty} \left( 1 + \frac{1}{n} \right)^n
$$

En pratique, $e$ est calculé pour une valeur finie de $n$. Cela introduit des erreurs liées à la précision numérique.

#### Exemple : Approximations numériques de $e$
```  python
# Approximation du nombre e
print('n \t\t e_n \t\t\t erreur relative')
for i in range(1, 16):
    n = 10 ** i
    e_n = (1 + 1/n) ** n
    erreur = abs(e_n - np.e) / np.e
    print(f'{n:10} \t {e_n:.15f} \t {erreur:.15e}')
``` 

#### Analyse :  
- Plus $n$ augmente, plus $e_n$ converge vers la valeur réelle de $e$.
- Cependant, des limitations apparaissent pour de très grands $n$ en raison de la précision numérique disponible.

**Exercice** :  
1. Testez le calcul de $e$ pour des valeurs encore plus grandes de $n$.  
2. Observez si des anomalies se produisent au-delà d'une certaine limite.

#### Illustration graphique : Convergence vers $e$
```  python
# Illustration graphique de la convergence
n_values = [10**i for i in range(1, 15)]
e_values = [(1 + 1/n) ** n for n in n_values]
errors = [abs(e - np.e) for e in e_values]
plt.figure(figsize=(10, 6))
plt.plot(n_values, e_values, label="Approximation de e", marker='o')
plt.axhline(y=np.e, color='r', linestyle='--', label="Valeur réelle de e")
plt.xscale('log')
plt.title("Convergence de l'approximation de e")
plt.xlabel("Valeurs de n (log scale)")
plt.ylabel("Valeur approchée de e")
plt.legend()
plt.grid(True)
plt.show()
``` 

### La fonction exponentielle $e^x$
La fonction exponentielle est définie par la série infinie suivante :

$$
e^x = \sum_{k=0}^\infty \frac{x^k}{k!}
$$

En pratique, l'ordinateur calcule une **série tronquée** :

$$
s_i(x) = \sum_{k=0}^i \frac{x^k}{k!}
$$

#### Exemple : Calcul de $e^x$ avec une tolérance fixée
```  python
def approx_exp(x, tol=1e-10):
    somme = 1.0
    terme = 1.0
    k = 1
    while abs(terme) > tol:
        terme *= x / k
        somme += terme
        k += 1
    return somme

# Comparaison pour x=1
x = 1
print(f'Valeur calculée : {approx_exp(x)}')
print(f'Valeur réelle (numpy) : {np.exp(x)}')
``` 

**Analyse** :  
- Le nombre de termes requis dépend de la tolérance choisie.  
- Des erreurs d'arrondi peuvent se cumuler pour des valeurs très grandes ou très petites de $x$.

**Exercice** :  
1. Écrivez une fonction pour comparer la série tronquée et la valeur réelle de $e^x$.  
2. Testez pour différents $x$ et différentes tolérances.















# Norme IEEE 754 : Représentation des nombres flottants

## Introduction à la Représentation Binaire des Nombres Réels

La représentation des nombres réels en informatique est un défi complexe qui nécessite une compréhension approfondie des principes de base de la représentation binaire.

### Structure Générale d'un Nombre Flottant

Un nombre flottant selon la norme IEEE 754 est composé de trois parties :
- **Bit de signe** : Indique si le nombre est positif ou négatif
- **Exposant** : Représente l'échelle du nombre
- **Mantisse (ou fraction)** : Représente la précision du nombre

## Norme IEEE 754 : Types de Précision

### 1. Simple Précision (float32)
- **Structure** : 32 bits
  - 1 bit de signe
  - 8 bits pour l'exposant
  - 23 bits pour la mantisse
- **Caractéristiques** :
  - Plage : $\pm 10^{-38}$ à $\pm 10^{38}$
  - Précision : environ 7 décimales
  - Économe en mémoire

### 2. Double Précision (float64)
- **Structure** : 64 bits
  - 1 bit de signe
  - 11 bits pour l'exposant
  - 52 bits pour la mantisse
- **Caractéristiques** :
  - Plage : $\pm 10^{-308}$ à $\pm 10^{308}$
  - Précision : environ 15-17 décimales
  - Standard en Python et calcul scientifique

```  python
import sys
import numpy as np

def analyse_float_types():
    """Analyse détaillée des types de nombres flottants"""
    print("Analyse des types float en Python :")
    print(f"float32 - Plage : {np.finfo(np.float32).min} à {np.finfo(np.float32).max}")
    print(f"float64 - Plage : {np.finfo(np.float64).min} à {np.finfo(np.float64).max}")
    print(f"\nPrécision :")
    print(f"float32 : {np.finfo(np.float32).precision} décimales")
    print(f"float64 : {np.finfo(np.float64).precision} décimales")

analyse_float_types()
``` 

## Visualisation des Erreurs de Précision

### Comparaison float32 vs float64

```  python
def precision_comparison():
    """Démonstration des différences de précision"""
    x_32 = np.float32(1.0)
    y_32 = np.float32(1e-8)
    x_64 = np.float64(1.0)
    y_64 = np.float64(1e-8)
    
    print("Comparaison de précision :")
    print(f"float32 : 1.0 + 1e-8 = {x_32 + y_32}")
    print(f"float64 : 1.0 + 1e-8 = {x_64 + y_64}")
    print(f"Valeur théorique    : {1.0 + 1e-8}")

precision_comparison()
``` 

## Types d'Erreurs Numériques

### 1. Erreurs d'Arrondi
Les erreurs d'arrondi surviennent lorsqu'un nombre réel ne peut être représenté exactement en binaire.

### 2. Erreurs d'Annulation
Situation où la soustraction de nombres très proches amplifie les imprécisions.

```  python
def demonstration_annulation():
    """Illustration des erreurs d'annulation"""
    # Calcul problématique : soustraction de nombres très proches
    a = 1.0000000001
    b = 1.0000000000
    
    print("Erreur d'annulation :")
    print(f"a = {a}")
    print(f"b = {b}")
    print(f"a - b = {a - b}")
    print(f"Valeur attendue : 1e-10")

demonstration_annulation()
``` 

## Exercices d'Évaluation

### Exercice 1 : Analyse de Précision
**Objectif** : Comprendre l'impact de la précision sur les calculs.

1. Écrivez un programme qui :
   - Crée deux tableaux de nombres avec float32 et float64
   - Calcule leur somme
   - Compare les résultats
   - Identifie les différences de précision

2. Répondez aux questions suivantes :
   - Quand utiliseriez-vous float32 plutôt que float64 ?
   - Quels sont les risques de perte de précision ?

### Exercice 2 : Propagation des Erreurs

**Objectif** : Observer la propagation des erreurs dans une série de calculs.

1. Implémentez une fonction qui :
   - Prend une série de nombres
   - Effectue des opérations successives (addition, multiplication)
   - Calcule l'erreur cumulative

2. Testez avec :
   - Une série de nombres très grands
   - Une série de nombres très petits
   - Une série de nombres alternant entre grand et petit

```  python
def propagation_erreurs(serie, operation='addition'):
    """
    Analyse la propagation des erreurs dans une série de calculs
    
    Args:
    - serie (list/np.array): Série de nombres à traiter
    - operation (str): Type d'opération ('addition' ou 'multiplication')
    
    Returns:
    - Résultats et analyse des erreurs
    """
    # Votre implémentation ici
    pass

# Exemple d'utilisation
numeros_grands = [1e10, 1, 1e-10]
numeros_alternants = [1e10, 1e-10, 1e10, 1e-10]

print("Série de nombres grands :")
print(propagation_erreurs(numeros_grands))
``` 

### Exercice 3 : Conception d'un Visualisateur d'Erreurs

**Objectif** : Créer une visualisation des erreurs de précision.

1. Développez un script qui :
   - Génère une série de calculs avec différentes précisions
   - Trace un graphique montrant l'accumulation des erreurs
   - Compare float32, float64, et éventuellement decimal

Conseils :
- Utilisez matplotlib pour la visualisation
- Annotez clairement les sources d'erreurs
- Montrez l'évolution des erreurs sur plusieurs itérations

## Recommandations :
- Utilisez float64 par défaut
- Soyez conscient des limitations de précision
- Utilisez des bibliothèques comme `decimal` pour une précision accrue si nécessaire