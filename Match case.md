#Programmation #Epita #OCAML 

Le match case est une alternative au `if else` qui permet de gérer facilement la logique de notre programme en gérant de façon exhaustive toutes les issues possible à une condition.

Dans un match case les conditions sont exécutée de manière linéaire donc on effectue le premier test, puis le deuxième et ainsi de suite...

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
# Warning