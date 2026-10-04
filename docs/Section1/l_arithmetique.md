---
icon: lucide/sigma
---
# L'arithmétique

En programmation il peut être utile d'effectuer des calculs mathématiques. Le C++ nous donne donc la possibilité de le faire avec des opérations arithmétiques. Ici le code vaut mille mot.

```  c++
int expression { 5 * (4 - 2) };
std::cout << expression; //On affiche le résultat à l'écran
```
>On remarque que l'écran affiche *10* et non `5 * (4-2)`, c'est-à-dire que le compilateur peut effectuer nos calculs comme le ferait une calculatrice. 

Regardons un exemple plus pratique de ceci. Imaginons que nous dévelopions un jeu vidéo, où le score du joueur doit être augmenté.

``` c++
int score {0}; //on store le score dans une variable
// ... plus loin
score = score + 1;
```
Ici on assigne au `score` la valeur actuelle de celui-ci plus 1, donc on l'augmente de un. D'ailleur il existe un racourci pour faire ceci (même deux).

``` c++
int nb1 {2};
nb1 += 4; //on ajoute quatre à la valeur de nb1

int nb2 {3};
++nb2; //on augmente la valeur de nb2 une fois.

std::cout << "Nombre 1 : " << nb1 << "\n Nombre 2 : " << nb2;

```

>- Pour le premier racourci, `nb1` était égal à deux. On l'a ensuite ajouté à *4* (comme si on faisait `nb1 = nb1 + 4`) pour obtenir 6.

>- Pour le deuxième racourci on à utilisé l'opérateur d'incrément pour passer de *3* à *4*.

## Les opérateurs

Comme on a vu, pour faire nos opérations arithmétiques on a utilisé des *opérateurs*, notamment l'opérateur d'addition (`+`), d'affectation d'addition (`+=`) et d'incrément (`++`). Toutefois le C++ nous offre beaucoup plus d'options. Voici une petite liste des opérateurs du C++ qu'on utilisera en arithmétique.



| Nom | Symbole | Résultat |
| -------- | :------: | -------- |
| Addition | `+` | Somme de deux nombres |
| Soustraction | `-` | Différence de deux nombres |
| Multiplication| `*`| Produit de deux nombres|
| Division| `/`| Quotient de deux nombres|
| Modulo | `%`| [**Reste**][reste] de la division de deux nombres|

[reste]: https://fr.wikipedia.org/wiki/Reste "Par exemple le reste de la division 7 / 2 est 1 puisque 2 * 3 + 1 = 5."

??? note
    Il existe des opérateurs qui ne sont pas dédiés à l'arithmétique. Il seront donc couverts dans une prochaine section.

**Un exemple**
``` c++
double pi { 3.14 };
int nombre {9};
int nb2 {4};

std::cout   << "9 x pi = " << nombre * pi 
            << "\n9 / pi = " << nombre / pi
            << "\n9/ 4 = " << nombre / nb2;
```
Ici on effectue des opérations sur des nombres de manière assez habituelle; cependant, on dirait qu'il y a une erreur. Le programme affirme que `9 / 4 = 2`, alors que ce n'est clairement pas vrai, la réponse réelle devrait être un nombre décimal. Le programme *se trompe* car il considère que `nombre` et `nb2` sont des nombres entiers (type `int`).

!!! Warning "Attention"
    La division de deux entiers en C++ donnera toujours un autre entier.

Donc, il enlève la partie décimale, ce qui n'arrive pas lorsqu'on divise un nombre par pi, comme celui-ci est décimal.

**La solution**
``` c++
double nombre {9.0}; //changer le type à double (décimal)
int nb2 {4};

std::cout << nombre / nb2; //2.25
```

## Les opérateurs d'affectations
