#Programmation #Epita #OCAML 

# Fonction classique :


# Fonction anonyme :

Une fonction anonyme (aussi appelées fonction lambda) est une fonction sans nom que l'on peut définir dans notre code OCAML.

Pour créer une fonction anonyme on utilise le mot clé `function` :

```ocaml
(*Cette fonction n'a pas de nom donc on ne peut pas l'appeler*)
function x -> x+2;;

(*Execution du code*)
- : int -> int = <fun>
```

Pour appeler cette fonction il y a deux méthodes possibles :

L'appeler directement :
```ocaml
(function x -> x+2)(2);;

(*Execution du code*)
- : int = 4
```

Lui donner un nom :
```ocaml
let foo = function x -> x+2;;

foo 2;;

(*Execution du code*)
val foo : int -> int = <fun>
- : int = 4
```

Cette deuxième méthode est équivalente à une définition de fonction classique.

## Mot clé `fun`

On peut aussi utiliser le mot clé `fun` à la place du mot clé `function` pour aller plus vite :

```ocaml
let x = fun x -> x+2;;
x 3;;

(*Execution du code*)
val x : int -> int = <fun>
- : int = 5
```



```ocaml
let f= function 
 "1" -> (function (a, b) -> (a + b) / 2)
| "2" -> (function (a, -> if a < b then a else 
| "3" -> (function (a, -> if a > b then a else a
| _ -> failwith "";;
```