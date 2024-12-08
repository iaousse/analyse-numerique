# Matplotlib, NumPy et SciPy pour le Calcul Scientifique

Ce document propose une introduction aux bibliothèques Matplotlib, NumPy, et SciPy, essentielles pour le calcul scientifique et la visualisation en Python. Il se termine par une section sur les bonnes pratiques et une série d'exercices pour consolider les connaissances.

---

## Matplotlib : Création de Visualisations

### Introduction à Matplotlib

Matplotlib est une bibliothèque de traçage 2D très utilisée pour créer des graphiques en Python. Elle permet de réaliser des visualisations simples ou complexes, adaptées aux besoins de l'analyse scientifique.

``` python
# Installation de Matplotlib
# !pip install matplotlib

# Importation standard
import matplotlib.pyplot as plt
```

### Création de Graphiques Simples

``` python
# Création d'un graphique linéaire
x = [1, 2, 3, 4, 5]
y = [1, 4, 9, 16, 25]

plt.plot(x, y, marker='o', linestyle='-', color='b', label="y = x²")
plt.title("Exemple de Graphique")
plt.xlabel("x")
plt.ylabel("y")
plt.legend()
plt.grid(True)
plt.show()
```

### Visualisations Avancées

``` python
# Histogramme
data = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
plt.hist(data, bins=4, color='green', edgecolor='black')
plt.title("Histogramme")
plt.xlabel("Valeurs")
plt.ylabel("Fréquence")
plt.show()
```

---

## NumPy : Calcul Numérique Performant

### Introduction à NumPy

NumPy (Numerical Python) est une bibliothèque dédiée au calcul scientifique. Elle offre :
- Des tableaux multidimensionnels performants.
- Des opérations mathématiques vectorisées.
- Des outils pour l'algèbre linéaire et les statistiques.

``` python
# Installation et importation
# !pip install numpy
import numpy as np
```

### Création et Manipulation de Tableaux

``` python
# Création de tableaux
tableau_1d = np.array([1, 2, 3, 4, 5])
tableau_2d = np.array([[1, 2, 3], [4, 5, 6]])

# Propriétés des tableaux
print(f"Forme : {tableau_2d.shape}, Type : {tableau_2d.dtype}, Dimensions : {tableau_2d.ndim}")
```

### Opérations Mathématiques

``` python
# Opérations vectorisées
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
print(a + b)          # Addition
print(a ** 2)         # Puissance
print(np.mean(a))     # Moyenne
```

### Algèbre Linéaire

``` python
# Multiplication matricielle et inverse
A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])
print(np.dot(A, B))   # Produit matriciel
print(np.linalg.inv(A)) # Inverse
```

---

## SciPy : Calculs Avancés

### Introduction à SciPy

SciPy est une bibliothèque construite sur NumPy, offrant des fonctionnalités supplémentaires pour :
- L'optimisation.
- L'intégration.
- Le traitement de signaux.

``` python
# Installation et importation
# !pip install scipy
from scipy import linalg, optimize
```

### Exemple d'Optimisation

``` python
# Trouver un minimum local
def f(x):
    return x**2 + 4*np.sin(2*x)

resultat = optimize.minimize(f, x0=1)
print(f"Minimum local trouvé : {resultat.x}")
```

### Résolution de Systèmes Linéaires

``` python
# Résolution avec SciPy
A = np.array([[3, 2], [1, 4]])
b = np.array([6, 8])
solution = linalg.solve(A, b)
print(f"Solution : {solution}")
```

---

## Bonnes Pratiques

- **Clarté du Code** : Utilisez des noms de variables significatifs.
- **Visualisations Lisibles** : Ajoutez des titres, des légendes, et des axes clairs à vos graphiques.
- **Gestion des Erreurs** : Vérifiez les dimensions et les types de données avant d'effectuer des opérations.

---

## Exercices

### Exercice 1 : Graphique avec Matplotlib

1. Créez un graphique représentant la fonction $y = \sin(x)$ pour $x \in [0, 2\pi]$.
2. Ajoutez une grille, des légendes, et un titre.

### Exercice 2 : Manipulation de Tableaux NumPy

1. Créez un tableau de 10 nombres aléatoires suivant une distribution normale.
2. Calculez sa moyenne et son écart-type.
3. Remplacez tous les éléments supérieurs à la moyenne par 0.

### Exercice 3 : Résolution Numérique avec SciPy

1. Résolvez le système linéaire suivant avec SciPy :
   $$
   \begin{align*}
   2x + y &= 5 \\
   4x - 3y &= -6
   \end{align*}
   $$
2. Trouvez le minimum de la fonction $f(x) = (x-2)^2 + 3$.
