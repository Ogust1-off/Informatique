# Informatique S3 — Cours Python — Séquence 2

## Sommaire
- [Séquence 2 — Logique, tests conditionnels et boucles](#seq2)
	- [1. Logique](#seq2-1)
		- [1.1 Conditions logiques](#seq2-1-1)
		- [1.2 Opérateurs logiques](#seq2-1-2)
	- [2. Tests conditionnels](#seq2-2)
		- [2.1 Instruction if](#seq2-2-1)
		- [2.2 Instruction if-else](#seq2-2-2)
		- [2.3 Instruction if-elif-else](#seq2-2-3)
		- [2.4 Instruction match-case](#seq2-2-4)
	- [3. Boucles](#seq2-3)
		- [3.1 Boucle for](#seq2-3-1)
		- [3.2 Boucle while](#seq2-3-2)


<a id="seq2"></a>
# Séquence 2 — Logique, tests conditionnels et boucles
<a id="seq2-1"></a>
## 1. Logique
<a id="seq2-1-1"></a>
### 1.1 Conditions logiques
```python
cond_1 = 5**2 < 2**5
cond_2 = 36 ==89
print(cond_1, cond_2)
# RETOURNE : True False
```
**Exercice :** Demander l'année de naissance de l'utilisateur et déterminer s'il est majeur (`True`) ou non (`False`).
```python
a=int(input("Année de naissance : "))
calc=2026-a #Pour l'année 2026
cond=calc>=18
print(f"Majeur? {cond}")
```
> **Remarque :**
> Le programme ne tient pas compte du mois et du jour de naissance (ajout personnel)

<a id="seq2-1-2"></a>
### 1.2 Opérateurs logiques
| Opérateur | Signification | Exemple   |
| --------- | ------------- | --------- |
| `and`     | ET            | `p and q` |
| `or`      | OU            | `p or q`  |
| `not`     | NON           | `not p`   |

```python
cond=(56>8)and(6!=9)
print(cond)
# RETOURNE : True
```

**Exercice :** Donner la génération de la personne en fonction de son année de naissance.
```python
a=int(input("Année de naissance : "))
cond1=a>=1965 and a<=1980
cond2=a>=1981 and a<=1996
cond3=a>=1997 and a<=2010
print(f"genX? {cond1}\ngenY? {cond2}\ngenZ? {cond3}")
```

<a id="seq2-2"></a>
## 2. Tests conditionnels
> **Remarque :**
> - Le séparateur `:` est placé après la condition.
> - L'indentation indique les actions à effectuer lorsque la condition est vérifiée.

<a id="seq2-2-1"></a>
### 2.1 Instruction if
```python
if condition:
    instructions
```

**Exercice :** Re-test de majorité, *en fonction de l'année*.
```python
age=2026-int(input("Année de naissance : "))
if age<18:
    print("Mineur")
if age>=18:
    print("Majeur")
```
<a id="seq2-2-2"></a>
### 2.2 Instruction if-else
```python
if condition:
    action_1
else:
    action_2
```
 
**Exercice :** paire ou impaire
```python
number=int(input("Choisir un nombre : "))
if number%2==0:
    print(f"Le nombre {number} est pair")
else:
    print(f"Le nombre {number} est impair")
```
<a id="seq2-2-3"></a>
### 2.3 Instruction if-elif-else
```python
if condition:
    action_1
elif condition_2:
    action_2
# ... autant de blocs elif que nécessaire
else:
    action_n
```

**Exercice :** Test de divisibilité de 2 à 7 d'un nombre entier choisi par l'utilisateur
```python
nombre=int(input("Choisir un nombre entier: "))
if nombre%2==0:
    print(f"{nombre} est divisible par 2")
elif nombre%3==0:
    print(f"{nombre} est divisible par 3")
elif nombre%5==0:
    print(f"{nombre} est divisible par 5")
elif nombre%7==0:
    print(f"{nombre} est divisible par 7")
else:
    print(f"{nombre} n'est pas divisible par 2, 3, 5, 7")
```
> **Note personnelle :** si on choisit `6` on remarque que le programme affiche uniquement que `6 est divisible par 2` et non par 3. En effet quand le programme trouve une condition qui est vérifiée, il ne vérifie pas les autres. Autrement dit pour 6 il s'arrête à divisible par 2. Pour cela il faudrait utiliser des `if` à la place des `elif` pour vérifier chaque condition. Il faudrait aussi remplacer/supprimer le `else` car il se trouverait à la fin de la dernière boucle.

<a id="seq2-2-4"></a>
### 2.4 Instruction match-case
Similaire à `if`-`elif`-`else`. Dès qu'un `case` correspond, les autres `case` ne sont pas évalués.
```python
match element:
    case valeur_1:
        action_1
    case valeur_2:
        action_2
    # ... autant de blocs case que nécessaire 
```

Exemple :
```python
x=2
match x:
    case 1:
        print("x vaut 1")
    case 2:
        print("x vaut 2")
# RETOURNE : x vaut 2
```
Pour tester des conditions avec des opérateurs de comparaison, la syntaxe change légèrement et il faut utiliser un `if`.
```python
case x if x < 2:
```
On peut aussi utiliser `case _:` qui agit un peu comme le `else` (Ajout personnel)


**Exercice :** Programme qui demande quelle opération est associée au symbole `**` en Python.
```python
print("Dans le langage Python, quelle opération est associée au symbole **?\nA. division\nB. multiplication\nC. puissance\nD. division euclidienne\n")
rep=input("Saisir la lettre de votre réponse : ")
match rep:
    case "A":
        print("FAUX")
    case "B":
        print("FAUX")
    case "C":
        print("TU AS TROUVÉ LA BONNE REPONSE")
    case "D":
        print("FAUX")
```

<a id="seq2-3"></a>
## 3. Boucles
- `for`: parcourt les éléments d'un itérable.
- `while`: répète des instructions tant qu'une condition est vraie.

<a id="seq2-3-1"></a>
### 3.1 Boucle `for`
```python
for element in iterable:
    Instruction
```

Exemple :
```python
for i in range(4):
    print(i)
```
- `range(n)`: entier de 0 à n-1
- `range(m, n)`: entier de m à n-1
- `range(m, n, p)`: on va de l'entier `m` à n-1 avec un pas de `p` (Ajout personnel)

**Exercices :** Calculer la somme : $\sum_{k=1}^{2026} \frac{k}{2}$ et le produit: $\prod_{k=1}^{20} k^2$
```python
somme=0
for i in range(1,2027):
    somme+=(i/2)
print(somme)
# RETOURNE : 1026675.5
```
```python
prod=1
for i in range(1,21):
    prod*=i**2
print(prod)
# RETOURNE : 5919012181389927685417441689600000000
```


On peut également parcourir directement une liste grâce aux boucles `for` :
```python
for i in [1,2,3]:
    print(i)
# RETOURNE :
# 1
# 2
# 3
```
```python
for c in "hello":
    print(c)
# RETOURNE :
# h
# e
# l
# l
# o
```
Ajout personnel : on peut aussi parcourir deux listes (ou plus) à la fois avec `zip`:
```python
for i, j in zip(liste1, liste2):
``` 
<a id="seq2-3-2"></a>
### 3.2 Boucle while
```python
while condition:
    instruction
```

Exemple :
```python
i=0
while i < 4:
    print(i)
    i += 1
``` 
> **Attention :** il faut veiller à ce que la condition finisse par devenir fausse afin d'éviter une boucle infinie. (Ajout personnel)
> `break` permet de quitter une boucle. (Ajout personnel)

**Exercice :** Calcul du PGCD
```python
dividende=int(input("Saisir un dividende : "))
diviseur=int(input("Saisir un diviseur : "))
a=dividende
b=diviseur
r=dividende
while r != 0:
    r = a % b
    a = b
    b = r

print(f"{a} est le PGCD")
```

