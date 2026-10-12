---
icon: lucide/split
---
# Le branchement conditionnel
Maintenant que nous savons manipuler des expressions booléenes et des variables booléenes nous pouvons les utiliser pour contrôler l'ordre d'exécution de notre code, ceci se nomme le branchement conditionnel. Prenons l'exemple d'un jeu vidéo où un joueur peut s'acheter un item spécial s'il détient plus de dix pièces. Notre situation s'explique par ce petit diagrame.

``` mermaid
flowchart TB
A[Nombre de pièces] -->|Plus grand ou égal à 10| B(L'item est obtenu)
A --> |sinon| C(L'item n'est pas obtenu)
```
Nous pouvons exprimer ceci en code avec les mots clés `if` qui veut dire *si* et `else` qui veut dire *sinon*.
``` c++
#include <iostream>
int main(){
    int nb_de_pieces{};
    std::cout << "Combien avez-vous de pieces?\n";
    std::cin >> nb_de_pieces;

    if(nb_de_pieces >= 10){ //si on a assez de pieces
        std::cout << "Vous obtenez l'item\n";
    }
    else{ //sinon
        std::cout << "Vous n'avez pas assez de pieces\n";
    }

}
```
> Nous voyons que le programme s'assure que le joueur détient plus de 10 pièces pour se procurer l'item.

## Les mots clés `if`et `else`
Comme vu dans l'exemple précédent pour exécuter une instruction conditionnelle, on écrit `if` on met notre condition booléenne entre parenthèses et on met le code à executer entre accolades.
``` c++
if(condition){
    //ceci sera execute
    std::cout << "Bonjour";
}
```
???note 
    Ici `condition` est de type `bool`; nos apprentissages du chapitre précédents seront donc cruciaux pour ce chapitre. 


Considérons un programme qui détermine le signe d'un nombre (négatif, nul, positif). Le branchement conditionnel peut s'expliquer par ce diagramme.
``` mermaid
graph LR
A[Nombre] ==>|Supérieur à zéro| B{Positif}
A ==> |Zéro| C{Nul}
A ==> |Sinon| D{Négatif}

```
> Remarquez que la troisième condition est implicite : nous spécifions simplement que tout nombre non-nul non positif est nécéssairement négatif.

```c++ title="Ce même programme"
int nombre{10};

if(nombre > 0){
    std::cout << "Le nombre est positif\n";
}
if(nombre == 0){ //notez qu' on prend ==
    std::cout << "Le nombre est  nul\n";
}
else{
    std::cout << "Le nombre est  negatif\n";
}

```


!!! info 
    Notez qu'ici les accolades ne sont pas nécessaires comme on n'exécute qu'une seule instruction (une ligne).

### Le branchement imbriqué
Il est possible d'avoir des conditions embranchées dans des conditions, par exemple :
``` c++
int x {};
if(x > 0){
        if (x < 4){
            std::cout << "x est entre 0 et 4\n";
        }
}

```
Ici notre instruction ne s'exécutera que si la première **et** la deuxième condition sont remplies. Toutefois on peut faire mieux en utilisant les opérateurs logiques vu dans le chapitre précédent. 
``` c++
int x{};
if( x > 0 && x < 4){
    std::cout << "x est entre 0 et 4\n"; 
}

```
> Le programme est ici plus clair et concis.
!!! tip "Conseil"
    Préférez les opérateurs logiques aux conditions imbriquées.


## La condition`else if`
Il est possible d'avoir à exprimer une condition dépendante d'une autre condition. Par exemple si on veut savoir si un nombre est supérieur à 70 ou s'il est supérieur à 60 mais pas à 70. Pour cela on utilise un `else if`.
``` c++
int note{90};
if(note > 85) //cette valeur est tres subjective ;D
    std::cout << "Quel bonne note!\n";

else if(nb > 60) // on utilise else if
    std::cout << "Au moins on passe\n";

```
> "Quelle bonne note"

Remarquons ici que comme la note était plus grande que 85 le programme a dit *Quelle bonne note*, mais il n'a pas dit *au moins on passe*, comme ces conditions sont interdépendantes. Si on n'avait pas utilisé le `else if`, le résultat aurait été différent.

``` c++
int note{90};
if(note > 85) //cette valeur est tres subjective ;D
    std::cout << "Quel bonne note!\n";

if(nb > 60) // on utilise un if simple
    std::cout << "Au moins on passe\n";

```
> Quel bonne note!

> Au moins on passe

Le programme donne ici une réponse assez étrange, mais elle est parfaitement logique. 90 est supérieur à 85, mais aussi à 60, c'est pour cela que les deux branches sont exécutés. En utilisant `else if` on peut dire au programme qu'une seule des deux conditions peut être exécutée, réglant ainsi notre problème.

## Un programme concret
Il est beau de voir l'utilisation théorique du branchement conditionnel, mais il reste inutile si on ne l'utilise pas concrètement. Composons donc un programme qui peut convertir des notes en lettres à des pourcentages.

``` c++
#include <iostream>
int main(){
    int note_pourcentage{};
    std::cout << "Entrez votre note : ";
    std::cin >> note_pourcentage;

    
    char note_lettre{}; //la note est de type charactere

    if(note >= 90)
        note_lettre = 'A';

    else if (note >= 80)
        note_lettre = 'B';

    else if (note >= 70)
        note_lettre = 'C';

    else 
        note_lettre = 'F'; //assumons un monde ou la note de passage est 70 
    
    std::cout << "\nVotre note est " << note_lettre;
}

```
> *  Notre programme compare la note à différents critères pour l'associer à une lettre
> * On utilise `else if` pour spécifier que chaque note peut seulement être associée à une seule lettre.




## Exercises
!!! Question

    Écrivez un programme qui prend un nombre. Si celui-ci est divisible par 3 le programme dit *Fizz*, s'il est divisible par 5 la console affiche *Buzz*. Si le nombre est divisible par 3 et par 5 on a *FizzBuzz*.
    

    ??? info "Réponse"
        ``` c++
        #include <iostream>
        int main(){
            int nombre{}; 
            std::cout << "Entrez un nombre : "\n;
            std::cin >> nombre;

           if(nombre % 3 == 0)
                std::cout << "Fizz";

            if (nombre % 5 ==0)
                std::cout << "Buzz";
        }
        ```

!!! Question

    Écrivez un programme qui prend deux nombres et nous indique dans quel [quadrant](https://en.wikipedia.org/wiki/Quadrant_(plane_geometry)) se trouve le point avec ces coordonées.
    
    > Note : les points des axes ne sont pas sur des quadrants.
    

    ??? info "Réponse"
        ``` c++
        #include <iostream>
        int main(){
            int x{};
            int y {}; 

            std::cout << "Entrez la coordonnée x  : "\n;
            std::cin >> x;

            std::cout << "Entrez la coordonnée y  : "\n;
            std::cin >> y;

           if(x > 0 && y > 0)
                std::cout << "Quadrant 1";

           if (x < 0 && y > 0)
                std::cout << "Quadrant 2";

            if (x < 0 && y < 0)
                std::cout << "Quadrant 3";

            if (x > 0 && y < 0)
                std::cout << "Quadrant 4";

            else
                std::cout << "Pas de quadrant";
        }
        ```