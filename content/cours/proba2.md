---
title: "Variables aléatoires discrètes"
date: 2022-09-08T11:05:26+02:00
---

Ex:


Sur 10 dés, quel est la proba d'obtenir 3 fois la valeur 6 ?

On prend la valeur aléatoire X = nb de 6. Ici X peut avoir 10 valeur,
un 6, deux 6, trois 6 etc... X suis donc une loi binomiale. X compte un binaire
,et donc une loi de bernouli, si on ne lance le dés qu'une seule fois. Avec
X(succès) = "obtient 6" et X(échec) = "n'obtient pas 6". On répète cette
éperience 10 fois de manière indépendante.

On obtient une loi binomiale:

```
p = P(succès) = 1/6, et n = 10; donc X ~ B(10, 1/2). On recherche k = 3.

P(X = 3) = (10 3) * (1/6)^3 * (1-1/6) ^ (10 - 3)

```
