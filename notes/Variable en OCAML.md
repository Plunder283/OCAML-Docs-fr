#Programmation #Epita #OCAML

# Variable Globale

Pour déclarer une variable globale en OCAML il suffit d'utiliser le mot clé `let` comme suit :

```ocaml
let variable = 3;;
```

Cette variable pourra être réutilisée plus tard dans le code.

# Variable Temporaire 

## Mot clé `in`

Le mot clé `in` permet de faire des variables "locale" ou temporaire :

```ocaml
(*Pour faciliter la compréhension ce code doit être écrit dans la console OCML*)
let var = 3;;

let var = 6 in var+3;;

var;;
```

Si j'exécute ce code :
``
```ocaml
# let var = 3;;
val var : int = 3

# let var = 6 in var+3;;
- : int = 9

# var;;
- : int = 3
```

Ici on voit bien que la variable `var` contient 3 à la fin de l'exécution de notre programme car nous avons utilisé le mot clé `in` dans la deuxième ligne.

### Portée du mot clé `in`

Si je reprends le code de tout à l'heure, que je le modifie comme ceci : 

```ocaml
(*Pour faciliter la compréhension ce code doit être écrit dans la console OCML*)
let var = 3;;

let var = let var = 6 in var+3;;

var;;
```

Si j'exécute ce code :

```ocaml
# let var = 3;;
val var : int = 3

# let var = let var = 6 in var+3;;
val var : int = 9

# var;;
- : int = 9
```

Ici on voit bien que la variable `var` contient 9 au lieu du 3 du début, cela s'explique par le fait que le mot clé `in` se réfère au `let` le plus proche (donc ici le deuxième `let var`)
