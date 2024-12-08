# Représentation des nombres en calcul scientifique

Dans ce chapitre, nous explorons comment les nombres sont représentés dans les ordinateurs, les impacts de ces représentations sur les calculs numériques, et les erreurs qu'elles peuvent générer. Les exemples pratiques en Python illustrent ces concepts.

``` python
# Importation des bibliothèques nécessaires
import numpy as np
import matplotlib.pyplot as plt
``` 

---

## Introduction : La représentation des nombres

Les ordinateurs utilisent des approximations pour représenter les nombres réels. Cette limitation est due à la capacité finie de la mémoire. Cela entraîne des erreurs d'arrondi, des pertes de précision, et parfois des résultats inattendus lors des calculs complexes.

- **Limite fondamentale** : Un nombre réel, en raison de sa nature infinie en base 10, est représenté de manière tronquée ou arrondie en base 2.
- **Conséquences** :
  - **Erreurs d'arrondi** : Lorsqu’un nombre ne peut être représenté exactement, il est arrondi à la valeur la plus proche.
  - **Erreurs d'annulation** : Ces erreurs se produisent lorsqu'on soustrait deux nombres presque égaux, ce qui amplifie l'effet des approximations.

**Exemple : Effet d'une erreur d'annulation**  
``` python
# Exemple d'erreur d'annulation
a = 1.0000000001
b = 1.0000000000
c = a - b
print(f"Résultat attendu : {1e-10}, Résultat calculé : {c}")
``` 

---

## Approximation des constantes mathématiques

### Le nombre d'Euler $e$

Le nombre d’Euler $e$ est défini par :

$$
e = \lim_{n \to \infty} \left( 1 + \frac{1}{n} \right)^n
$$

En pratique, $e$ est calculé pour une valeur finie de $n$. Cela introduit des erreurs liées à la précision numérique.

#### Exemple : Approximations numériques de $e$

``` python
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
2. Observez si des anomalies se produisent au-delà d’une certaine limite.

#### Illustration graphique : Convergence vers $e$

``` python
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

En pratique, l’ordinateur calcule une **série tronquée** :

$$
s_i(x) = \sum_{k=0}^i \frac{x^k}{k!}
$$

#### Exemple : Calcul de $e^x$ avec une tolérance fixée

``` python
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

---

## Norme IEEE 754 : Représentation des nombres flottants

La norme **IEEE 754** est le standard utilisé pour représenter les nombres réels en mémoire. Elle définit deux types principaux de précision :

1. **Simple précision (float32)** :
   - Utilise 32 bits pour coder un nombre.
   - Moins précise, mais nécessite moins de mémoire.
   - Plage de valeurs : $10^{-38}$ à $10^{38}$.

2. **Double précision (float64)** :
   - Utilise 64 bits.
   - Précision élevée, utilisée par défaut en Python.
   - Plage de valeurs : $10^{-308}$ à $10^{308}$.

### Propriétés des nombres flottants

``` python
# Affichage des limites des nombres en Python
import sys
print(f'Plus petit nombre : {sys.float_info.min}')
print(f'Plus grand nombre : {sys.float_info.max}')
``` 

#### Exemple : Erreurs liées à la précision

``` python
# Comparaison entre float32 et float64
x = np.float32(1.0)
y = np.float32(1e-8)
print(f"Résultat attendu : {1.0 + 1e-8}")
print(f"Résultat avec float32 : {x + y}")
print(f"Résultat avec float64 : {1.0 + 1e-8}")
``` 

---

## Erreurs d'arrondi et d'annulation

Les erreurs d'arrondi se produisent lorsque la précision est insuffisante pour représenter un nombre. Ces erreurs peuvent être amplifiées dans certains calculs :

1. **Somme de grands et petits nombres** : Les petits nombres peuvent être négligés.
2. **Annulation** : La soustraction de deux nombres proches amplifie les erreurs.

#### Exemple : Somme alternée

``` python
n = 1000
x = np.linspace(1, n, n)
y = np.sin(x) - np.sin(x - 1)
somme = np.sum(y)
print(f'Somme calculée : {somme}')
``` 

**Exercice** :  
1. Implémentez un exemple où la soustraction de nombres proches entraîne une perte de précision.  
2. Analysez l’impact sur des séries longues.

---
