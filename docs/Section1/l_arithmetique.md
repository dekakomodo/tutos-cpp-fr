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

## Un exemple
Imaginons que nous dévelopions un jeu vidéo, où le score du joueur doit être augmenté. Voici comment on pourrait le faire, grâce à une variable et aux opérations.

``` c++
int score {0}; //on store le score dans une variable
// ... plus loin
score = score + 1;
```
Ici on assigne au `score` la valeur actuelle de celui-ci plus 1, donc on l'augmente de un. D'ailleur il existe un racourci pour ajouter une valeur à une variable(même deux).

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

### Des opérations entre plusieurs variables
Au lieu de se contenter d'additioner des variables avec des nombres, pourquoi ne pas additioner des variables avec d'autres variables ou de les multiplier entre elles?


``` c++ title="Un exemple et un problème"
double pi { 3.14 };
int nombre {9};
int nb2 {4};

std::cout   << "9 x pi = " << nombre * pi  // le produit de deux variables
            << "\n9 / pi = " << nombre / pi
            << "\n9/ 4 = " << nombre / nb2;
```
Ici on effectue des opérations sur des nombres de manière assez habituelle; cependant, on dirait qu'il y a une erreur. Le programme affirme que `9 / 4 = 2`, alors que ce n'est clairement pas vrai, la réponse réelle devrait être un nombre décimal. Le programme *se trompe* car il considère que `nombre` et `nb2` sont des nombres entiers (type `int`).

!!! Warning "Attention"
    La division de deux entiers en C++ donnera toujours un autre entier.

Donc, il enlève la partie décimale, ce qui n'arrive pas lorsqu'on divise un nombre par pi, comme celui-ci est décimal.


``` c++ title="La solution"
double nombre {9.0}; //changer le type à double (décimal)
int nb2 {4};

std::cout << nombre / nb2; //2.25
```

### Les opérateurs d'affectations
Comme discuté  [au dessus](#un-exemple), il est possible d'affecter à une variable le résultat d'une opération sur elle même. On l'avait fait avec l'addition, mais sachez que ce racourci fonctionne avec toutes les opérations. 
``` c++
int n1 {10};
n1 += 2;//n1 = 10 + 2 = 12
n1 *= 4; //n1 =  12 * 4 = 48

n1 /= 6; //n1 = 48 / 6 = 8
n1 %= 3; //n1 = 8 % 3 = 2

```
>Dans l'exemple ci-dessus, les commentaires expliquent l'opération effectuée sur n1. On ajoute **2**, puis on multiplie par **4**, on divise par **6** et puis on trouve le reste avec **3**.

## Exercices
Pour tester vos connaisances voici deux petits exercices.
``` c++ title="Un exercice classique"
double nombre{7.5};
nombre = nombre - 1.5;
nombre *= 3;

```
!!! Question

    Quel est la valeur de `nombre`?

    ??? info "Réponse"
        **18**. On enlève 1.5 à 7.5 pour obtenir 6. On multiplie 6 par 3 pour avoir 18.

***

``` c++ title="Question Piège"
int decimal{14};
decimal /= 4;
decimal + 2;

```
!!! Question

    Quel est la valeur de `decimal`?

    ??? info "Réponse"
        **3**. La question comprenait deux pièges malins. Premièrement, lorsqu'on divise `decimal` par 4 comme celui-ci est un nombre entier (`int`) le C++ retire la portion décimale du résultat (On 3 au lieu de 3,5). Deuxièmement, la ligne `decimal + 2;` ne fait absolument rien! On demande simplement au C++ de trouver la valeur de `decimal` plus deux, et puis de ne pas l'utiliser.

***

!!! Warning "Attention"
    Il est crucial de distinguer une expression comme `x+2` de `x +=2`. La première n'a aucun effet seule, tandis que la deuxième augment réellement la valeur de x de 2.