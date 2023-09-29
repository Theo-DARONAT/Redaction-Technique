---
title: "ReRAM, ou le futur de la mémoire depuis 1970"
summary: "La Resistive Random Access Memory est une technologie de mémoire non-volatile se basant sur le phénomène de résistance.
Plus compact et beaucoup moins énergivore que les autres mémoires concurrentes, elle est une très bonne candidate pour le futur des objets connectés."

date: 2023-09-25T14:41:00+02:00

author: "DARONAT Théo"

tags: ["ReRAM", "mémoire", "news"]

## Show the Table Of Content
showToc: true

## Enable math support
math: true

## If it's draft (true), it will not be published
draft: false
---


## De quoi parle-t-on ?

Nous allons aborder ici un sujet de recherche actuellement mené par plusieurs
acteurs comme IBM, Samsung ou Intel, et de son potentiel pour l’avenir de l’informatique.

La **ReRAM** ou **RRAM**, pour **Resistive Random Access Memory**, est un type de mémoire
se basant sur le phénomène de **résistivité**.

Mais contrairement à ce que son nom pourrait sous-entendre, la ReRAM se sépare
également de la RAM « classique » par le fait que sa mémoire soit **non-volatile**.
Autrement dit pour les non-initiés : Quand on cesse de l’alimenter en courant,
les données restent.


## Comment ça fonctionne ?

Comme dit précédemment, tout se base sur le système de résistivité.

Une cellule (l’endroit où l’on stocke l’information sous forme de bit
(‘0’ ou ‘1’) physique) est composée de trois couches : deux couches extérieures
composées de métal et jouant le rôle d’**électrode** et une centrale à base
d’**oxyde métallique**.

Ce métal est un matériau conducteur, le courant peut facilement passer entre
deux morceaux liés.
L’oxyde métallique, quant à lui, est un **matériau isolant** dit **dialectrique**
(ne contenant pas de charge électrique).

C’est grâce au procédé d’[**oxydo-réduction**](https://fr.wikipedia.org/wiki/R%C3%A9action_d%27oxydor%C3%A9duction)
(redox), une réaction chimique de laquelle résulte un transfert d'électrons
entre certains matériaux, que la ReRAM prend vie.
Voici une courte vidéo d'une expérience chimique montrant le phénomène de
[**redox**](https://www.youtube.com/watch?v=vK6BPYwS2aw).

Ici, la réaction chimique se concrétise par une impulsion électrique au niveau
des électrodes qui perdent des électrons.
Ces dernier sont récupéré par l'oxyde métalique, créant un filament reliant les
deux électrodes.


Voilà comment cela fonctionne :
- Quand une tension électrique précise est appliquée (tension **Set**) au niveau
  des électrodes, un **filament se crée** dans l’oxyde métallique, reliant
  les deux électrodes, faisant passer la cellule d’un état **très résistant**
  à un état peu **résistant**.
- Et inversement, lorsqu’une autre tension précise est appliquée (tension **Reset**),
le **filament se brise** et la cellule repasse à un état **très résistant**.

C’est la méthode utiliser pour écrire une donnée sur une cellule.

Par exemple, pour le cas de la technologie proposée par l’entreprise
[Weebit](https://www.weebit-nano.com/technology/reram-bitcell/), c’est une
**tension positive ou négative** qui va créer ce phénomène et ainsi faire changer d’état la cellule.

Maintenant que nous avons appris à écrire sur une cellule, comment pouvons-nous
la lire ? En réalité, c’est très simple !

Il suffit d’utiliser une formule servant de base à l’électronique : **`U = R x I`**.

Un courant avec une **faible tension**, suffisamment faible pour ne pas déclencher
le Set ou le Reset, est appliquée et, grâce à la formule ci-dessus, en mesurant
le courant et connaissant la tension on en **déduit l’état de la résistance**.

Mais, on dirait presque du binaire…
Et en effet, ça l’est !
Nous avons notre système de mémoire sur lequel nous pouvons écrire et lire.

### Pour récapituler

L’état de résistance faible (quand le filament est créé,
via une tension Set) représente le ‘1’, le courant arrive facilement à
traverser les deux électrodes.

A l’inverse, l’état de résistance élevé (quand le filament se brise, via une
tension Reset) représente le ‘0’, le courant ne passe presque plus.

Pour lire la mémoire, il suffit de mesurer la résistance pour savoir dans quel état on est.


## Multi-Level Memory

C’est fantastique, nous avons trouvé un moyen plus compliqué de créer une mémoire.
Mais qu’est-ce qui la différencie fondamentalement des autres pour être promue
au rang de révolution, si ce n’est de meilleur performance ?
Le suspense est insoutenable n’est-ce pas ?

Abordons le concept de **Multi-Level Memory**, ou « **mémoire à plusieurs niveaux** » en français.
Contrairement aux autres mémoires, ici la valeur binaire (0 ou 1) n’est pas à
proprement « physique », mais est plutôt **calculée**.
Par exemple la SRAM se base sur une porte logique électronique et la Flash NAND,
quant à elle, se base sur une porte logique physique, chacune n’ayant que **deux
états possibles**.

Dans notre cas, la ReRAM vient augmenter sa résistivité grâce à une certaine
impulsion électrique et la **lecture se fait en calculant cette résistivité**.
Cela veut dire qu’en soit, nous n’obtenons pas un 0 ou un 1, mais une valeur
plus large comme $100\Omega$.

Plus haut, nous évoquions les tensions **Set** et **Reset**.
En réalité, il peut y avoir **différentes tensions Set**, permettant chacune un
niveau différent de résistivité.

On peut avoir, par exemple, un niveau :
- Très résistant (0)
- Résistant (1)
- Peu résistant (2)
- Très peu résistant (3)

Dans ce cas, nous avons **4 niveaux de résistivité**, c’est-à-dire 4 valeurs possibles.

En informatique, un **bit supplémentaire permet d’écrire 2x plus de valeurs**.
Et inversement, pouvoir différencier 2x plus de valeurs sur une cellule signifie avoir **un bit supplémentaire**.
Donc ici nous avons une cellule avec une taille de 2 bits.

Si nous sommes capables de différencier 8 valeurs sur une cellule,
cette dernière possèderait une taille de 3 bits, et ainsi de suite.


Autrement dit, pouvoir lire plusieurs niveaux de résistivité permet de démultiplier
l’espace de stockage d’une cellule, et ainsi multiplier la taille de la mémoire
de la ReRAM sans augmenter sa taille physique.


## Avantages et inconvénients

Voyons maintenant les avantages et les inconvénients que la ReRAM propose.
Quel est le réel intérêt de se compliquer la vie à créer une nouvelle façon de
stocker de la donnée ?

**ATTENTION** : Les données utilisées dans cette partie peuvent être
potentiellement obsolètes car les gros constructeurs ne révèlent rien de leurs
avancés et la recherche autour du sujet est toujours active.
Les données sur lesquelles nous nous appuierons date de 2020 pour la plupart.

Nous allons comparer les caractéristiques de la ReRAM avec la mémoire
[**Flash NAND**](https://fr.wikipedia.org/wiki/M%C3%A9moire_flash),
mémoire non-volatile la plus répandu (carte SD, SSD, etc...).

| Caractéristiques Analysés | Caractéristiques de la ReRAM par rapport à la Flash NAND |
| ------------------------- | ------------------------- |
| Consommation | 20x moins |
| Performance : Lecture | 100x plus rapide |
| Performance : Ecriture | 1000x plus rapide |
| Endurance | Entre 10x et 10⁷x supérieur |
| Dimension | 2x plus dense |
| Rétention | Equivalent (10 ans) |
| Plage d'éfficacité optimale | Entre 50°C et 120°C (La Flash NAND n'en a pas) |

Reprenons ce tableau point par point pour le comprendre :

#### Consommation

Dans un premier temps, l’un des principaux avantages de la ReRAM sur ses
concurrentes est sa **très faible consommation d’énergie**.
Que ce soit en termes de lecture ou d’écriture, la ReRAM est bien moins
énergivore que les autres types de mémoires présents sur le marcher actuellement.

#### Performance

Pour ce qui est des performances, la ReRAM fait partie des mémoires les plus
efficaces avec un temps de lecture et d’écriture **inférieur à 10ns**.

#### Endurance

Niveau endurance, il est possible de réécrire la mémoire de la ReRAM entre
$10^6$ et $10^{12}$ fois.
En comparaison, la mémoire Flash NAND à une endurance de $10^5$ réécritures.

#### Coût, Fabrication et Taille

De part ses **matériaux plutôt simple**, la ReRAM ne sera pas très cher à fabriqué
et est même plus compacte que les autres mémoires.

#### Efficacité et Rétention

Cependant, la ReRAM possède une plage de **température optimale de fonctionnement
allant de 50°C à 120°C**.
La ReRAM possède une durée de rétention de l’information de 10 ans quand elle
est dans ses conditions optimales (aux allant-tours de 80°C),
ce qui est équivalent à celle de la NAND.


### Pour récapituler

La ReRAM est en de nombreux points très performante, que ce soit la consommation
d’énergie, les performances de lecture et d’écriture ainsi que son endurance.

Tout ceci est pondéré par une zone de température optimale allant
de 50 à 120°C.


## Les possibilités pour le futur des technologies

Alors pourquoi n'est-elle pas encore sur le marché ?

C'est majoritairement dû à un problème de stabilité au niveau du stockage.
Les matériaux dont sont composées les cellules peuvent être altérés avec le
temps et ainsi détériorer les données stockées.
C'est l'un des principaux axes de recherches actuel sur le sujet.

Mais dans le cas où ce problème serait résolu, quels pourraient être ses
applications ?

### Cache de CPU

L’une de ses utilisations pourrait être de servir de cache au CPU, voir même de
fournir un cache par cœur.

Actuellement, ce qui est utilisé pour du cache est principalement de la
[SRAM](https://en.wikipedia.org/wiki/Static_random-access_memory),
un type de mémoire volumineux et coûteux mais avec de très grandes performances.

La ReRAM est 25 fois plus compacte, ce qui pourrait permettre d’agrandir le
cache et même de pouvoir associer un cœur de CPU avec son cache dédié.
De plus, le fonctionnement du CPU pourrait maintenir la température idéale de
fonctionnement de la ReRAM, et ainsi, avoir ses performances optimales.

Cependant, il reste encore plusieurs points à améliorer pour que la ReRAM
soit réellement intéressante dans ce cas de figure.

Que ce soit au niveau des performances, principale raison de l’utilisation de
la SRAM, où cette dernière est environ 10x supérieur ou au niveau de son
endurance qui est nettement inférieur, la SRAM ayant une endurance $>10^{16}$.

### Capteurs et objets connectés

L’un des principaux enjeux pour l’avenir des objets connectés est l’autonomie.
Il est normal de ne pas avoir envie de recharger son pot de fleur connecté
tous les deux jours.

La ReRAM pourrait aider à pallier ce problème notamment grâce au fait qu’elle
soit beaucoup moins énergivore que les autres types de mémoire.
De plus, son aspect très compact et sa **Multy Level Memory** pourrait permettre
une bien plus grande capacité de stockage.

La montre connectée à plusieurs To d’espace de stockage ne semblent plus si loin.


### Disque Dur et Data Center

De par sa non-volatilité et sa compacité, la ReRAM est tout indiquée à être
utiliser comme espace de stockage ultra compacte.

Son utilisation dans des data centers pour remplacer les mémoires de même type
semble parfaite.
En plus des avantages sités dans l’exemple ci-dessus qui s’appliquent aussi ici,
les data centers produise une grande quantité de la chaleur, et c’est exactement
ce qu’aime la ReRAM pour fonctionner dans des conditions optimales.
Permettant ainsi de réduire leur taille, leur consommation ainsi que de gagner
en efficacité.

Malgré tout, si vous n’avez pas besoin de stockage de masse pour sauvegarder
vos photos de vacances ou n’êtes pas forcément séduit par l’idée d’avoir un
pot de fleur connecté, la ReRAM pourrait tout de même trouver un intérêt chez vous.
Le faible coup des matériaux semble diriger la ReRAM vers un prix bas et ainsi
rentre l’espace de stockage (USB, disque dur, …) plus accessible.


## Conclusion et ouverture
Comme nous l’avons vu, la ReRAM est une technologie très prometteuse apportant
avec elle une nouvelle technologie : le **Multi Level Memory**.

Surpassant ainsi la mémoire non-volatile la plus utilisée actuelle que ce soit en
performance, en endurance ou en consommation.

Cependant elle a besoin d’être aux allant-tours des 80°C pour fonctionner
de manière optimale.

Nous n’avons pas vu tous les cas d’usages possibles, nous nous sommes contentés
de voir les cas qui pourrait directement faire parti de la vie de tout un chacun.
Par exemple, l’application à la simulation de
[neurones](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9220758)
est très intéressante !


**Cependant !** Gardez à l’esprit que les recherches autour de la ReRAM sont
encore actives.
Tout ceci peut s’avérer dépassé et obsolète d’ici quelques mois voire années.

Enfin, la ReRAM n’est pas le seul type de mémoire en développement ayant du
potentiel.
Quid de la
[STT-MRAM](https://www.techtarget.com/searchstorage/definition/MRAM) ?

Restez attentifs et soyez sur vos gardes car le futur entraperçu en 1970
risque d’arriver plus tôt que prévu.


## Approfondir

1. [Oxydo-réduction](https://fr.wikipedia.org/wiki/R%C3%A9action_d%27oxydor%C3%A9duction)
2. [Vidéo redox](https://www.youtube.com/watch?v=vK6BPYwS2aw)
2. [Mémoire Flash](https://fr.wikipedia.org/wiki/M%C3%A9moire_flash)
3. [SRAM](https://en.wikipedia.org/wiki/Static_random-access_memory)
4. [MRAM et STT-MRAM](https://www.techtarget.com/searchstorage/definition/MRAM)
5. [Utilisation de la ReRAM pour la simulation de réseau de neurones](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9220758)
(document scientifique)


## Bibliographie

1. “[Resistive Random Access Memory (RRAM): an Overview of Materials, Switching Mechanism, Performance, Multilevel Cell (mlc) Storage, Modeling, and Applications](https://doi.org/10.1186/s11671-020-03299-9)”,
by Furqan Zahoor, Tun Zainal Azni Zulkifli and Farooq Ahmad Khanday
2. Article from [Lumenci](https://www.lumenci.com/post/reram)
3. Crossbar Technology : [ReRAM Advantage](https://www.crossbar-inc.com/technology/reram-advantages/)
4. “[Multi-Level Control of Resistive RAM (RRAM) Using a Write Termination to Achieve 4 Bits/Cell in High Resistance State](https://hal-lirmm.ccsd.cnrs.fr/lirmm-03377249)”,
by Hassen Aziza, Said Hamdioui, Moritz Fieback, Mottaqiallah Taouil, Mathieu Moreau, Patrick Girard, Arnaud Virazel, Karine Castellani-Coulie
5. “[Robust and reliable ReRAM-based non-volatile sequential logic circuits in deeply-scaled CMOS tehnologies](https://pastel.hal.science/tel-03701635)”,
by Natalija Jovanovic

