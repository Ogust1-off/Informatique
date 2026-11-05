# Informatique S3 — Cours Python - Séquence 5

## Sommaire
- [Séquence 5 — Bibliothèque NumPy](#seq5)
	- [1. Opérations mathématiques](#seq5-1)
		- [1.1 Constantes et fonctions utiles](#seq5-1-1)
			- [A. Constantes](#seq5-1-1-A)
			- [B. Fonctions mathématiques](#seq5-1-1-B)
		- [1.2 Fonctions usuelles](#seq5-1-2)
		- [1.3 Complexes](#seq5-1-3)
	- [2. Tableaux NumPy](#seq5-2)
		- [2.1 Vecteurs, matrices & tableaux particuliers](#seq5-2-1)
			- [A. Création de tableaux](#seq5-2-1-A)
			- [B. Dimensions d'un tableau : `shape`](#seq5-2-1-B)
			- [C. Indexation et extraction (slicing)](#seq5-2-1-C)
			- [D. Redimensionnement : `reshape()`](#seq5-2-1-D)
			- [E. Trace d'une matrice](#seq5-2-1-E)
			- [F. Création de tableaux régulièrement espacés](#seq5-2-1-F)
			- [G. Tableaux particuliers](#seq5-2-1-G)
		- [2.2 Opérations sur les tableaux](#seq5-2-2)


<a id="seq5"></a>
# Séquence 5 — Bibliothèque NumPy

NumPy est une bibliothèque Python utilisée pour les calculs scientifiques, notamment pour manipuler des tableaux numériques et effectuer des opérations mathématiques.

Par convention, on importe NumPy sous le nom `np` :
```python
import numpy as np
```
La documentation et des tutoriels sont disponibles sur [numpy.org](https://numpy.org/).

<a id="seq5-1"></a>
## 1. Opérations mathématiques
<a id="seq5-1-1"></a>
### 1.1 Constantes et fonctions utiles

<a id="seq5-1-1-A"></a>
**A. Constantes**
| Mathématiques | NumPy | Signification |
| :- | :- | :- |
| $\pi$ | `np.pi` | Constante $\pi$ |
| $e$ | `np.e` | Base du logarithme népérien |
| $+\infty$ | `np.inf` | Infini positif |
| NaN (Not a Number) | `np.nan` | Valeur représentant un résultat numérique indéfini ou absent |

<a id="seq5-1-1-B"></a>
**B. Fonctions mathématiques**
| Fonction NumPy | Notation Mathématique | Signification | Exemple |
| :- | :- | :- | :- |
| np.abs(x) | $\lvert x\rvert$ | Valeur absolue de $x$ | `np.abs(-3)` → `3` |
| np.sign(x) | $\mathrm{sgn}(x)$ | Renvoie le signe de $x$ : −1, 0 ou 1 | `np.sign(-3)` → `-1` |
| np.round(x, d) |  | Arrondit $x$ à $d$ décimales | `np.round(3.14159, 2)` → `3.14` |
| np.floor(x) | $\lfloor x \rfloor$ | Plus grand entier inférieur ou égal à $x$ | `np.floor(3.8)` → `3.0` |
| np.ceil(x) | $\lceil x \rceil$ | Plus petit entier supérieur ou égal à $x$ | `np.ceil(3.2)` → `4.0` |

**Exercice :** Soit $\displaystyle{\lim_{n\to+\infty}\sum_{k=1}^{n}\frac{1}{k^2}=\frac{\pi^2}{6}}$, écrire les fonctions suivantes :
1) `inverseCarres(n)` : calcule $\frac{1}{n^2}$.
2) `somme(n)` : calcule la somme des inverses des carrés de $1$ à $n$.
3) `erreur(n)` : calcule l'écart entre cette somme et sa limite théorique.

```python
import numpy as np

def inverseCarres(n):
    return 1/n**2

def somme(n):
    somme=0
    for i in range(1,n+1):
        somme+=inverseCarres(i)
    return somme

def erreur(n):
    return np.abs(np.pi**2/6-somme(n))
```

**Exercice :** Soit $a>0$, $x_0=a$, $x_{n+1}=\frac12(x_n+\frac{a}{x_n})$
Cette relation permet d'approcher $\sqrt a$ par la méthode de Héron.
1) `heron(a, epsilon)` : calcule une approximation de $\sqrt a$ jusqu'à ce que la différence entre deux approximations successives soit inférieure à epsilon. La fonction renvoie l'approximation obtenue ainsi que le nombre d'itérations effectuées.

```python
import numpy as np

def heron(a,epsilon):
    x0=a
    x=0.5*(a+1)
    cpt=1
    while np.abs(x-x0)>=epsilon:
        x0=x
        x=(1/2)*(x0+(a/x0))
        cpt+=1
    return x, cpt

a = float(input("Choisir une valeur de a (> 0) : "))
epsilon = float(input("Choisir une valeur pour epsilon (> 0) : "))

if a > 0 and epsilon > 0:
    print(heron(a, epsilon))
else:
    print("a et epsilon doivent être strictement positifs.")
```

<a id="seq5-1-2"></a>
### 1.2 Fonctions usuelles
Les fonctions usuelles de NumPy permettent d'effectuer des opérations mathématiques sur des nombres, mais également directement sur des tableaux (vectorisation).

| Fonction NumPy | Notation Mathématique | Signification |
| :- | :- | :- |
| `np.sqrt(x)` | $\sqrt{x}$ | Racine carrée |
| `np.exp(x)` | $e^x$ | Fonction exponentielle |
| `np.log(x)` | $\ln(x)$ | Logarithme népérien |
| `np.sin(x)` | $\sin(x)$ | Sinus |
| `np.cos(x)` | $\cos(x)$ | Cosinus |
| `np.tan(x)` | $\tan(x)$ | Tangente |
| `np.arccos(x)` | $\arccos(x)$ | Arc cosinus |
| `np.arcsin(x)` | $\arcsin(x)$ | Arc sinus |
| `np.arctan(x)` | $\arctan(x)$ | Arc tangente |

> **Remarque :** Les fonctions trigonométriques donnent par défaut les résultats en radians.

```python
import numpy as np
X=[1,2,3]
L=np.sqrt(X)
print(L)
# RETOURNE : [1.         1.41421356 1.73205081]
```
Contrairement aux fonctions de la bibliothèque `math`, ces fonctions peuvent être appliquées à des tableaux de valeur.

**Exercice :** Méthodes des rectangles.

Soit: $\displaystyle{I=\int_{a}^{b}f(x)dx}$. On cherche à approcher le résultat de cette intégrale à l'aide de la somme de rectangles.

* $\displaystyle{I_g=h\sum_{i=0}^{n-1}f(x_i)}$ 
* $\displaystyle{I_d=h\sum_{i=1}^{n}f(x_i)}$

Écrire les fonctions suivantes :
1) `decoupage(a, b, n)` : renvoie les points de subdivision de l'intervalle.
2) `rectangles(f, a, b, n)` : calcule les approximations à gauche et à droite de l'intégrale.

```python
import numpy as np

def decoupage(a, b, n):
    h = (b-a)/n
    l = []
    for i in range(n+1):
        l.append(a+h*i)
    return np.array(l)

def rectangles(f, a, b, n):
    points = decoupage(a, b, n)
    h = (b-a)/n

    Ig = np.sum(f(points[:-1]))*h
    Id = np.sum(f(points[1:]))*h

    return Ig, Id

def f(x):
    return x

print(rectangles(f, 0, 1, 4))
# RETOURNE : (np.float64(0.375), np.float64(0.625))
```

<a id="seq5-1-3"></a>
### 1.3 Complexes
NumPy permet également de manipuler les nombres complexes.

| Fonction NumPy / Python | Signification | Exemple (pour $z=3+4i$) (z = 3+4j en python) |
| :- | :- | :- |
| `z.real` | Partie réelle | `3.0` |
| `z.imag` | Partie imaginaire | `4.0` |
| `z.conjugate()` | Conjugué de $z$ | `(3-4j)` |
| `np.angle(z)` | Argument de $z$ en radians | `0.9272952180016122` |
| `np.angle(z, deg=True)` | Argument de $z$ en degrés | `53.13010235415598` |
| `np.abs(z)` | Module de $z$ | `5.0` |

**Exercice :** Calculer une approximation de $\pi$ par la méthode d'Archimède.
```python
# A Faire
```

<a id="seq5-2"></a>
### 2. Tableaux NumPy
NumPy permet de convertir des listes Python en tableaux numériques appelés ndarray *(N-dimensional array)*.

```python
import numpy as np 
X=[1,2,3,4]
L=np.log(X)
print(type(L))
# RETOURNE : <class 'numpy.ndarray'>
```

<a id="seq5-2-1"></a>
### 2.1 Vecteurs, matrices & tableaux particuliers

<a id="seq5-2-1-A"></a>
**A. Création de tableaux**

```python
import numpy as np 
vec = np.array([1,2,3,4])
mat = np.array([[1,2],[3,4]])
print(vec)
print(mat)
# RETOURNE :
# [1 2 3 4]
# [[1 2]
#  [3 4]]
```

<a id="seq5-2-1-B"></a>
**B. Dimensions d'un tableau : `shape`**

L'attribut shape renvoie les dimensions du tableau sous la forme d'un tuple.

```python
import numpy as np 
mat=np.array([[1,2,3],[4,5,6]])
print(mat.shape)
print(mat.shape[0])
print(mat.shape[1])
# RETOURNE :
# (2, 3)
# 2
# 3
```
* `mat.shape[0]` : nombre de lignes de la matrice `mat`.
* `mat.shape[1]` : nombre de colonnes de la matrice `mat`.

<a id="seq5-2-1-C"></a>
**C. Indexation et extraction (slicing)**

Comme pour les listes Python, les éléments d'un tableau NumPy sont accessibles grâce à leurs indices.

| Syntaxe | Description |
| :- | :- |
| `vec[i]` | Accède à l'élément d'indice `i` du vecteur `vec`. |
| `mat[i, j]` ou `mat[i][j]`| Accède à l'élément situé à la ligne `i` et à la colonne `j`. |
| `mat[i, :]` | Extrait la ligne `i` de la matrice. |
| `mat[:, j]` | Extrait la colonne `j` de la matrice. |
| `mat[i:j, k:l]` | Extrait un sous-tableau : lignes de `i` à `j-1` et colonnes de `k` à `l-1`. |
> **Attention :** dans un slicing `debut:fin`, l'indice de début est inclus, mais celui de fin est exclu.

Exemple :
```python
import numpy as np

mat = np.array([[1, 2, 3], [4, 5, 6]])

print(mat[0, 1])
print(mat[1, :])
print(mat[:, 0])

# RETOURNE :
# 2
# [4 5 6]
# [1 4]
```
<a id="seq5-2-1-D"></a>
**D. Redimensionnement : `reshape()`**

La méthode reshape() permet de modifier la forme d'un tableau sans changer ses éléments.

```python
import numpy as np 
tab=np.array([[1,2,3],[4,5,6]])
print(tab.reshape(1,6))
print(tab.reshape(3,2))
# RETOURNE :
# [[1 2 3 4 5 6]]
# [[1 2]
#  [3 4]
#  [5 6]]
```
> **Attention :** aux bornes
> Ici, par exemple `tab.reshape(1,8)` est impossible car tab contient uniquement 6 éléments.

<a id="seq5-2-1-E"></a>
**E. Trace d'une matrice**

La trace d'une matrice carrée $A\in\mathcal{M}_p(ℝ)$ est la somme des coefficients de sa diagonale principale :

$$
A =
\begin{pmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{n1} & a_{n2} & \cdots & a_{nn}
\end{pmatrix}
$$

$$\displaystyle{\mathrm{Tr}(A)=\sum_{i=1}^n a_{ii}=a_{11}+a_{22}+\cdots+a_{nn}}$$

**Exercice :** Écrire une fonction trace(A) qui calcule la trace d'une matrice carrée.
```python
import numpy as np

def trace(mat):
    mat = np.array(mat)

    if mat.ndim == 2 and mat.shape[0] == mat.shape[1]: # mat.ndim == 2 vérifie que le tableau possède deux dimensions.
        s = 0
        for i in range(mat.shape[0]):
            s += mat[i][i]
        return s
    else:
        print("La matrice doit être carrée.")

print(trace([[1, 1], [1, 1]]))
# RETOURNE : 2
```
<a id="seq5-2-1-F"></a>
**F. Création de tableaux régulièrement espacés**

```python
vec1=np.linspace(2,10,5)
vec2=np.arange(2,10,2)
```
* `np.linspace(a, b, n)` : crée n valeurs régulièrement espacées entre a et b, bornes incluses.
* `np.arange(a, b, p)` : crée des valeurs de a inclus à b exclu, avec un pas de p.

<a id="seq5-2-1-G"></a>
**G. Tableaux particuliers**

| Fonction NumPy | Résultat |
| :- | :- |
| `np.zeros(x)` | Tableau de $x$ zéros |
| `np.zeros([x,y])` | Matrice de zéros de dimension $x\times y$ |
| `np.ones(x)` | Tableau de $x$ uns |
| `np.ones([x,y])` | Matrice de uns de dimension $x\times y$ |
| `np.eye(x)` | Matrice identité de dimension $x\times x$ |
| `np.diag([a1, a2, ... , an])` | Matrice diagonale contenant: $a_1, a_2, ... , a_n$ ($n\in ℕ$) |

Exemples : 
```python
np.zeros(2)
# RETOURNE :
# [0. 0.]
```

```python
np.zeros([2,2])
# RETOURNE :
# [[0. 0.]
#  [0. 0.]]
```

```python
np.ones(2)
# RETOURNE : 
# [1. 1.]
```

```python
np.ones([2,2])
# RETOURNE :
# [[1. 1.]
#  [1. 1.]]
```

```python
np.eye(2)
# RETOURNE :
# [[1. 0.]
#  [0. 1.]]
```

```python
np.diag([1,2,3,4])
# RETOURNE :
# [[1 0 0 0]
#  [0 2 0 0]
#  [0 0 3 0]
#  [0 0 0 4]]
```

<a id="seq5-2-2"></a>
### 2.2 Opérations sur les tableaux
Les opérations arithmétiques usuelles peuvent être appliquées directement aux tableaux NumPy.

```python
import numpy as np 

A=np.array([[1,2],[3,4]])
print(A+A)
print(5*A)
print(5*A-A)
print(A*A)
print(A**0.5)

# RETOURNE :
# [[2 4]
#  [6 8]]
# [[ 5 10]
#  [15 20]]
# [[ 4  8]
#  [12 16]]
# [[ 1  4]
#  [ 9 16]]
# [[1.         1.41421356]
# [1.73205081 2.        ]]
```

> **Attention :**
> A*B effectue une multiplication terme à terme et non un produit matriciel.
> A**2 élève chaque coefficient de A au carré.
> `np.dot(A, B)` ou `A @ B` permet d'effectuer un produit matriciel.

**Exercice :** Écrire un programme permettant de calculer le produit matriciel de deux matrices $A,B\in\mathcal{M}_n(ℝ)$, sans utiliser np.dot(A, B).
```python
# À faire
```

