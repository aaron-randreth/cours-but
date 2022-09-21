---
title: "Développement efficace - Introduction à la complexité algorithmique"
date: 2022-09-06T13:59:25+02:00
tags: ["Ressource R03.02 - Développement efficace"]
---

# Informations sur le cours 

## Modalités d'évaluation 

- 6 séances d'amphi, TD, TP
- Controle de 30min en amphi à la 3éme scéance
- Un DST

## Notions étudiées 

- Complexité 
- Arbres
- Récursivité 
- Tables de hashage 

## Plan 

2) Notations 

# Cours 

## La théorie de la complexité 

C'est l'étude du temps et de l'espace que prend un algorithmique prends pour résoudre un problème, souvant selon le nombre d'entrées.

**À quoi cela peut servir ?**
-  Comparer les performances de 2 aglos traitant le même pb
- À savoir si le code est *scalable*, utilisable sur le big data avec bcp de données

Nous fesant abstractions de la puissance de la machine et des optimisations des compilateurs pour se concentrer le coût des actions de l'algo en fonctions de n données.

```Toml
Complexité temporelle: Temps CPU/GPU

Complexité spacialle: Ressources mémoire
```

## Mesure la compléxité 

On peut mesurer un nombre important d'opérations pour et extrapoler de cela la complexité.

L'analyse consiste alors a exprimer le nb d'opérations effectuées C(n) comme une fonctions de la taille n des données. 

<!--- TODO: rewrite the equations--->

$$

\sum_{i=1}^{n} * i =  \frac{n * (n + 1)}{2}

$$

## La complexité asymptotique 

<!--- TODO: fill this out --->

C'est l'étude de la complexité des algorithmes quand n (nb de données) tends vers $\infnity$

## Comparaison asympottique 

On étudie une fonction -> $\infnity$ grace à des fonctions plus simples, "connues". 

# Of note 

Complexité temp tjrs > Complexité spacialle, étant donné que pour alouer de la mémoire cela prends du temps, compléxité spaciale augmente quand la temp augmente
