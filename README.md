# CPP-Module-01

![C++](https://img.shields.io/badge/C++-98-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![Top language](https://img.shields.io/github/languages/top/NicolasBaudoin/CPP-Module-01?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/NicolasBaudoin/CPP-Module-01?style=flat-square)

> Memory allocation, pointers to members, references and switch statements.

Deuxième module du parcours C++ à 42. Zombies, pointeurs/références et pointeurs de fonctions membres. Tout le code suit la norme **C++98**.

---

- [Règles générales](#règles-générales)
- [Exercice 00 — BraiiiiiiinnnzzzZ](#exercice-00--braiiiiiiinnnzzzz)
- [Exercice 01 — Moar brainz!](#exercice-01--moar-brainz)
- [Exercice 02 — HI THIS IS BRAIN](#exercice-02--hi-this-is-brain)
- [Exercice 03 — Unnecessary violence](#exercice-03--unnecessary-violence)
- [Exercice 04 — Sed is for losers](#exercice-04--sed-is-for-losers)
- [Exercice 05 — Harl 2.0](#exercice-05--harl-20)
- [Exercice 06 — Harl filter](#exercice-06--harl-filter)
- [Rendu et évaluation](#rendu-et-évaluation)

## Règles générales

- Compiler avec `c++` et les flags `-Wall -Wextra -Werror`, compatible `-std=c++98`
- Dossiers d'exercices : `ex00`, `ex01`, ..., `exn`
- Classes en **UpperCamelCase**, un fichier de classe par nom de classe
- Pas de fuite mémoire avec `new`/`delete`
- STL (containers/algorithms) interdite avant les Modules 08/09
- `using namespace` et `friend` interdits (sauf mention contraire) → **note = -42**
- `*printf()`, `*alloc()`, `free()` interdits → **note = 0**

---

## Exercice 00 — BraiiiiiiinnnzzzZ

| | |
|---|---|
| **Dossier** | `ex00/` |
| **Fichiers à rendre** | `Makefile`, `main.cpp`, `Zombie.{h, hpp}`, `Zombie.cpp`, `newZombie.cpp`, `randomChump.cpp` |
| **Interdit** | Aucun |

Classe `Zombie` avec un attribut privé `name` et une méthode `void announce(void)` qui affiche :

```
<name>: BraiiiiiiinnnzzzZ...
```

Deux fonctions à implémenter :

- `Zombie* newZombie(std::string name);` — crée un zombie sur le **tas** et le retourne
- `void randomChump(std::string name);` — crée un zombie sur la **pile**, le fait annoncer

Le but : déterminer quand allouer sur la pile ou sur le tas. Le destructeur doit afficher un message avec le nom du zombie détruit.

---

## Exercice 01 — Moar brainz!

| | |
|---|---|
| **Dossier** | `ex01/` |
| **Fichiers à rendre** | `Makefile`, `main.cpp`, `Zombie.{h, hpp}`, `Zombie.cpp`, `zombieHorde.cpp` |
| **Interdit** | Aucun |

```cpp
Zombie* zombieHorde( int N, std::string name );
```

Alloue **N zombies en une seule allocation**, les initialise tous avec le même nom, retourne un pointeur sur le premier. Tester `announce()` sur chacun. Ne pas oublier `delete[]` et vérifier les fuites mémoire.

---

## Exercice 02 — HI THIS IS BRAIN

| | |
|---|---|
| **Dossier** | `ex02/` |
| **Fichiers à rendre** | `Makefile`, `main.cpp` |
| **Interdit** | Aucun |

Une variable `string` initialisée à `"HI THIS IS BRAIN"`, un pointeur `stringPTR` et une référence `stringREF` vers elle. Afficher :

1. Les 3 adresses mémoire (variable, pointeur, référence)
2. Les 3 valeurs (variable, `*stringPTR`, `stringREF`)

Objectif : démystifier les références comme autre syntaxe pour manipuler des adresses.

---

## Exercice 03 — Unnecessary violence

| | |
|---|---|
| **Dossier** | `ex03/` |
| **Fichiers à rendre** | `Makefile`, `main.cpp`, `Weapon.{h, hpp}`, `Weapon.cpp`, `HumanA.{h, hpp}`, `HumanA.cpp`, `HumanB.{h, hpp}`, `HumanB.cpp` |
| **Interdit** | Aucun |

- `Weapon` : attribut privé `type` (string), `getType()` (référence constante), `setType()`
- `HumanA` : reçoit son `Weapon` **par référence** au constructeur, toujours armé
- `HumanB` : ne reçoit **pas** de `Weapon` au constructeur, peut ne pas en avoir (pointeur), `setWeapon()`
- `attack()` affiche : `<name> attacks with their <weapon type>`

> Réfléchir avant de coder : dans quel cas préférer un pointeur, dans quel cas préférer une référence vers `Weapon` ?

Vérifier l'absence de fuites mémoire.

---

## Exercice 04 — Sed is for losers

| | |
|---|---|
| **Dossier** | `ex04/` |
| **Fichiers à rendre** | `Makefile`, `main.cpp`, `*.cpp`, `*.{h, hpp}` |
| **Interdit** | `std::string::replace` |

Programme prenant 3 paramètres : `<filename> <s1> <s2>`. Copie le contenu de `<filename>` dans `<filename>.replace` en remplaçant chaque occurrence de `s1` par `s2`.

- Manipulation de fichiers **en C++** uniquement (pas de `fopen`/`fread`/...)
- Toutes les méthodes de `std::string` sont autorisées, **sauf `replace`**
- Gérer les erreurs / entrées invalides
- Fournir ses propres tests

---

## Exercice 05 — Harl 2.0

| | |
|---|---|
| **Dossier** | `ex05/` |
| **Fichiers à rendre** | `Makefile`, `main.cpp`, `Harl.{h, hpp}`, `Harl.cpp` |
| **Interdit** | Aucun |

Classe `Harl` avec 4 méthodes **privées** : `debug()`, `info()`, `warning()`, `error()`, et une méthode publique :

```cpp
void complain( std::string level );
```

**Obligatoire : utiliser des pointeurs sur fonctions membres** pour dispatcher selon `level` — pas de cascade `if/else if`. Fournir des tests montrant Harl se plaindre sur chaque niveau.

---

## Exercice 06 — Harl filter

| | |
|---|---|
| **Dossier** | `ex06/` |
| **Fichiers à rendre** | `Makefile`, `main.cpp`, `Harl.{h, hpp}`, `Harl.cpp` |
| **Interdit** | Aucun |
| **Optionnel** | Le module passe sans cet exercice |

Filtre le niveau de log : affiche tous les messages **à partir du niveau donné** (DEBUG < INFO < WARNING < ERROR) en paramètre.

```
$> ./harlFilter "WARNING"
[ WARNING ]
...
[ ERROR ]
...
$> ./harlFilter "n'importe quoi"
[ Probably complaining about insignificant problems ]
```

**Obligatoire : utiliser un `switch`**. Nommer l'exécutable `harlFilter`.

---

## Rendu et évaluation

- Rendu sur le dépôt Git ; seul le contenu du repo est évalué
- Une petite modification peut être demandée en soutenance pour vérifier la compréhension réelle du code
