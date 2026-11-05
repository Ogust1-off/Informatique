# Informatique S3 — Cours Python — Séquence 1

## Sommaire
- [Séquence 1 — Premiers pas en Python](#seq1)
	- [1. Bases](#seq1-1)
		- [1.1 Variable, identifiant et affectation](#seq1-1-1)
		- [1.2 Commentaire](#seq1-1-2)
		- [1.3 Entrée/Sortie](#seq1-1-3)
	- [2. Types et opérations](#seq1-2)
		- [2.1 Nombres](#seq1-2-1)
		- [2.2 Booléens](#seq1-2-2)
		- [2.3 Chaînes de caractères, conversion de type et f-strings](#seq1-2-3)
	- [3. Débogage](#seq1-3)
		- [3.1 Réflexes](#seq1-3-1)
		- [3.2 Erreurs courantes](#seq1-3-2)


<a id="seq1"></a>
# Séquence 1 — Premiers pas en Python
<a id="seq1-1"></a>
## 1. Bases
<a id="seq1-1-1"></a>
### 1.1 Variable, identifiant et affectation
**Définition :** Une **variable** est l'association d'un **identifiant** à un objet stocké en mémoire.
Cette opération d'association est appelée **affectation** (`=`).
Exemple : `a = 1` et `b = 2`.

> **Attention :**
> 1. (`=`) n'est pas symétrique : `1 = a` est impossible.
> 2. L'opérateur `=` permet également la mise à jour d'une variable.
            
**Exercice :** Attribuer une valeur à la variable `a` et une autre à la variable `b`.
```python
a = 1
b = 2
```
Pour échanger deux variables, on peut faire :
```python
c = a
a = b
b = c
```

> **Remarque :**
> 1. Bien choisir l'identifiant des variables (`s`, `somme`, etc.).
> 2. Un identifiant doit respecter certaines règles : il ne peut pas contenir certains caractères (`@`, `#`, etc.) et ne peut pas commencer par un nombre.
          
<a id="seq1-1-2"></a>  
### 1.2 Commentaire
En Python, on utilise `#` pour écrire un commentaire sur une ligne.
Un commentaire peut également être placé après du code sur la même ligne.
On peut aussi utiliser `"""` pour une chaîne de caractères multilignes. On peut parfois l'utiliser comme un commentaire, mais ce n'est pas techniquement un commentaire.

**Exemple :**
```python
# commentaire d'une ligne
a = 1  # commentaire après du code
"""
Chaîne de caractères
sur plusieurs lignes
"""
```

<a id="seq1-1-3"></a>
### 1.3 Entrée/Sortie
Affichage : `print()`

Multi-affichage :
```python
a = 1
b = 2
c = 3
print(a, b, c)
# RETOURNE : 1 2 3
```

Affichage de chaîne de caractères : `print("Hello World!")`

Saisie utilisateur : `input()`

> **Attention :** `input()` renvoie **toujours** une chaîne de caractères.

Exemple :
```python
name = input("Quel est votre nom ? ")
print(name)
```
<a id="seq1-2"></a>
## 2. Types et opérations
**Définition :** En Python, chaque objet possède un **type**. Il indique la nature de l'objet manipulé et les **opérations** que l'on peut lui appliquer.

Fonction `type()`:
```python
print(type("Hello World"))
# RETOURNE : str
```

<a id="seq1-2-1"></a>
### 2.1 Nombres

- `int`: entier relatif
- `float`: nombres décimaux
- `complex`: nombre complexe, avec `j` pour représenter la partie imaginaire (identique au i en maths)

Exemple :
```python
z= 3+4j
print(z.real, z.imag)
```

Opérations arithmétiques:
| Opérateur | Signification                             |
| --------- | ----------------------------------------- |
| `+`       | addition                                  |
| `-`       | soustraction                              |
| `*`       | multiplication                            |
| `**`      | puissance                                 |
| `/`       | division                                  |
| `//`      | division euclidienne                      |
| `%`       | modulo (reste de la division euclidienne) |


**Exercice :**
```python
a, b = 21, 5
a/b # 4.2 en float
a//b # 4 en int
a%b # 1 en int
```

**Opérations d'affectation :**
incrémentation, décrémentation
```python
a += 1
b -= 2
```

**Exercice :** Bob a 4 notes : 10, 15, 13 et 8. Calculer sa moyenne.
```python
moy = 10
moy += 15
moy += 13
moy += 8
moy /= 4
print(moy)
# RETOURNE : 11.5
```
<a id="seq1-2-2"></a>
### 2.2 Booléens
`bool` -> `True`, `False`

Opérations de comparaisons:
| Opérateur | Signification       |
| --------- | ------------------- |
| `==`      | égal à              |
| `<`       | inférieur à         |
| `>`       | supérieur à         |
| `<=`      | inférieur ou égal à |
| `>=`      | supérieur ou égal à |
| `!=`      | différent de        |


**Exercice :**
```python
a, b = True, False
a == b  # False
a != b  # True
```
<a id="seq1-2-3"></a>
### 2.3 Chaînes de caractères, conversion de type et f-strings
- Type d'une chaîne de caractères: `str`
- Concaténation: assemblage de deux chaînes de caractères avec `+`

Exemple :
```python
txt1="Hello"
space=" "
txt2="World"
print(txt1+space+txt2)
```
La concaténation fonctionne également avec `+=`

**Exemple personnel :**
```python
txt = "Hello"
txt += " World"
```

Conversion de type : convertit une valeur dans le type souhaité.
| Fonction | Type |
| :- | :- |
| `int()` | Entier |
| `float()` | Nombre réel |
| `complex()` | Nombre complexe |
| `bool()` | Booléen |
| `str()` | Chaîne de caractères |

Exemple :
```python
age = 20
print("J'ai "+str(age)+" ans")
```
```python
age = 20.0
print(f"J'ai {age:.0f} ans")
# RETOURNE : J'ai 20 ans
```

**Exercice :**
```python
p = float(input("Ton poids (kg)? "))
t = float(input("Ta taille (m)? "))
print(f"Ton imc est: {p/(t**2)}")
```

<a id="seq1-3"></a>
## 3. Débogage
<a id="seq1-3-1"></a>
### 3.1 Réflexes
- Lire l'erreur et essayer de la comprendre.
- Vérifier la syntaxe du code.
- Utiliser `help()`. [Par exemple `help(print)` renvoie la documentation sur la fonction `print()`]
- Rechercher en ligne votre message d'erreur.

<a id="seq1-3-2"></a>
### 3.2 Erreurs courantes
- `SyntaxError`: apparaît quand le code est mal écrit: oubli de parenthèse, de tabulation, de frappe dans le code (print("Hello Wolrd") n'est pas une erreur), ...
- `NameError`: apparaît par exemple quand une variable n'est pas définie, ...

