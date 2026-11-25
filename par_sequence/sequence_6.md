# Informatique S3 — Cours Python - Séquence 6

## Sommaire
- [Séquence 6 — Bibliothèque `matplotlib.pyplot`](#seq6)
	- [1. Figures et graphiques](#seq6-1)
	- [2. Customisation](#seq6-2)
		- [2.1 Titres et axes](#seq6-2-1)
		- [2.2 Traits, police, courbes et couleurs](#seq6-2-2)
	- [3. Multi-affichage](#seq6-3)
		- [3.1 Plusieurs courbes](#seq6-3-1)
		- [3.2 Subplots](#seq6-3-2)



<a id="seq6"></a>
# Séquence 6 — Bibliothèque `matplotlib.pyplot`
Par convention, on l'importe sous le nom `plt` :
```python
import matplotlib.pyplot as plt
```

<a id="seq6-1"></a>
## 1. Figures et graphiques
Pour créer une fenêtre de figure: `plt.figure()`
`plt.plot(x,y)` : trace une courbe reliant les points de coordonnées `(x[i], y[i])`. Les tableaux `x` et `y` doivent avoir la même taille.
À la fin pour afficher le graphique on fait: `plt.show()`

Exemple :
```python
import matplotlib.pyplot as plt
import numpy as np

x=np.linspace(0,2*np.pi, 500)
y=np.cos(x)
plt.figure()
plt.plot(x,y)
plt.show()
```

**Exercice :** $f(x)=\cos(\frac{\sin(x)}{x^2})$
1) Faire $f(x)$
2) Tracé de la courbe représentative sur $[-2.5,2.5] avec 5 000 points
```python
import matplotlib.pyplot as plt
import numpy as np

x=np.linspace(-2.5,2.5, 5000)
y=np.cos((np.sin(x)/x**2))
plt.figure()
plt.plot(x,y)
plt.show()
```
> **Remarque :** en $x=0$ la fonction n'est pas définie.

<a id="seq6-2"></a>
## 2. Customisation

<a id="seq6-2-1"></a>
### 2.1 Titres et axes
`plt.title("Mon titre")`
`plt.xlabel("titre d'abscisses")`
`plt.ylabel("titre d'ordonnées")`
`plt.xlim([a,b])`
`plt.ylim([c,d])`
`plt.grid()` Trace la grille automatiquement

<a id="seq6-2-2"></a>
### 2.2 Traits, police, courbes et couleurs

**Traits et marqueurs :**

| Option | Style de trait |
| :-: | :- |
| `'-'` | Trait continu (par défaut) |
| `'--'` | Tirets |
| `'-.'` | Tirets et points alternés |
| `':'` | Pointillés |

| Option | Marqueur |
| :-: | :- |
| `'.'` | Point |
| `'o'` | Cercle |
| `'x'` | Croix |
| `'+'` | Plus |
| `'*'` | Étoile |
| `'s'` | Carré |
| `'D'` | Losange |
| `'d'` | Losange fin |
| `'p'` | Pentagone |
| `'h'` | Hexagone |
| `'^'` | Triangle pointant vers le haut |
| `'v'` | Triangle pointant vers le bas |
| `'<'` | Triangle pointant vers la gauche |
| `'>'` | Triangle pointant vers la droite |
| `'\|'` | Trait vertical |
| `'_'` | Trait horizontal |

**Couleurs :**

`plt.plot(x,y, color='r')`
`plt.plot(x,y, color='orange')`

| Code court | Nom complet | Couleur |
| :-: | :-: | :-: |
| `'b'` | `'blue'` | Bleu |
| `'g'` | `'green'` | Vert |
| `'r'` | `'red'` | Rouge |
| `'c'` | `'cyan'` | Cyan |
| `'m'` | `'magenta'` | Magenta |
| `'y'` | `'yellow'` | Jaune |
| `'k'` | `'black'` | Noir |
| `'w'` | `'white'` | Blanc |
| — | `'orange'` | Orange |
| — | `'purple'` | Violet |
| — | `'brown'` | Marron |
| — | `'pink'` | Rose |
| — | `'gray'` | Gris |

**Taille du trait :**

`plt.plot(x,y, linewidth=5, marker='o', markersize=10)`

**Taille de police :**

- `plt.title("title", fontsize=8)`
- `plt.xticks(fontsize=12)`
- `plt.yticks(fontsize=14)`


<a id="seq6-3"></a>
## 3. Multi-affichage
<a id="seq6-3-1"></a>
### 3.1 Plusieurs courbes
Il faut juste rajouter une ligne `plt.plot`
Par exemple :
```python
plt.plot(x,y1)
plt.plot(x,y2)
```

Ajout de légende:
```python
plt.plot(x,y1, label='courbe1')
plt.plot(x,y2, label='courbe2')
plt.legend()
```
Ou alors:
```python
plt.legend(['courbe1','courbe2'])
```
<a id="seq6-3-2"></a>
### 3.2 Subplots
Utile pour ajouter plusieurs graphiques dans une seule figure.

```python
plt.subplot(abc)
# a : nombre de lignes de graphiques ;
# b : nombre de colonnes de graphiques ;
# c : position du graphique, en commençant à 1.
```
Lorsque l'un des paramètres est supérieur ou égal à 10, il faut utiliser la syntaxe avec trois arguments séparés par des virgules. Cette syntaxe fonctionne également pour les nombres inférieurs à 10.







Copyright © 2026 Ogust'1. All rights reserved.