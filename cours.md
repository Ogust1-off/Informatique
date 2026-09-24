# Informatique S3 - Cours Python

# Séquence 1: "Premiers pas en Python"
## 1 Base
### 1.1 Variable identifiant et affectation
DEF: Une **variable** c’est l’association d’un **identifiant**  à un objet stocké en mémoire
Cette opération d’association est appelée **affectation** (`=`) (`a=1 b=2`)
Attention: 
1) (`=`) n’est pas symétrique! (~~1=a~~ NON!)
2) mise à jour des var
            
**Exercice:**
```python
a=1
b=2
```
Pour inverser les deux:
```python
c=a
a=b
b=c
```

Remarque: 
1. Bien choisir l'identifiant des var (s, somme)
2. Identifiants admissibles (pas de `@`,`#`, ...)(on ne commence pas par un nombre)
            
### 1.2 Commentaire
en python `#` pour une ligne et `"""` pour un § `"""`

### 1.3 Entrée/Sortie
Affichage: `print()`

Multi-affichage:
```python
a=1
b=2
c=3
print(a,b,c)
RETOURNE: 1 2 3
```

Affichage de chaîne de caractère: `print("Hello World!")`

Requête user: `input()`

Attention: input renvoie **toujours** une chaine de caractère

Exemple:
```python
name=input("Quelle est votre nom")
print(name)
```

## 2 Types et opérations
DEF: En python chaque obj a un **type**. Il indique la nature de l'obj manipulé et les **operation** que l'on peut lui appliquer.

fonction type: `print(type("Hello World"))` -> str

### 2.1 Nombres

- int: entier relatif
- float: nbr décimaux
- complex: avec j pour i en variable

Exemple:
```python
z= 3+4j
print(z.real, z.imag)
```

Opération arithmétique:
```
+ addition
- sous
* multiplication
** puissance
/ div
// division eucli..
% modulo (rest de la div eucli)
```

**Exercice:**
```python
a,b=21,5
a/b -> 4.2 en float
a//b -> 4 en int
a%b -> 1 en int
```

**Opération affectations:**
incrémentation, décrémentation
```
a+=1
b-=2
```

**Exercice:** Bob à 4 note: 10, 15, 13, 8 Moyenne:
```python
moy=10
moy+=15
moy+=13
moy+=8
moy/=4
print(moy)
RETOURNE: 11.5
```
        
### 2.2 Booléens
bool -> True, False

opération de comparaison:

| == | égale à |
| < | inf |
| > | sup |
| <= | inf égal |
| >= | sup égal |
| != | dif de |

**Exercice:**
```
a,b -> True,False
a==b ->False
a!=b ->True
```
        
### 2.3 Chaînes de caractère, conversion de type et f-strings
type -> 'str'
concaténation: fusion de 2 chaine de str -> +

**Exemple:**
```python
txt1="Hello"
space=" "
txt2="World"
print(txt1+space+txt2)
```
fonctionne aussi en +=

conversion de type: conerttie le contenue du () en truc de devant
```python
int()
float()
complex()
str()
```

**Exemple:**
```python
age=20
print("J'ai "+str(age)+" ans")
```
```python
age=20.0
print(f"J'ai {age:.0f} ans") -> J'ai 20 ans
```

**Exercice:**
```python
p = float(input("Ton poids (kg)?"))
t = float(input("Ta taille (m)?"))
print(f"Ton imc est: {p/(t**2)}")
```

## 3 Debogage
### 3.1 Reflexe
Lire l'erreur et la comprendre
verifier la syntaxe du code
help()
google

### 3.2 Erreurs courantes
ErrorSyntax
ErrorName

# Séquence 2: Logique, tests conditionnels et boucles
## 1 Logique
### 1.1 Conditions logiques
```python
cond_1 = 5**2 < 2**5
cond_2 = 36 ==89
print(cond_1, cond_2)
RETOURNE: True False
```
**Exercice:** demander année naissance user si majeur True else False
```python
a=int(input("année de naissance "))
calc=2026-a
cond=calc>=18
print(f"Majeur? {cond}")
```

### 1.2 Opérateur logiques
| and | ET |p and q |
|  or|  OU|p or q  |
| not |  NON| not p |
```python
cond=(56>8)and(6!=9)
print(cond)
RETOURNE: True
```

**Exercice:** Generation de la personne
```python
a=int(input("année de naissance "))
cond1=a>=1965 and a<=1980
cond2=a>=1981 and a<=1996
cond3=a>=1997 and a<=2010
print(f"genX? {cond1}\ngenY? {cond2}\ngenZ? {cond3}")
```

## 2 Tests conditionnels
**Remarque**:
* séparateur :
- indentation

### 2.1 Instruction if
```python
if condition:
    instructions
```

**Exercice:** Re-test de majorité
```python
age=2026-int(input("année de naissance "))
if age<18:
    print("Mineur")
if age>=18:
    print("Majeur")
```
 
### 2.2 Instruction if-else
```python
if condition:
    action_1
else:
    action_2
```
 
**Exercice:** paire ou impaire
```python
number=int(input("Choisir un nombre "))
if (number%2)==0:
    print(f"Le nombre {number} est pair")
else:
    print(f"Le nombre {number} est impair")
```

### 2.3 Instruction if-elif-else
```python
if condition:
    action_1
elif condition2:
    action_2
# ... autant de blocs elif que nécessaire
else:
    action_n
```

**Exercice:** Test de divisibilité de 2 à 9
```python
Instruction pas très claire mais c'est simple si l'instruction est claire
```

### 2.4 Instruction match-case
```python
match element:
    case valeur_1:
        action_1
    case valeur_2:
        action_2
```

Exemple:
```python
x=2
match x:
    case 1:
        print("x vaut 1")
    case 2:
        print("x vaut 2")
```

**Exercice:** prog qui demande: Dans le langage Python, quelle opération est associée au symbole `**`?  
```python
print("Dans le langage Python, quelle opération est associée au symbole **?\nA. division\nB. multiplication\nC. puissance\nD. division euclidienne\n")
rep=input("Saisir la lettre de votre réponse: ")
match rep:
    case "A":
        print("FAUX")
    case "B":
        print("FAUX")
    case "C":
        print("TU A TROUVER LA BONNE REPONSE")
    case "D":
        print("FAUX")
```

## 3 Boucles
- `for`: on sait combien de fois itérer
- `while`: itérer suivant une condition

### 3.1 Boucle for
```python
for element iterable:
    Instruction
```

Exemple:
```python
for i in range(4)
    print(i)
```
`range(n)`: entier de 0 à n-1 - `range(m,n)`: entier de m à n-1 

**Exercice:** Somme de 1 à 2026 de k/2 et Produit de 1 à 20 de k^2
```python
sum=0
for i in range(1,2027):
    sum+=(i/2)
print(sum)
```
et
```python
prod=1
for i in range(1,21):
    prod*=i**2
print(prod)
```

On peut aussi l'écrire sous forme de liste:
```python
for i in [1,2,3]:
    print(i)
RETOURNE:
1
2
3
```
```python
for c in "hello":
     print(c)
RETOURNE:
h
e
l
l
o
```

### 3.2 Boucle while
```python
while condition:
     Instruction
```

Exemple:
```python
i=0
while i<4:
     print(i)
     i+=1
``` 

**Exercice:** calcule PGCD
```python
dividande=int(input("Saisir un dividende: "))
diviseur=int(input("Saisir un diviseur: "))
a=dividande
b=diviseur
r=dividande
while r!=0:
    r=a%b
    a=b
    b=r
    print(a)
print(f"{a} est le PGCD")
```

# Séquence 3: Liste

## 1 Liste
```python
L=[1,2,3,4]
print(L)
RETOURNE: [1,2,3,4]
```
ou
```python
L=["Hello",25,True,0]
```

Les listes possèdent leur propre type: `list` et donc la fonction de conversion associer: `list()`
```python
L=list("Hello")
print(L)
RETOURNE: ['H', 'e', 'l', 'l', 'o']
```

```python
print(list(range(5)))
RETOURNE: [0,1,2,3,4]
```

Format par compression
```python
L=[i for i in range(5)]
print(L)
``` 

Librairie `random` importation: `import random`
`random.randint(m,n)` renvoie un nombre aléatoire entre m et n

**Exercice:** générer et afficher une liste qui affiche des 20 entiers aléatoire entre 0 et 10
```python
import random
liste=[random.randint(0,10) for i in range(20)]
print(liste)
```
*correction perso avec des truc pas vue:*
```python
import random
liste=[]
for i in range(20):
    liste.append(random.randint(0,10))
print(liste)
```

### 1.1 Parcours d'une liste
Taille: `len()`

`[12,32,76,98,15]' 12: indice 0, 32: indice 1, ... , 15: indice 4. MAIS AUSSI: 15: indice -1, 98: indice -2, ..., 12: indice -5.

`L[i]` pour le nombre d'indice i d'une liste L

```python
L=[12,32,76,98,15]
print(L[1],L[-4])
RETOURNE: 32, 32
```

**ATTENTION**:
1) élément ≠ indice
2) indexation croisante vas de 0 a len(L)-1

**Exercice:** Demander a un utilisateur un nombre, créer une liste qui va de 0 au nombre de l'utilisateur, faire la somme de tous les termes de la suite.
```python
nombre=int(input("Choisire un nombre "))
liste=[]

#Ma version
"""for i in range (nombre):
    liste.append(i)
"""
#Version cours
liste=[i for i in range(nombre)]

somme=0
for i in range (len(liste)):
    somme+=liste[i]

print(f"La somme de 0 à {nombre} est: {somme}")
```

### 1.2 Opérations sur les listes
Concaténation: `+`
```python
L1=[1,2,3]
L2=[1,5,6]
print(L1+L2)
RETOURNE: [1,2,3,1,5,6]
```

```python
print([1]*20)
RETOURNE: [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
```

`L1==L2': si L1 exactement égale a L2 on revoie `True` sinon `False`

Copie: `L.copy()`
Exemple:
```python
L=[1,2,3]
M1=L
M2=L.copy()
L[0]=100
print(M1,M2)
RETOURNE: [100, 2, 3] [1, 2, 3]
```

**Exercice:** Afficher la suite de Fibonacci dans un liste de 0 a 19 (Fn+2=Fn+1+Fn, ∀n)
```python
liste=[0,1]
somme=0

#Ma version
"""
for i in range(2,20):
    liste.append(liste[i-1]+liste[i-2])
"""
#Version avec les truc du cours
for n in range(18):
    liste=liste+[liste[n+1]+liste[n]]

print(liste)
RETOURNE: [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987, 1597, 2584, 4181]
```

### 1.3 Modification de listes

```python
L=["h","e","l","l","o"]
L[1]="a"
print(L)
RETOURNE: ['h', 'a', 'l', 'l', 'o']
```

Ajout d'éléments:
`append(élement)`, `insert(indice,élément)`

Exemple:
```python
L=["h","e","l","l","o"]
L.append("!")
L.insert(2,"e")
print(L)
RETOURNE: ['h', 'e', 'e', 'l', 'l', 'o', '!']
```

**Exercice:** Testeur de palindrome
```python
mot=input("Saisir un mot en minuscule: ")
listeMot=[]
for i in mot:
    listeMot.append(i) # Transformation du mot en une liste avec chaque caractère indépendant
palindrome=True

for j in range(len(mot)//2):
    if listeMot[j]!=listeMot[-(j+1)]: #Comparaison des caractères : 1er avec le dernier, 2e avec l'avant-dernier, ... avec la méthode des indices croissants et décroissants
        palindrome=False
        # On pourrait rajouter un break pour sortir immédiatement de la boucle quand on sait que ce n'est pas un palindrome.

if palindrome==True:
    print(f"Le mot {mot} est un palindrome.")
else:
    print(f"Le mot {mot} n'est pas un palindrome.")
```
