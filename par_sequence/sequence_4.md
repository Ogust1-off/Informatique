# Informatique S3 — Cours Python - Séquence 4

## Sommaire
- [Séquence 4 — Fonctions et algorithmique](#seq4)
	- [1. Écriture de fonctions](#seq4-1)
		- [1.1 Définition et syntaxe](#seq4-1-1)
		- [1.2 Paramètres et renvois](#seq4-1-2)
		- [1.3 Documentation](#seq4-1-3)
	- [2. Appel de fonctions](#seq4-2)
		- [2.1 Bibliothèques Python](#seq4-2-1)
		- [2.2 Portée des variables](#seq4-2-2)
		- [2.3 Récursivité](#seq4-2-3)


<a id="seq4"></a>
# Séquence 4 — Fonctions et algorithmique
<a id="seq4-1"></a>
## 1. Écriture de fonctions
<a id="seq4-1-1"></a>
### 1.1 Définition et syntaxe

En Python, comme dans les autres langages, l'usage de fonctions est fortement recommandé pour améliorer la lisibilité d'un code. Cela permet entre autres d'éviter de réécrire plusieurs fois un même code quand il dépend uniquement d'un changement de variable (cf Programme du produit matriciel [Seq3 §1.4](#seq3-1-4)) (Ajout personnel)

On utilise `def` pour créer une fonction
```python
def fonction(parametres):
    instructions
    return resultats
```
```python
r=fonction(parametres)
```
La variable `r` contient ce que la fonction `fonction` retourne.

> **Remarque :**
> 1) `return` ≠ `print`
> 2) paramètres ≠ arguments

**Exercice :** Crée une fonction qui retourne l'image de la fonction : $f(x)=\frac{x^2+2x-4}{\sqrt{x-3}}$
```python
x=int(input("Votre valeur de x: "))
def f(x):
    resultat = (x**2+2*x-4)/((x-3)**(1/2))
    return resultat
print(f(x))
```

Le type d'une fonction est `function`.
Donc :
```python
type(f)
# RETOURNE : <class 'function'>
```

On peut donc écrire :
```python
def f(x):
    # instructions
    return
def g(x):
    # instructions
    return
def composition(f,g,x):
    return f(g(x))
```

<a id="seq4-1-2"></a>
### 1.2 Paramètres et renvois

```python
def fonction(p1, ... , pn):
    # instructions
    return r1, ... , rm

a1, ... , am = fonction(p1, ... , pn)
```

> **Remarque :**
> 1) Une fonction peut ne pas avoir de paramètres (`f()`) par exemple `.sort()`,`.copy()` (qui en réalité sont des méthodes).
> 2) Une fonction peut ne rien renvoyer par exemple :
> ```python
> def hello():
>     print("Hello World!")
> hello()
>
> # RETOURNE : Hello World!
> # Mais la fonction hello ne retourne rien (None).
> ```

**Exercice :** Soit un polynôme du second degré: $p(x)=ax^2+bx+c$, avec $(a,b,c)\inℝ^3$.
Déterminer les solutions de $p(x)=0$ pour $a=-1$, $b=-2$ et $c=5$.
```python
def racines(a,b,c):
    delta=b**2-4*a*c
    if delta>0:
        x1=(-b-delta**(1/2))/(2*a)
        x2=(-b+delta**(1/2))/(2*a)
        return x1,x2
    elif delta==0:
        return (-b)/(2*a)
    else:
        return "Aucune racine réelle"
    
print(racines(-1,-2,5))
# RETOURNE : (1.4494897427831779, -3.449489742783178)
```

<a id="seq4-1-3"></a>
### 1.3 Documentation

Il est important d'expliquer ce que fait une fonction. Voici une manière de le faire :
```python
def fonction(p1, ... , pn):
    """
    fonction: description de ce que la fonction fait.
    ----------------------
    Entrée :
        p1 : info
        ...
        pn : info
    ----------------------
    Sortie : info
        r1 : info
        ...
        rm : info
    """
    return r1, ... , rm
```

<a id="seq4-2"></a>
## 2. Appel de fonctions
<a id="seq4-2-1"></a>
### 2.1 Bibliothèques Python

1) Pour utiliser un module ou une bibliothèque, il faut d'abord l'importer. Pour cela on utilise : `import` en suivant la syntaxe :
```python
import nomBibliotheque
```
On peut citer comme exemple courant de bibliothèque `random` ou `math` que l'on utilise comme ceci : `import random`, `import math`.

> **Remarque :**
> Pour que l'on puisse utiliser les fonctions associées à ces bibliothèques il est important de faire l'import avant l'usage de ses fonctions. On place donc généralement les imports au début du code.
> ```python
> import math
> import random
> # import ...
> 
> # Puis seulement ensuite le reste du code.
> ```

2) Pour utiliser les fonctions de la bibliothèque importée on utilise la syntaxe suivante :
```python
nomBibliotheque.nomfonction()
```
Qui permet ici d'utiliser la fonction `nomfonction` de la bibliothèque `nomBibliotheque`.

3) On peut aussi renommer cette bibliothèque pour faciliter son usage dans la suite du code. Ici `nomBibliotheque` en `nouveauNom` :
```python
import nomBibliotheque as nouveauNom
```
Pour l'utiliser on utilise donc le nouveau nom donné à la fonction, suivi de la fonction appelée en suivant la syntaxe suivante :
```python
nouveauNom.nomfonction()
```

4) On peut aussi importer uniquement une fonction d'une bibliothèque.
Ici on importe la fonction `fonctionImporter` de la bibliothèque `nomBibliotheque`:
```python
from nomBibliotheque import fonctionImporter
```
Pour l'utiliser on utilise donc son nom : `fonctionImporter()`

5) Enfin, on peut aussi renommer cette fonction importée pour faciliter son utilisation dans le code :
Ici, on importe `fonctionImporter` depuis `nomBibliotheque` et on renomme la fonction importée en `fct` :
```python
from nomBibliotheque import fonctionImporter as fct
```
Pour l'utiliser on utilise donc son nouveau nom : `fct()`.

Exemple de fonction courante de la bibliothèque `math`: `sqrt`, `cos`, `sin`.

**Exercice :** Trouvez l'angle entre la ("grande") diagonale d'un cube et une de ses arêtes adjacentes.
1) produit_scalaire(x,y)
2) angle_entre_2vecteurs(x,y)
```python
import math

def produit_scalaire(x,y):
    produit=0
    for i in range(len(x)):
        produit+=x[i]*y[i]
    return produit

def angle_entre_2vecteurs(x,y):
    if len(x)!=len(y):
        print("Vos vecteurs ne sont pas de même dimension")
    else:
        #angle=math.acos((produit_scalaire(x,y))/(math.sqrt(x[0]**2+x[1]**2)*math.sqrt(y[0]**2+y[1]**2)))
        angle=math.acos((produit_scalaire(x,y))/(math.sqrt(produit_scalaire(x,x))*math.sqrt(produit_scalaire(y,y))))
        return angle

#print(produit_scalaire([0,1],[1,0]))
print(f"L'angle entre vos deux vecteurs est de {angle_entre_2vecteurs([0,1,0],[1,1,1])} radian")

# RETOURNE : L'angle entre vos deux vecteurs est de 0.9553166181245092 radian
```

<a id="seq4-2-2"></a>
### 2.2 Portée des variables
- Les variables locales sont définies dans une fonction et ne sont accessibles que dans celle-ci.
- Les variables globales sont définies en dehors des fonctions et peuvent être utilisées dans celles-ci, sous certaines conditions.

Exemple :
```python
n=5 # Variable global
def afficheur():
    for i in range(n): # Variable local
        print("i=", i)
    print("ici i vaut", i)
afficheur()
print("n=", n)
print("i=", i) # ERREUR car i est une variable local donc le programme ne la connaît pas
```

<a id="seq4-2-3"></a>
### 2.3 Récursivité
C'est quand une fonction s'appelle elle-même pour se définir
*C'est très pratique pour les processus itératifs (calcul de somme, ...)*

Exemple :
```python
def factorielle(n):
    if n<=1:
        return 1
    else:
        return n*factorielle(n-1)

print(factorielle(5))
# RETOURNE: 120
```

**Exercice :** Soit la suite $U_{n+2}=U_{n+1}\times U_n$ avec $U_0=2$ et $U_1=3$.
1) U(n) -> calculer $U(5)$
2) sommeSuite(n) -> calculer sommeSuite(5)
```python
def U(n):
    if n==0: return 2
    elif n==1: return 3
    else:
        return U(n-1)*U(n-2)

def sommeSuite(n):
    if n==0: return U(n)
    else:
        return U(n)+sommeSuite(n-1)

print(f"U(5) = {U(5)} et la somme de U(0) à U(5) = {sommeSuite(5)}")
# RETOURNE : U(5) = 1944 et la somme de U(0) à U(5) = 2081
```

