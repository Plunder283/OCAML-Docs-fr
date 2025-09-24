#Programmation #Epita #OCAML 
# Fonction classique :
Une fonction classique en OCAML se définit avec le mot clé `let` suivi du nom de la fonction, de ses paramètres, et de son corps.

```ocaml
let func x = x+2;;

func 2;;

(*Execution du code*)
val func : int -> int = <fun>
- : int = 4
```
Dans cet exemple, nous définissons une fonction nommée `fonction` qui prend un paramètre `x` de type `int` et retourne `x+2`. 
Le compilateur OCAML infère automatiquement que cette fonction a le type `int -> int`, ce qui signifie qu'elle prend un entier en entrée et retourne un entier.
# Fonction anonyme :
Une fonction anonyme (aussi appelée fonction lambda) est une fonction sans nom que l'on peut définir dans notre code OCAML. Ces fonctions sont particulièrement utiles pour des opérations courtes et ponctuelles, ou comme arguments d'autres fonctions.

Pour créer une fonction anonyme on utilise le mot clé `function` :

```ocaml
(*Cette fonction n'a pas de nom donc on ne peut pas l'appeler*)
function x -> x+2;;

(*Execution du code*)
- : int -> int = <fun>
```
Bien que cette fonction soit créée, elle n'est pas directement utilisable car elle n'a pas de nom pour l'appeler.

## Call une fonction anonyme :
Pour appeler cette fonction il y a deux méthodes possibles :

### Méthode 1 : L'appeler directement :
On peut appliquer directement la fonction anonyme à un argument en l'entourant de parenthèses :
```ocaml
(function x -> x+2)(2);;

(*Execution du code*)
- : int = 4
```

### Méthode 2 : Lui donner un nom :
On peut assigner la fonction anonyme à une variable pour pouvoir la réutiliser :
```ocaml
let foo = function x -> x+2;;

foo 2;;

(*Execution du code*)
val foo : int -> int = <fun>
- : int = 4
```

Cette deuxième méthode est équivalente à une définition de fonction classique. En effet, `let foo = function x -> x+2` produit exactement le même résultat que `let foo x = x+2`.

## Fonction Anonyme avec arguments multiples :
Lorsqu'on veut créer une fonction anonyme avec plusieurs arguments, on utilise le principe de curryfication (currying). Chaque fonction ne prend qu'un seul argument et retourne une nouvelle fonction qui attend l'argument suivant :
```ocaml
let anon = function x -> function y -> x + y;;

anon 3 2;;

(*Execution du code*)
val anon : int -> int -> int = <fun>
- : int = 5
```
Dans cet exemple, `anon` est une fonction qui prend un entier `x` et retourne une fonction qui prend un entier `y` et retourne `x + y`. Le type `int -> int -> int` se lit comme `int -> (int -> int)`.
## Mot clé `fun`

On peut aussi utiliser le mot clé `fun` à la place du mot clé `function` pour créer des fonctions anonymes de manière plus concise. La différence principale est que `fun` permet de spécifier directement plusieurs paramètres :

```ocaml
let x = fun x -> x+2;;
x 3;;

(*Execution du code*)
val x : int -> int = <fun>
- : int = 5
```

**Comparaison `fun` vs `function` :**
- `fun x y -> x + y` est équivalent à `function x -> function y -> x + y`
- `fun` est plus pratique pour des fonctions simples avec plusieurs paramètres
- `function` est nécessaire quand on veut utiliser le pattern matching
# Fonction avec Pattern Matching :
Le pattern matching permet de créer des fonctions qui se comportent différemment selon la valeur de leur argument. C'est une fonctionnalité très puissante d'OCAML qui remplace avantageusement les structures conditionnelles dans de nombreux cas :
```ocaml
let func1 = function
	| 1 -> "Hi"
	| 2 -> "Hallo"
	| 3 -> "Hello World!"
	| _ -> failwith "Mauvais Argument";;

func1 3;;

(*Execution du code*)
val func1 : int -> string = <fun>
- : string = "Hello World!"
```
Dans cet exemple :
- La fonction `func1` examine la valeur de son argument
- Si l'argument vaut 1, elle retourne "Hi"
- Si l'argument vaut 2, elle retourne "Hallo" 
- Si l'argument vaut 3, elle retourne "Hello World!"
- Pour toute autre valeur (`_` est un motif qui capture tout), elle lève une exception avec `failwith`
## Fonction avec Pattern Matching et avec Plusieurs Arguments :
On peut combiner pattern matching et fonctions à plusieurs arguments pour créer des comportements complexes. Voici un exemple d'une calculatrice simple :
```ocaml
let func1 = function
	| "Add" -> (function x -> function y -> x + y)
	| "Sub" -> (function x -> function y -> x - y)
	| "Mul" -> (function x -> function y -> x * y)
	| "Div" -> (function x -> function y -> x / y)
	| _ -> failwith "Wrong Arguments";;
	
func1 "Add" 2 8;;
func1 "Sub" 10 8;;
func1 "Mul" 2 6;;
func1 "Div" 4 2;;

(*Execution du code*)
val func1 : string -> int -> int -> int = <fun>
- : int = 10
- : int = 2
- : int = 12
- : int = 2
```
Cette fonction fonctionne en deux étapes :
1. **Premier argument** : Elle examine la chaîne de caractères pour déterminer quelle opération effectuer
2. **Arguments suivants** : Elle retourne une fonction qui prend deux entiers et effectue l'opération correspondante

Par exemple, `func1 "Add"` retourne une fonction d'addition, et `func1 "Add" 2 8` applique cette fonction d'addition aux nombres 2 et 8.

Le type `string -> int -> int -> int` indique que la fonction prend une chaîne de caractères, puis deux entiers, et retourne un entier.
