---
title: "DevSys4"
date: 2022-09-21T08:11:19+02:00
---

# Appels systèmes 

**pipe**: Permet à une comande d'envoyer des données à un autre.

**kill-signal**: envoie et reception d'un signal (le proc va regarder de
regularly un tableau de signaux)

**sockets**: communication à distance

Sous Unix, plusieurs procs lourds peuvent partager la même zone mémoire
(pratique pour la comm inter proc, pas très utilisé)

## Fork() 

Crée un nouveau proc via **duplication**, le processus *père* est dupliqué et crée
un processus *fils*.

```C
#include <sys/types.h>
#include <unistd.h>

pid_t fork(void);

```

Cette fonction a deux valeurs de retour, elle retourne une valeur au fils et une
valeur différente au père. Le père obtient le pid d fils, le fils obtient 0.
Si l'on obtient un -1, erreur de création du fils.

Comme le fork est une duplication, on doit vérifier avec cette valeur de retour
si l'onn est le père ou le fils, et agir en conséquence.

```C

// Son propre ID
getpid();

// Le PID du père
getppid();

```

Comme chaque processus(sauf exception) a un seul père, on peut retrouver
uniquement enregister le pid du fils dans celui du père et obtenir 

Comme fork est une duplication père et fils partagent :
- le même code (text)
- les mêmes descripteurs de fichiers ouverts
- les mêmes variables, mais uniquement celles d'environment et pas les locales

**Side note**: il n'y a pas de variables d'environment globales i.e si l'on
modifie/casse la valeur d'une variables, les autres procs ne vont pas être
affecté.

## Wait() 

Wait élimine les procs zombies, et permet la sync d'un processus sur la
terminaison de ses descendants avec la recup des infos relatives à cette
terminaison.

Wait provoque la suspension du processus appelant judq'a la fin d'**un** de ses
processus fils.

```C
#include <sys/types.h>
#include <sys/wait.h>

pid_t wait(int* status_fils);

```

## Waitpid()

Attends qu'un fils précis se termine.

```C

pid_t Waitpid(pid_t pid, int* status, int options);

```

Run `info pid` for more info.

## Exec() 

La famille d'appel `exec()`  de remplacer le processus appelant par un nouveau, 
avec du nouveau code, de nouvelles données, et une nouvelle pile mais les mêmes
variables, le même pid.

Il ne **crée pas** de nouveau processus.

```C
#include <unistd.h>

// Path to new code source
int execl(const char* path, const char* args, ...);


```

**Rappel**: Chaque proc a dans sa table de fichiers ouverts, les 3 std (in, out, err).

## Flock() 

Verrouillage d'un fichier.

for more advanced info `info fcntl`

- porte sur un descripteur de fichier.
- Verrouillage du fichier en entier
- verou exclusif pour ceux qui écrivent
- verrou partagé pour ceux qui lisent
- verou consultatif (un proc n'est pas obligé de respecter l'indicateur de verrou)

```C

// info flock
int flock(int fd, int operation); 

```

**Note**: `open` renvoie un `int` comme descripteur de fichiers, alors que `fopen` renvoie un `FILE*`.
`open` nous permet d'utiliser `read` and `write`.

`lockf` au un verrou obligatoir
