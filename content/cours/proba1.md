---
title: "Probalités: Introduction"
date: 2022-08-29T10:09:02+02:00
tags: ["Ressource R03.08 - Probalités"]
math: true
---

<!--- TODO: Polish those notes --->

# Objectifs du module 

* modélistion aléatoire 

# Utilisations possibles de la probalité 

## Calculer la valeur approchée d'une intégrale 

On place N nombres de points dans le carré, et on compte le nombre de points
qui se situent sur la courbe. La proportion de point va nous donner une idée de l'aire.
e.g si la courbe a une aire de 0.6 dans le carré de 1 alors on va retrouver cette proportion
de points sous cette courbe.

## Calculer la popularité d'une page web (Random Web Surfer) 

En cliquant aléatoirement sur des liens et enn se déplaçant de page en page, on peut déterminer
la popularité de la page selon la proportion.

# Bases de la théorie des probalités 

## Termes de base 


* $\Omega$ : "Univers" = l'ensemble de toutes les possibilitées 
* $\mathbb{P}$ : "(mesure de ) probalité" qui associe à chaque évenement E (avec E $\in \Omega$ ) une valeur entre 0 et 1

## Exemples 

$\Omega$ = { Tous les dices }

P({1,2}) =  1/3

E = {1,2}

E appartient à $\Omega$


Ici le dice de 1 est un évènement aléatoire.

$\Omega$ appartient à $\Omega$ est un évènement certain.

{dice 1} et {dice 2} sont incompatible 

```
A : {résultat > 2 } -> P(A) = 4/6 = 2/3
B : {est pair} -> P(B) = 1/2

A intersection B = "4 ou 6" -> P(A $\cap$ B) = 2/3 * 1/2 = P(A) * P(B) 

```

Comme cette proba est !=  de 0 alors A et B sont indépendant.


C = {résultat => 2 } -> P(C) = 5/6
C $\cap$ B = {2, 4, 6} -> B

P(B) sachant C = P(B $\cap$ C) / P(C) = ( 1/2 ) / 5/6 = 3/5


# Variable aléatoire 


