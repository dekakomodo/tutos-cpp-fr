---
icon : lucide/square-chevron-right
---
# Interagir avec la console
Jusqu'à date, nous avons uniquement affiché certaines choses à la console, c'est-à-dire qu'on a utilisé la console strictement comme une sortie de caractère, un affichage de texte.
``` c++ title="Un retour sur le Hello World"
#include <iostream>
int main(){
    std::cout << "Bonjour!";
}
```
Dans cette section nous allons dissecter le *Hello World* et nous allons apprendre à interagir avec l'utilisateur.
## La sortie de caractères
!!! abstract "Définition"
    La sortie de caractère (*character output* en anglais) est un objet qui nous permet d'afficher du texte à la console.

Cet objet est abbrégé `cout` et nous est fourni par le fichier *iostream*. Lorsqu'on lui applique **l'opérateur de décalage (`<<`)**, on peut afficher du texte. En regardant le *Hello World*, d'abord on demande au C++ de nous donner accès aux définitions de `<iostream>`. Ensuite dans notre fonction `main()` on récupère l'objet `cout` et puis on lui applique l'opérateur de décalage avec notre texte.

### Afficher plusieurs objets
Dans les leçons précédentes, nous avons utilisé des capacitées de l'objet `cout` sans les décrire explicitement. Par exemple, celui-ci peut afficher, des caractères, des chaînes de caractères(texte), des nombres et même la valeur d'une variable.
``` c++
int x {23}
std::cout << 3;
std::cout << 'a'; //on utilise des guillemets simples car il s'agit d'un seul caractère.
std::cout << x;
```
Ici, on n'a pas besoin de récupérer l'objet `cout` pour ensuite afficher du texte. On peut à la place enchaîner des opérateurs de décalage.
``` c++
int x {23};
std::cout << 3 << 'a' << x;
```
Le résultat affiché sera le même.
### Les séquences d'échappement
Les séquences d'échappement permettent d'afficher des caractères auxquels on n'a pas accès. L'exemple le plus courrant est lorsque vient le temps de sauter une ligne. Comme on ne peut pas physiquement sauter une ligne dans notre chaîne de caractère, on utilise le caractère d'échappement `'\n'`.
``` c++ title="La bonne méthode"
std::cout << "Bonjour\n" << "Comment allez-vous?\n"; //on saute une ligne
```
!!! failure "Erreur"
    Si on décide de sauter une ligne manuellement le programme ne compile pas. 
    ``` c++
    std::cout << "Bonjour
    Comment allez-vous?";
    ```

***

Il existe d'autres séquences d'échappements qui peuvent s'avérer utiles.

| Symbole|  Résultat | Utilisation |
| :---     | :----:   | ---:     |
|`\n`     | Saut de ligne   | Très fréquente    |
|`\t`     | Tabulation     | Occasionelle     |
|`\'`      | Guillemet simple  | Fréquente  |
|`\"`      | Guillemet double  | Fréquente  |
|`\\`      | Barre oblique inversée  | Occasionelle  |
|`\0`      | Caractère nul  | Occasionelle  |

## L'entrée de caractère
Maintenant que nous maitrisons la sortie de caractère, attaquons l'entrée. Celle-ci nous permet de recevoir de l'information de notre utilisateur. L'objet que nous utiliserons pour l'entrée est le `cin`.
``` c++ title="L'exemple de base"
#include <iostream>
int main(){
    std::cout << "Enter un nombre : ";
    int reponse{};
    std::cin >> reponse; //On store la réponse dans notre variable
    std::cout << "\nVotre nombre est : " << reponse;
}

```
Ici veuillons noter quelques choses. 

- D'abord, au lieu d'utiliser l'opérateur de décalage gauche (`<<`) on utilise le droit (`>>`), pour storer la réponse.

- Ensuite, notre programme assume que l'utilisateur répondra avec un nombre, si ce n'est pas le cas nous aurons des problèmes. Nous réglerons ceux-ci plus loin dans le cours.

- Enfin, il est également possible de receuillir des données textuelles (chaînes de caractères), mais comme nous n'avons pas encore étudié celles-ci, il vaut mieux en parler plus tard.

## Exercices

!!! Question

    Trouvez l'erreur : 
    ``` c++
    int a{};
    std::cin << a;
    std::cout >> "Vous avez entré " >> a;
    ```

    ??? info "Réponse"
        Les opérateurs de décalages (`<<` et `>>`) sont inversés. `std::cin` utilise `>>` et `std::cout` utilise `<<`.

!!! Question

    Écrivez un programme qui prend un nombre décimal de l'utilisateur et nous indique son carré.
    

    ??? info "Réponse"
        ``` c++
        #include <iostream>
        int main(){
            double nombre{}; //double car c'est un nombre decimal
            std::cout << "Entrez un nombre : ";
            std::cin >> nombre;

            std::cout << "Le carré de " << nombre << " est de " << nombre * nombre <<'\n';
        }
        ```

!!! Example "Défi"

    Écrivez un programme qui calcule l'IMC (indice de masse corporelle) de quelqu'un selon la formule
     
    IMC = Masse (kg) / (Taille (m))<sup>2</sup>
    

    ??? info "Réponse"
        ``` c++
        #include <iostream>
        int main(){
            double masse{};
            double taille{};
            std::cout << "Entrez la masse du sujet en kg : \n";
            std::cin >> masse;

            std::cout << "Entrez la taille du sujet en m : \n";
            std::cin >> taille;

            std::cout << "L\'IMC du sujet est de : " << masse / (taille * taille);
        }
        ```



