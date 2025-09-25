#Programmation #Epita #OCAML 

# 1. If/Else - Structure conditionnelle de base

La structure `if/else` permet d'exécuter du code selon qu'une condition soit vraie ou fausse.

# Syntaxe de base :
```ocaml
if condition then
	(* code si vrai *)
else if condition then
	(* code si autre condition vraie*)
else
	(* code si toutes les conditions sont fausses*)
```

⚠️ **Important** : En OCAML, le `if` est une expression qui doit toujours retourner une valeur. Les deux branches (`then` et `else`) doivent avoir le même type.
## Exemples pratiques :
```ocaml
let is_positive x = 
  if x > 0 then 
    true 
  else 
    false;;

let describe_number x =
  if x > 0 then
    "positif"
  else if x < 0 then
    "négatif"  
  else
    "zéro";;
```
# 2. Match Case

Le match case est une alternative au `if else` qui permet de gérer facilement la logique de notre programme en gérant de façon exhaustive toutes les issues possible à une condition.

Dans un `match`, les conditions sont testées séquentiellement : on effectue le premier test, puis le deuxième, et ainsi de suite jusqu'à trouver une correspondance.

Il est possible de faire des match case en OCAML comme ceci :

```ocaml
let func x = match x with
	| 0 -> false
	| 1 -> true
	| y when y <= 10 -> false
	| _ -> true;; (*Cas par défaut (équivalent à un else)*)
```

Voyons ce que fait cette fonction lorsque nous l'exécutons avec différents arguments :

```ocaml
val func : int -> bool = <fun>

# func 0;;
- : bool = false

# func 1;;
- : bool = true

# func 5;;
- : bool = false
  
# func 12;;
- : bool = true
```

Ici OCAML compare la valeur passée à la fonction `func` avec plusieurs "cas" que nous allons détailler :

## Cas simples : 

```ocaml
| 0 -> false
| 1 -> true
```

Si on traduit ces lignes on obtient quelque chose comme : "Si x = 0 alors return false", "Si x = 1 alors return true".

## Cas avec variable :

```ocaml
| y when y <= 10 -> false 
```

Lorsqu'une variable est utilisée comme ceci elle prends la valeur de la variable passée dans le match (dans notre cas y = x).
Si on avait pas mis le mot clé `when` mais simplement `y -> false` la condition serait toujours exécutée.

## Default Case :
```ocaml
| _ -> true;; (*Cas par défaut (équivalent à un else)*)
```
Dans un `match` le underscore correspond au cas par défaut, c'est à dire que peut importe la valeur à comparer
# Warning