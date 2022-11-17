---
title: "Qualité de Developpement"
subtitle: "Cours 1: Éstimer le coût des changements anticipés"
date: 2022-11-09T09:42:09+01:00
---

# Notions étudié 

- Principe SOLID
- Dépendance
- Test Driven Dev

# Prérequis 

- Encapsulation 
- Sous-typage

# Bibliographie 

- Agile software dev (Robert C Martin)
- [Refactoring: Improving the Design of Existing Code (Martin Fowler,
  Addison-Wesley)](refactoring.com/catalog)


## Complexité, coûts et changements 

Principe YAGNI qui chercher àà limiter la complexité, et make features when they
have a good reason to be needed. Changements principaux -> rajouter un cas. Ex:
rajouter un type d'anneau

Coût que l'on chercher à minimiser -> coût "marginal", le changement que l'on va
introduire dans les autres classes en créant cette nouvelle classe. On peut
mesurer cela avec le nombre de classes impacté, la taille de ces classes
impacté, et la stabilité des codes impacté (si les classes elles même changent
beacoup c'est moins grave).

On ne donne pas trop de détails, en fesant abstraction pour donner de la
flexibilité pour les changements qu'on ne peut pas prévoir.

Dépendance de contenant -> contient des classes etc qui ne concernent pas la
fonction centrale du packetage.

Pas de transitivité des dépendances. Si A utilise B et B utilise C, A n'utilise
pas forcément C.
