---
title: "DevSys5"
date: 2022-09-28T08:15:45+02:00
---

```C
#include <unistd.h>

int pipte(int df(2));

fd[0] est ouvert en lecture et fd[1] en écriture

```

Tout ce qui est écrit dans fd[1] est transmis par pipe à fd[0].
Le père et le fils partagent les descripteurs des fichiers du tube.
Quand l'un écrit à une extremité, l'autre peut lire l'autre extremité.

On n'utilise la pipe que dans un sens.

ex:

si fils écrit et père lit, fils doit fermer son fd\[0\] (lecture) et le père doit
fermer son fd\[1\] (écriture).

Si le lecteur est plus rapide que l'écrivain, alors read va hang et attendre l'écrivain.
Si le processus écrivain s'éteint, le read return un 0 comme tout les descripteurs 
en écriture sont fermés.

