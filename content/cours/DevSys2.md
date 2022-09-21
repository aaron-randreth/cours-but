---
title: "DevSys2"
date: 2022-09-07T08:06:35+02:00
---

Processus en mémoire : Programme en exe

[Stack] [  |  ] [  v  ] [     ] [     ] [     ] [  ^  ] [  |  ] [heap ] [data ]
[text ] -> stores machine code

# Hiérarchie de la mémoire 

- cache -> megaoctets, rapide, chère, volatile -> utile pour les operations
  processeurs, ralenti moins que la RAM
- RAM -> giga-octet, rapide, prix moyen, volatile
- SSD -> tera-octet, lent, non volatile, cheap

# Adresse logique/physique

- Adresse symbolique: Adresse dans le prg
- logique: générée par la CPU
- physique: Adresse vue par la mémoire et registstres d'adresses de la meme
  (base + logique = physique en mem continue)

- MMU (mem management unit) fait le passage entre l'adresse logique et la
  physique

Logique est dans le prg, pour passer de celle là à la physique le CPU fait un
calcul. Comme le prg ne peut connaitre les addresses libres à l'écriture, elle
abstrait cela en adresse logique, qui sont transformé par le CPU en adresses
physiques "réelles".

# Espaces d'adressage 

## Le principe 

Pendant que des processus font des I/O, qui sont lent, le CPU travaille sur les
autres processus. Cette augmentation de vitesse introduit, l'espace d'adressage:
ensemble des adresses qu'un processus peut utiliser en mem. Cela évite l'acces,
l'allocation, etc... d'un processus sur la mem utilisé par un autre 

Avoir plusierus app en mémoires: 

## Solution originele  

### son principe 

- Chaque proc a son propre espace d'adressage, pour éviter les conflits entre
  eux
- elle peut déterminer si une adresse appartient à son espace en vérifiatn
  qu'elle est: pour adresse A **base** <= A < **base+limite**
- la **base**: plus petite adressage physique légale (similaire à la première
  adresse d'un tableau en C)
- la **limite (étendue)**: taille totale de l'espace physique auquel le proc a
  accès

### Ses défaults 

Cette méthode fonctionne si la mem physique peut contenir tous les procs, ce qui
n'est pas le cas.

## Les nouvelles solutions 

- Segementation et/ou pagniation 
- virtual mem
- swaping 

# Allocation mémoire 

La mem physique est séparée en deux, une partie pour l'OS et une pour les procs
utilisateurs.

## Stratégies d'allocation continue 

- First fit: 1er bloc libre de taille suffisante, 50% des blocs sont
  inutilisables dus à la fragmentation
- Best fit: plus petit bloc libre de taille suffisante, crée de nombreux espaces
  mem libres inutilisables
- worst fit: plus grand bloc libre

L'allocation continue mène à de la fragmentation, les zones mémoires continues
vont laisser des espaces trop petit et inutilisables. On obtient aussi des blocs
de taille différente, ce qui rend le prog plus complexe. Une solution à cela
consiste à déplacer les zones mémoires, en les réallouant pour renplire les
petits espaces libres. Cela peut mener à des freeze. L'allocation continue reste
cenpendant une mauvaise solution.

## Allocation par segementation 

- Segementation: méchanisme permettant mappage entre l'adresses logique et
  physique.

Les bouts de mémoires avec des méthodes de fonctionnement différents ont des
segements diff. Un espace d'adressage logique peut être rep en un ensemble de
plusieurs seg.

### Le principe 

- adresse logique: <no. du segement, offset>, <s, d>
- la table mappe une adresse logique (en deux dim) en une adresse physique

- s: index qui pointe sur une entrée dans la table des segements. On obtient la
  base (debut du seg) et la limite.
- d: déplacement/offset, 0 <= d < limite la mémoire récupère d + base =
  physique.

### Ses défaults 

- fragmentation externe au segement: pas suffisament de place pour un nouveau
  proc, les blocs libres ne sont pas contigus. Besoin de defrag

## Allocation par pagination 


### Le principe Le pb des outres solutions était ceux de l'allocation contigus,
et l'utilisation de tailles différentes.

On découpe la mem physique en blocs de taille fixe, appelés **frames** (**cadre
de pages**). La mem logique est découpée en blocs de même taille, des **pages**

### Les avantages 

### En pratique 

- adresse logique: <p, d>
- p: num de la page 
- d: offset 

La taille de la page, et du frame, est fixée par le hardware. Elle est définie
en puissance de 2 (pour des questions de facilité de calcul), elle varie entre
512o et 1GO (1024o), et dépends de l'architecture de l'ordi.

## Page + Segment 

On utilise le principe de page en plus de la table des segments, qui contient
seulement l'adresse des pages du procs.

d / T = no.page

## Mémoire virtuelle 

On en stocke pas les proc entièrement en mem, ce qui n'est pas utilisé est
stoqué sur le disque. Le proc peut donc utiliser de la mem plus grande que la
mem physique. On rajoute donc aux pages un bit pour indiquer si elle est sur la
mem centrale. Les mobiles utilisent la mem flash au lieu de la mem centrale.

On appele l'échange des données d'un proc entre la mem centrale et la mem **le
swap**. C'est cependant lent, et prend du CPU.
