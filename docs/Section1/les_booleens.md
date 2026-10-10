---
icon : lucide/toggle-right
---
# Les booléens
Pour l'instant, nos programmes fonctionnent de manière très linéaires. C'est-à-dire que les instructions sont toujours évaluées dans le même ordre. Pour développer des algorithmes plus complexes nous allons devoir séparer notre code selon des **conditions**. Ces conditions sont se qu'on appele des valeurs booléennes.

!!! Abstract "Définition"
    Un booléen est un type de donné qui peut avoir une valeur vraie ou fausse.

``` c++ title="Des variables booléennes"
bool vrai {true}; 
bool faux {false};
```
> * En C++ le type `bool` est utilisé pour créer une variable booléenne
> * Les littéraux `true` et `false` sont utilisé pour spécifier si une valeur est fausse.

Vu ainsi les booléens ont l'air complètement inutile, cependant leur importance est primordiale; c'est juste que nous n'allons pas manuellement les définir comme vrai ou faux.

## Les expressions booléennes
Considérez l'expression suivante : `3 < 5`. Elle est évidemment vraie, trois est inférieur à cinq, elle a donc la valeur `true`. On peut faire une observation similaire avec une variable.
``` c++
#include <iostream>
int main(){
    int nombre {3};
    std::cout << std::boolalpha << (nombre < 5); //true

}
```
> * Le programme affiche *true* à la console, comme 3 est plus petit que 5.
> * De façon générale, on peut comparer des valeurs à l'aide des opérateurs de comparaison.

??? info "Info sur std::boolalpha"
    Dans l'exemple ci-dessus nous avons utilisé `std::boolalpha` , un nouvel objet. Celui-ci dit simplement à la console d'afficher les booléens comme `true` ou `false`. Par défaut le C++ les affiches comme par 1 (true) ou 0 (false).

### Les opérateurs de comparaison
Les opérateurs de comparaisons nous permettent de tirer une valeur booléenne d'une comparaison.

| Symbole|  Nom| Exemple |
| :---     | :----:   | ---:     |
|`<`     | Inférieur   |`3 < 4`    |
|`>`     | Supérieur   | `5 > 2`     |
|`<=`      | Inférieur ou égal  | `2 <= 4`  |
|`>=`      | Supérieur ou égal  | `4 >= 4`  |
|`==`      | Égal | `65 == 65`  |
|`!=`      | N'est pas égal  | `-3 != 3`  |

!!! warning "Attention"
    Ne confondez surtout pas le symbole `=` avec le symbole `==`. Le premier sert à changer la valeur d'une variable, le deuxième sert à comparer deux valeurs.

Comme une expression de comparaison peut être vraie ou fausse, il est normal qu'on puisse assigner sa valeur à une variable booléene.

``` c++
#include <iostream>
int main(){
    int temperature{20};
    bool fait_froid {temperature <= 10}; //une valeur tres subjective ;)
    std::cout << std::boolalpha << fait_froid;
    }
```
> `false`

En utilisant les notions vu dans le chapitre précédent nous pouvons faire un programme qui demande la température chez notre utilisateur pour ensuite qualifier s'il fait froid. Essayez de concevoir ce programme avant de voir la solution.

``` c++
#include <iostream>
int main(){
    double temp{}; //note : la temperature peut etre decimale
    std::cout << "Il fait combien dehors : ";
    std::cin >> temp;

    std::cout << (temp <= 10);
}

```
> Une chose embêtante est que le programme répond simplement par `true`. Ne vous inquietez pas, nous arriverons à le faire dire quelque chose de plus intéréssant dans la prochaine leçon.

### Les opérateurs booléens
Il est possible que nous devrons programmer des conditions composée. Par exemple, on veut savoir si le score d'un joueur est plus petit que 3 mais plus grand que 0.
``` c++ title="Une première tentative"
int score {100}; //un score arbitraire
bool condition {0 < score < 3};
std::cout << std::boolalpha << condition;
```
> La console affiche vrai! Or 100 est clairement plus grand que 3.
!!! bug "Erreur"
    C'était un bel essai, mais malheuresement le C++ ne comprend pas notre notation. Il l'interprète de gauche à droite : `score > 0` est vrai. La valeur `true` est convertie à sa notation décimale (1). On a donc `1 < 3` qui est vrai.

Afin de faire une comparaison correcte nous devons utiliser un *opérateur booléen* qui connecte nos deux affirmation. Celui qu'on cherche est le *et*. Pour celui-ci le symbole `&&` est utilisé.

``` c++ title="La bonne méthode"
int score {100};
bool condition {(0 < score && score < 3)}; //on connecte les deux affirmations
std::cout << std::boolalpha << condition;
```
> On lit une affirmation de ce genre comme *Le score est plus grand que zéro et aussi plus petit que trois*. 

Au lieu d'utiliser le ***et*** logique nous pouvons utiliser le ***ou*** logique avec le symbole `||`. Si on veut prendre la *négation* d'une affirmation on utilise l'opérateur `!`.

``` c++ title="Un exemple"
int nb{6};

bool est_pair {nb % 2 == 0}; //l'operateur modulo est decrit en 1.2
bool est_impair {!est_pair}; //la negation d'un nombre impair

bool divisible_par_3 {nb % 3 == 0};
bool divisible_par_6 {divisible_par_3 && divisible_par_2}; 
```
Nous voyons donc à quel point les expressions booléennes sont intéréssantes. Nous pouvons catégoriser des données qui nous sont fournies en fonction de conditions préalables.
!!! warning "Attention"
    Lorsque vous utiliser les opérateurs `||` et `&&` assurer vous d'utiliser deux caractères. Les opérateurs `|` et `&` ont des fonctions complètement différentes et seront donc couvert dans une prochaine leçon.

Cette leçon ne comportera pas de questions, profitez-en bien :wink:.