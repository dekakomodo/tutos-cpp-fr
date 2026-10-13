---
icon : lucide/repeat
---
# Les boucles `while`
Jusqu'à date, les programme que nous avons conçu sont plus ou moins linéaires. Dépendamment de nos conditions notre programme peut choisir un branche. Toutefois, ce que nous allons apprendre dans cette leçon nous permettra d'exécuté des instructions à répétition. Par exemple écrivons un programme qui liste tous les nombres de 1 à 10.

``` c++ title="De façon linéaire"
#include <iostream>
int main(){
    std::cout << 1 << 2 << 3 << 4 << 5 << 6 <<7 << 8 << 9 << 10;
}

```
> Certes ce programme fonctionne, il n'est peu pratique; s'il fallait lister tout les nombres de 1 à 100 on y serait pour une étérnité.

## La notion de boucle
Une boucle `while` nous permet d'éxecuter du code tant qu'une condition est respectée.

``` c++
while (condition){
    //faire quelque chose
    std::cout << "Bonjour\n";
}

```
Ce code est lu dans cet ordre : 

1. Le compilateur vérifie si la condition est respectée (`condition == true` )
2. Le code dans les accolades est exécuté
3. On répète l'étape 1.

Nous pouvons donc afficher tout les nombres de 1 à 10 facilement.

``` c++
#include <iostream>
int main(){
    int compteur{1};
    while(compteur <= 10){
        std::cout << compteur << '\n';
        ++compteur 
    }
}
```
> * On initialise un compteur
> * Tant que celui-ci est inférieur ou égal à 10 on affiche sa valeur à l'écran
> * On augmente le compteur de 1 avec l'opérateur d'incrément (`++`)

Pour certains un schéma facilite la compréhension.

``` mermaid
graph TD
    B[Initialiser  compteur à 0]
    B --> C{ Vérifier la condition
     i <= 10}
    C -- Oui --> D[Afficher le compteur]
    D --> E(Augmenter le compteur)
    E --> C
    C -- Non --> F([Quitter la boucle])


```
### Les boucles infinies
En mettant une condition toujours vraie on peut avoir une boucle qui s'éxecute indéfiniment. La condition la plus simple qui est toujours vraie est simplement le mot clé `true`.

```c++
while(true){
    std::cout << "Bonjour\n";
}

```
> Ce programme dit *Bonjour* éternellement


!!! Warning "Attention"
    Il faut faire très attention à ne pas accidentellement mettre une condition toujours vraie dans une boucle, sinon le programme sera pris dans une boucle infinie.

Une boucle infinie peut être un outil utile mais seulement si on peut la quitter et que c'est un choix délibéré.

### Quitter une boucle
Nous pouvons quitter tout type de boucles avec le mot clé `break`. En couplant cette capacité avec le branchement conditionnel nous pouvons utiliser une boucle infinie sans danger.

```c++
#include <iostream>
int main(){
    int nombre{};
    while(true){ //boucle infinie
        std::cout << "Devinez le nombre secret\n ";
        std::cin >> nombre;
        if(nombre == 3)
            break; //On quitte la boucle
        std::cout << "Reesayez!\n";
        
    }
    std::cout << "Bravo";

}

```
Notre programme demande un nombre à répétition jusqu'à ce que l'utilisateur devine 3.