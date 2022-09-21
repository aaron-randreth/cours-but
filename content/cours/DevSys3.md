---
title: "DevSys3"
date: 2022-09-14T08:10:56+02:00
draft: true
---

# Création d'un processus 

- Init du système: (lors de l'amorçage de l'OS)
- Exécution d'un appel sys de création de proc par un proc en cours d'exe (sys
  call: **fork**)
- user request
- appel en gros

# Fin d'un processus 

- Arrêt normal (volontaire): appel sys **exit**
- Arrêt pour erreur (vollontaire): exe d'une instruction illégale, d'une réf
  memoire inexistance ou div par 0
- Arrêt pour erreur fatale (involontaire): compilation d'un prog inexistant (gcc
  foo.c -o foo)
- le proc est arrêté par un autre proc (involontaire): appel système kill

# État d'un processus 

- new: le processus est en cours de création
- running: les instructions s'executent 
- waiting: attend un évènt e.g I/O from the user
- ready: prêt pour être affecté à un processeur 
- terminated: finit son exe

## Processus zombie 

Tout proc a un proc père, il doit envoyer une valeur pour indiquer qu'il a
terminé. Si le proc a finit, mais n'a pas envoyé de valeur il est un **zombie**.
Il n'est plus en exécution mais existe tjrs et n'est pas terminé.

# Concept de thread 

- unité de base de l'utilisation d'un processus 

- le concept de thread permet a plusieurs threads d'exécution de partager des
  ressources pour travailler ensemble, afin d'acomplir une tâche donnée.
  Est seulement utile pour les **machines multi-coeurs**.

- les threads autorisent les exécutions multiples dans le même environnement de
  processus. Ils partagent donc le même espace mémoire, ce qui rend
  l'implementation plus difficile.

## Attributs d'un thread 

- indentificateur et état 
- compteur ordinal
- ...

## Ressources partagé 

...

## Avantages 

- Un thread est plus rapidement crée (100x)
- Superposition de 2+ activités (traitement proprement dit, et E/S)
- La comm entre eux est plus simple et rapide 
- Partage de ressources: par défaut la mem et les ressources du mem proc sont
  partagé
- Prog plus efficace: Très utiles pour les sys multi-processeur -> vrai
  parallélisme 

## POSIX Threads 

**Pthreads**:

- id
- ...

pthread_create: nouveau thread
pthread_exit: termine le thread 
pthread_join: attend la fin du thread 

# Parallélisme 

## Ressources non partagable 

Problème posé par une manip non atomique d'un ressource non partageable.

**manipulation atomique**: operation materiel qui ne peut pas être interropu,
change donc selon les machines. (un OP assembleur est une OP atomique)

On fait du tour à tour

Si le parallélisme est mal fait, on peut avoir du non-déterminisme (suivant
l'ordre d'exe des étapes atomiques, le res peut être différent.)


### Exclusion mutuelle 

un seul proc par ressource à la fois, chaque proc peu acceder à la ressource au
bout d'un temps fini (pas d'attente infinie pour un proc)

- restruction du parallélisme
- utilisation sequentielle de la ressource pour ces processus (donc si trop
  d'accès ressource, plus de parallélisme)
- actions atomiques -> on peut rendre une petite séquence d'action atomique

### Section critique 

On rends atomique un série d'instructions qui ne l'est pas à la base, ce qui
permet d'y appliquer l'exclustion mutuelle.
