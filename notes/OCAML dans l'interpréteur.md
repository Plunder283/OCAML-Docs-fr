#Programmation #Epita #OCAML

# Evaluation d'une fonction dans l'interpréteur OCAML

## Fonction simple :

```ocaml
let func x y z = 
	let v = (2 * x + 3 * y + 2 * z) /7 in
	if x > && y > v && z > v then
		3
	else
	if x > v || y > v then
		2
	else
	1;;
```

`val func : int -> int -> int -> int = <fun>`

Ce qui veut dire que la fonction `f` prends plusieurs arguments en entrée qui sont de type `int` et un argument en sortie qui sera de type `int` aussi (Le dernier type de la chaine sera toujours le type retourné)

## Fonction qui renvoie plusieurs variables :

```ocaml
let func x y z = (x+x, y+y, z+z)
```

`val func : int -> int -> int -> int * int * int = <fun>`

Quand on renvoie une "liste" OCAML va mettre des `*` pour signifier que nous renvoyons plusieurs données en sortie.

## Fonction avec arguments ou types inconnus :

```ocaml
let func x = x;;
```

`val func : 'a -> 'a = <fun>`

Si OCAML n'arrive pas à déterminer le type des arguments en entrée/renvoyé comme dans la fonction ci-dessus l'interpréteur va se contenter de simplement mettre le nom de la variable avec un `'`.
