---
title: "Devellopement système: Introduction"
date: 2022-09-02T11:37:22+02:00
tags: ["Ressource R03.05 - Programmation système"]
---

# Objectifs 

"Comprendre la structure d'une application client-server, et les mécanismes bas niveaux, mis en oeuvre dans une application multitâches."

<!--- TODO: vérifier ces définitions --->

**Processus**: l'ensemble des données stoqué par l'OS pour effectuer une action.

**Multitâches** (multithreaded): utilisation de plusieurs coeurs pour effectuer une action.

**Multiprocessus**: utilisation de plusieurs processus pour effectuer une action.

Découverte du développement d'applications **multi-processus**, traiter les problèmes de **synchronisations**, utiliser des outils de communications internes aux processus (interne à une même machine), mais aussi externe (entre plusieurs machines, via les **sockets**) via les APIs de transport.

# Système de fichiers 

## Gestion des fichiers en c 

### Gestion des erreurs 

```C
#include <errno.h>
```
Introduit une variable global errno qui contient le code erreur du dernier appel primitif système.

### Affichage des erreurs 

```C
#include <stdio.h>

int perror(const char* erreur);
```

### Création et suppression de répertoire 

```C
#include <sys/stat.h>

/* 
  returns 0 en cas de succès, et -1 dans errno contient le code d'erreur 
*/
int mkdir(const char* path, const char* mode);
int rmdir(const char* path);

```

### Contenu d'un répertoire 

```C
//définit dans <sys/dirent.h>

struct dirent { // Enregistrement qui permet de gérer un répertoire 
    // Charactérisation du fichier 
    ino_t d_ino; // numéro d'inode
    unsigned char d_type; //type du ficher
    char d_name[256]: // nom du fichier

    // Infos de contrôle 
    off_t d_off; // décalage jusqu'à la diren suivent
    unsigned short d_reclen; // longueur de cet enregistement 
  }
```

### Ouverture et fermeture d'un répertoire 

<!--- TODO: write down the functions and imports for this --->

### Lecture d'une entrée d'un répertoire 

```C
#include <sys/dirent.h>

// Ne retourne pas d'erreur, NULL à la fin de lecture 
struct dirent *readdir(DIR* dirp);
```

Ne pas `free` le pointeur dirent, le système s'occupe de sa déallocation et un `free` manuel peut être problématique.
