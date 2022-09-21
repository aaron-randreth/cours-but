---
title: "ProgSys2"
date: 2022-09-14T14:15:29+02:00
draft: true
---

processus: programme en excécution 
les acteurs: text(code) -> compilation -> execution 

1) make (cc .c -o )

2) l'OS est en charge de:
  - l'allocation des ressources mémoires 
  - gestions des I/O
3) On peut reperer une donnée avec son déplacement (on commence par la base)
4) Il faut comparer le déplacement avec la limite
  - si déplacement < limite -> ok
  - Sinon processus écrit ailleurs -> erreur de segmentation -> arrêter le processus
5) *base = 100, limite = 50, déplacement = 45 (Ok)
   *base = 100, limite = 50, déplacement = 51 (erreur)
6) adresse physique: base + deplacement = 145

espace d'adressage: 

début -> fin

base -> base + limite 1

= {100 .. 149}

7) problèmes  ?
Les segements ayant des tailles diff
-> l'arrêt d'un processus résulte en espace mémoire libre inexploitable -> "tous" (petit espace de mémoire libre) -> la fragmentation externe
