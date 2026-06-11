# Fiche courte — Automates finis

## Version examen

Cette fiche résume les notions importantes sur les **langages** et les **automates finis**.
Elle sert surtout à répondre rapidement aux questions d’examen.

---

# 1. Notions de base

## Alphabet

Un **alphabet** est un ensemble de lettres autorisées.

Exemple :

```text
A = {a, b}
```

Cela veut dire que les mots peuvent être construits seulement avec les lettres `a` et `b`.

---

## Mot

Un **mot** est une suite de lettres prises dans un alphabet.

Exemples sur `A = {a, b}` :

```text
a
b
ab
abba
bbaba
```

---

## Mot vide

Le mot vide se note :

```text
ε
```

Il ne contient aucune lettre.

Donc :

```text
|ε| = 0
```

---

## Ensemble `A*`

`A*` désigne l’ensemble de tous les mots possibles sur l’alphabet `A`.

Si :

```text
A = {a, b}
```

alors :

```text
ε, a, b, aa, ab, ba, bb, aba, ...
```

sont des mots de `A*`.

---

## Langage

Un **langage** est un ensemble de mots.

On écrit :

```text
L ⊆ A*
```

Cela veut dire que `L` est un sous-ensemble de `A*`.

---

## Longueur d’un mot

La longueur d’un mot `w` se note :

```text
|w|
```

Exemple :

```text
w = abba
|w| = 4
```

---

## Nombre de lettres dans un mot

Le nombre de lettres `a` dans un mot `w` se note :

```text
|w|a
```

Le nombre de lettres `b` dans un mot `w` se note :

```text
|w|b
```

Exemple :

```text
w = abba
|w|a = 2
|w|b = 2
```

---

## Complémentaire d’un langage

Le complémentaire de `L` dans `A*` se note :

```text
A* \ L
```

Cela veut dire :

> tous les mots de `A*` qui ne sont pas dans `L`.

---

# 2. Tableau des expressions classiques

| Expression     | Signification en français                                      | معنی ساده                                           |
| -------------- | -------------------------------------------------------------- | --------------------------------------------------- |
| `A`            | alphabet                                                       | مجموعه حروف مجاز                                    |
| `A*`           | tous les mots possibles sur `A`                                | همه کلمات ممکن با حروف `A`                          |
| `ε`            | mot vide                                                       | کلمه خالی، طول `0`                                  |
| `a*`           | zéro ou plusieurs `a`                                          | صفر یا چندتا `a`                                    |
| `b*`           | zéro ou plusieurs `b`                                          | صفر یا چندتا `b`                                    |
| `a+`           | un ou plusieurs `a`                                            | حداقل یک `a`                                        |
| `b+`           | un ou plusieurs `b`                                            | حداقل یک `b`                                        |
| `ab`           | un `a` suivi d’un `b`                                          | اول `a` بعد `b`                                     |
| `a* b+`        | zéro ou plusieurs `a`, puis un ou plusieurs `b`                | اول فقط `a`ها، بعد فقط `b`ها، حداقل یک `b` لازم است |
| `b* a b*`      | zéro ou plusieurs `b`, puis un `a`, puis zéro ou plusieurs `b` | دقیقاً یک `a`                                       |
| `b* a b* a b*` | mots avec exactement deux `a`                                  | دقیقاً دو `a`                                       |
| `A* a A*`      | mots contenant au moins un `a`                                 | حداقل یک `a` دارد                                   |
| `A* b A*`      | mots contenant au moins un `b`                                 | حداقل یک `b` دارد                                   |
| `a A*`         | mots qui commencent par `a`                                    | با `a` شروع می‌شود                                  |
| `b A*`         | mots qui commencent par `b`                                    | با `b` شروع می‌شود                                  |
| `A* a`         | mots qui se terminent par `a`                                  | با `a` تمام می‌شود                                  |
| `A* b`         | mots qui se terminent par `b`                                  | با `b` تمام می‌شود                                  |
| `a A* b`       | mots qui commencent par `a` et se terminent par `b`            | با `a` شروع و با `b` تمام می‌شود                    |
| `A* ab`        | mots qui se terminent par `ab`                                 | با `ab` تمام می‌شود                                 |
| `ab A*`        | mots qui commencent par `ab`                                   | با `ab` شروع می‌شود                                 |
| `(ab)*`        | répétition de `ab` zéro ou plusieurs fois                      | تکرار `ab`: مثل `ε`, `ab`, `abab`                   |
| `(a\|b)*`      | tous les mots sur `{a,b}`                                      | مثل `A*` وقتی `A = {a,b}`                           |
| `A* \ L`       | complémentaire de `L` dans `A*`                                | همه کلمات داخل `A*` که در `L` نیستند                |

> Remarque : ici, `*` veut dire “zéro ou plusieurs fois”, et `+` veut dire “une ou plusieurs fois”.

---

# 3. Automate fini

Un **automate fini** est une machine qui lit un mot lettre par lettre.

À la fin de la lecture, il décide si le mot est :

```text
accepté
```

ou

```text
refusé
```

Un automate contient :

* des états ;
* un état initial ;
* un ou plusieurs états finaux ;
* des transitions.

---

## État initial

L’état initial est l’état où l’automate commence.

On le note souvent avec une flèche :

```text
→ 0
```

Cela veut dire que l’état `0` est l’état initial.

---

## État final

Un état final est un état d’acceptation.

On le note souvent avec une étoile :

```text
* 1
```

Cela veut dire que l’état `1` est final.

Dans les dessins, un état final est représenté par un **double cercle**.

---

## Transition

Une transition indique où aller quand on lit une lettre.

Exemple :

```text
0 --a--> 1
```

Cela veut dire :

> si on est dans l’état `0` et qu’on lit la lettre `a`, alors on va dans l’état `1`.

---

# 4. Automate déterministe

Un automate est **déterministe** si :

> il a un seul état initial, et pour chaque état et chaque lettre, il y a au plus une transition.

## Phrase acceptée en examen

```text
L’automate est déterministe car il a un seul état initial et, pour chaque état et chaque lettre, il y a au plus une transition.
```

---

## Si l’automate n’est pas déterministe

Phrase modèle :

```text
L’automate n’est pas déterministe car, depuis l’état ..., avec la lettre ..., il y a plusieurs transitions possibles.
```

Exemple :

```text
Depuis l’état 0 avec la lettre b, on peut aller vers 0 et vers 1.
Donc l’automate n’est pas déterministe.
```

---

# 5. Automate complet

Un automate est **complet** si :

> pour chaque état et chaque lettre, il y a au moins une transition.

## Phrase acceptée en examen

```text
L’automate est complet car, pour chaque état et chaque lettre, il y a au moins une transition.
```

---

## Si l’automate n’est pas complet

Phrase modèle :

```text
L’automate n’est pas complet car, depuis l’état ..., avec la lettre ..., il n’y a aucune transition.
```

Exemple :

```text
Depuis l’état 1 avec la lettre b, il n’y a aucune transition.
Donc l’automate n’est pas complet.
```

---

# 6. Comment savoir si un mot est accepté ?

Pour savoir si un mot est accepté par un automate, on suit toujours la même méthode.

## Méthode

1. On part de l’état initial.
2. On lit le mot de gauche à droite.
3. On suit les transitions.
4. Si on termine dans un état final, le mot est accepté.
5. Sinon, le mot est refusé.

---

## Exemple accepté

```text
ab : 0 --a--> 1 --b--> 2
```

L’état `2` est final.

Donc :

```text
ab est accepté.
```

---

## Exemple refusé

```text
abb : 0 --a--> 1 --b--> 2 --b--> 0
```

L’état `0` n’est pas final.

Donc :

```text
abb est refusé.
```

---

## Cas spécial du mot vide `ε`

Pour le mot vide `ε`, on ne lit aucune lettre.

Donc on reste dans l’état initial.

* Si l’état initial est final, alors `ε` est accepté.
* Si l’état initial n’est pas final, alors `ε` est refusé.

---

# 7. Décrire le langage reconnu

C’est souvent la question la plus importante.

La question peut être :

```text
Décrire le langage reconnu par cet automate.
```

Ici, il ne faut pas seulement donner des exemples.

Il faut trouver la règle générale des mots acceptés.

---

## Phrases modèles

```text
L’automate reconnaît les mots qui ...
```

ou :

```text
L’automate reconnaît les mots de la forme ..., c’est-à-dire les mots qui ...
```

---

# 8. Méthode pour décrire le langage reconnu

Quand tu vois un automate, fais toujours ces étapes :

1. Regarder l’état initial.
2. Regarder les états finaux.
3. Tester des mots courts : `ε`, `a`, `b`, `aa`, `ab`, `ba`, `bb`.
4. Comprendre le rôle de chaque état.
5. Écrire la règle générale.

---

## Rôles classiques des états

Souvent, les états ont un sens simple.

Exemple 1 :

```text
état 0 = pas encore vu a
état 1 = déjà vu a
```

Exemple 2 :

```text
état 0 = nombre pair de a
état 1 = nombre impair de a
```

Exemple 3 :

```text
état 0 = avant le premier b
état 1 = après le premier b
état 2 = état mort
```

---

# 9. Exemple type 1

## Mots contenant au moins un `a`

Automate :

| État  | a   | b   |
| ----- | --- | --- |
| `→ 0` | `1` | `0` |
| `* 1` | `1` | `1` |

<svg width="720" height="230" viewBox="0 0 720 230" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_ex1" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>
  <line x1="80" y1="115" x2="145" y2="115" stroke="black" stroke-width="2" marker-end="url(#arrow_ex1)"/>
  <circle cx="190" cy="115" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="190" y="122" text-anchor="middle" font-size="22">0</text>
  <circle cx="490" cy="115" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="490" cy="115" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="490" y="122" text-anchor="middle" font-size="22">1</text>
  <path d="M225 115 C310 65, 370 65, 455 115" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex1)"/>
  <text x="340" y="70" text-anchor="middle" font-size="20">a</text>
  <path d="M165 80 C105 20, 275 20, 215 80" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex1)"/>
  <text x="190" y="35" text-anchor="middle" font-size="20">b</text>
  <path d="M465 80 C405 20, 575 20, 515 80" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex1)"/>
  <text x="490" y="35" text-anchor="middle" font-size="20">a,b</text>
</svg>

---

## Analyse

Depuis l’état `0` :

* avec `b`, on reste en `0` ;
* avec `a`, on va en `1`.

L’état `1` est final.

Depuis l’état `1` :

* avec `a`, on reste en `1` ;
* avec `b`, on reste en `1`.

Donc dès qu’on a lu au moins un `a`, on reste dans l’état final.

---

## Réponse examen

```text
L’automate reconnaît les mots qui contiennent au moins une lettre a.
```

---

## Exemples acceptés

```text
a
ba
ab
bbabb
```

---

## Exemples refusés

```text
ε
b
bb
bbbb
```

---

# 10. Exemple type 2

## Mots de la forme `a* b+`

Automate :

| État  | a   | b   |
| ----- | --- | --- |
| `→ 0` | `0` | `1` |
| `* 1` | `2` | `1` |
| `2`   | `2` | `2` |

<svg width="820" height="250" viewBox="0 0 820 250" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_ex2" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>
  <line x1="60" y1="130" x2="125" y2="130" stroke="black" stroke-width="2" marker-end="url(#arrow_ex2)"/>
  <circle cx="170" cy="130" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="170" y="137" text-anchor="middle" font-size="22">0</text>
  <circle cx="410" cy="130" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="410" cy="130" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="410" y="137" text-anchor="middle" font-size="22">1</text>
  <circle cx="650" cy="130" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="650" y="137" text-anchor="middle" font-size="22">2</text>
  <path d="M205 130 C275 85, 305 85, 375 130" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex2)"/>
  <text x="290" y="88" text-anchor="middle" font-size="20">b</text>
  <path d="M445 130 C515 85, 545 85, 615 130" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex2)"/>
  <text x="530" y="88" text-anchor="middle" font-size="20">a</text>
  <path d="M145 95 C85 35, 255 35, 195 95" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex2)"/>
  <text x="170" y="50" text-anchor="middle" font-size="20">a</text>
  <path d="M385 95 C325 35, 495 35, 435 95" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex2)"/>
  <text x="410" y="50" text-anchor="middle" font-size="20">b</text>
  <path d="M625 95 C565 35, 735 35, 675 95" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex2)"/>
  <text x="650" y="50" text-anchor="middle" font-size="20">a,b</text>
</svg>

---

## Analyse

Dans l’état `0`, on peut lire des `a`.

Quand on lit le premier `b`, on va dans l’état `1`.

L’état `1` est final.

Dans l’état `1`, on peut encore lire des `b`.

Mais si on lit un `a` après un `b`, on va dans l’état `2`.

L’état `2` est un état mort.

---

## Réponse examen

```text
L’automate reconnaît les mots composés de zéro ou plusieurs a suivis d’un ou plusieurs b.
```

Autre phrase possible :

```text
L’automate reconnaît les mots qui contiennent au moins un b et qui n’ont plus de a après le premier b.
```

---

## Exemples acceptés

```text
b
bb
ab
aaabb
```

---

## Exemples refusés

```text
ε
a
ba
aba
```

---

# 11. Exemple type 3

## Nombre pair de `a`

Automate :

| État   | a   | b   |
| ------ | --- | --- |
| `→* 0` | `1` | `0` |
| `1`    | `0` | `1` |

<svg width="720" height="270" viewBox="0 0 720 270" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_ex3" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>
  <line x1="80" y1="135" x2="145" y2="135" stroke="black" stroke-width="2" marker-end="url(#arrow_ex3)"/>
  <circle cx="190" cy="135" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="190" cy="135" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="190" y="142" text-anchor="middle" font-size="22">0</text>
  <circle cx="490" cy="135" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="490" y="142" text-anchor="middle" font-size="22">1</text>
  <path d="M225 120 C310 45, 370 45, 455 120" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex3)"/>
  <text x="340" y="55" text-anchor="middle" font-size="20">a</text>
  <path d="M455 150 C370 225, 310 225, 225 150" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex3)"/>
  <text x="340" y="220" text-anchor="middle" font-size="20">a</text>
  <path d="M165 100 C105 40, 275 40, 215 100" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex3)"/>
  <text x="190" y="55" text-anchor="middle" font-size="20">b</text>
  <path d="M465 100 C405 40, 575 40, 515 100" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex3)"/>
  <text x="490" y="55" text-anchor="middle" font-size="20">b</text>
</svg>

---

## Analyse

Avec la lettre `b`, on ne change pas d’état.

Avec la lettre `a`, on change d’état.

L’état `0` est final.

Donc :

```text
0 = nombre pair de a
1 = nombre impair de a
```

---

## Réponse examen

```text
L’automate reconnaît les mots qui contiennent un nombre pair de lettres a.
```

---

## Exemples acceptés

```text
ε
b
aa
baab
```

---

## Exemples refusés

```text
a
ab
baa
bab
```

---

# 12. Exemple type 4

## Nombre impair de `b`

Automate :

| État  | a   | b   |
| ----- | --- | --- |
| `→ 0` | `0` | `1` |
| `* 1` | `1` | `0` |

<svg width="720" height="270" viewBox="0 0 720 270" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_ex4" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>
  <line x1="80" y1="135" x2="145" y2="135" stroke="black" stroke-width="2" marker-end="url(#arrow_ex4)"/>
  <circle cx="190" cy="135" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="190" y="142" text-anchor="middle" font-size="22">0</text>
  <circle cx="490" cy="135" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="490" cy="135" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="490" y="142" text-anchor="middle" font-size="22">1</text>
  <path d="M225 120 C310 45, 370 45, 455 120" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex4)"/>
  <text x="340" y="55" text-anchor="middle" font-size="20">b</text>
  <path d="M455 150 C370 225, 310 225, 225 150" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex4)"/>
  <text x="340" y="220" text-anchor="middle" font-size="20">b</text>
  <path d="M165 100 C105 40, 275 40, 215 100" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex4)"/>
  <text x="190" y="55" text-anchor="middle" font-size="20">a</text>
  <path d="M465 100 C405 40, 575 40, 515 100" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_ex4)"/>
  <text x="490" y="55" text-anchor="middle" font-size="20">a</text>
</svg>

---

## Analyse

Avec la lettre `a`, on ne change pas d’état.

Avec la lettre `b`, on change d’état.

L’état `1` est final.

Donc :

```text
0 = nombre pair de b
1 = nombre impair de b
```

---

## Réponse examen

```text
L’automate reconnaît les mots qui contiennent un nombre impair de lettres b.
```

---

## Exemples acceptés

```text
b
ab
baaa
abbba
```

---

## Exemples refusés

```text
ε
a
bb
abba
```

---

# 13. Phrases prêtes pour l’examen

## Pour décrire un langage

```text
L’automate reconnaît les mots qui contiennent au moins une lettre a.
```

```text
L’automate reconnaît les mots qui commencent par a et se terminent par b.
```

```text
L’automate reconnaît les mots qui se terminent par ab.
```

```text
L’automate reconnaît les mots qui contiennent exactement deux lettres a.
```

```text
L’automate reconnaît les mots qui contiennent un nombre pair de lettres a.
```

```text
L’automate reconnaît les mots qui contiennent un nombre impair de lettres b.
```

```text
L’automate reconnaît les mots composés de zéro ou plusieurs a suivis d’un ou plusieurs b.
```

---

## Pour justifier avec les états

```text
L’état 0 signifie que le nombre de a lus est pair.
L’état 1 signifie que le nombre de a lus est impair.
Comme l’état final est 0, l’automate accepte les mots contenant un nombre pair de a.
```

```text
L’état 0 signifie qu’on n’a pas encore lu de a.
L’état 1 signifie qu’on a déjà lu au moins un a.
Comme l’état final est 1, l’automate accepte les mots contenant au moins un a.
```

```text
L’état 2 est un état mort : une fois arrivé dans cet état, on ne peut plus accepter le mot.
```

---

# 14. Résumé très court

Pour résoudre une question sur un automate :

1. Je regarde l’état initial.
2. Je regarde les états finaux.
3. Je lis le mot lettre par lettre.
4. Je suis les transitions.
5. Je regarde l’état final obtenu.
6. Si l’état obtenu est final, le mot est accepté.
7. Sinon, le mot est refusé.
8. Pour décrire le langage, je cherche la règle générale.

---

# 15. Mini méthode d’examen

Quand on te demande :

```text
Cet automate est-il déterministe ?
```

Réponds avec :

```text
Oui, car il a un seul état initial et au plus une transition pour chaque état et chaque lettre.
```

ou :

```text
Non, car depuis l’état ..., avec la lettre ..., il y a plusieurs transitions possibles.
```

---

Quand on te demande :

```text
Cet automate est-il complet ?
```

Réponds avec :

```text
Oui, car pour chaque état et chaque lettre, il y a au moins une transition.
```

ou :

```text
Non, car depuis l’état ..., avec la lettre ..., il n’y a aucune transition.
```

---

Quand on te demande :

```text
Le mot w est-il accepté ?
```

Réponds avec :

```text
On part de l’état initial.
On lit le mot de gauche à droite.
On suit les transitions.
On termine dans l’état ...
Comme cet état est final, le mot est accepté.
```

ou :

```text
Comme cet état n’est pas final, le mot est refusé.
```

---

Quand on te demande :

```text
Décrire le langage reconnu.
```

Réponds avec :

```text
L’automate reconnaît les mots qui ...
```

Puis donne une règle simple.

---

# 16. Idée principale à retenir

Un automate est comme une petite machine.

Il lit un mot lettre par lettre.

À la fin :

* s’il est dans un état final, le mot est accepté ;
* sinon, le mot est refusé.

Le plus important en examen est de comprendre :

```text
le rôle de chaque état
```

car cela permet de décrire le langage reconnu.

---

# Fiche d’entraînement — Automates finis

## Questions récentes et réponses modèles

Cette fiche contient les exercices déjà travaillés.
Elle sert à réviser les réponses attendues en examen.

---

# Partie 1 — Langages

## Question 1 — Langage défini par une longueur

Soit :

```text
A = {a}
L = { mots de longueur n | n = 2 + 3k, avec k ∈ N }
```

Les longueurs possibles sont :

```text
2, 5, 8, 11, ...
```

Donc un mot appartient à `L` si sa longueur est de la forme :

```text
2 + 3k
```

### Quatre mots de `L`

```text
aa
aaaaa
aaaaaaaa
aaaaaaaaaaa
```

### Quatre mots sur `A` qui n’appartiennent pas à `L`

```text
a
aaa
aaaa
aaaaaa
```

### Justification

```text
Les mots de L ont une longueur égale à 2, 5, 8, 11, ...
Donc un mot appartient à L si sa longueur est de la forme 2 + 3k.
```

---

## Question 2 — Exactement deux lettres `a`

Soit :

```text
A = {a, b}
L = { w ∈ A* | w contient exactement deux lettres a }
```

### Quatre mots de `L`

```text
aabb
abab
bbaa
baab
```

### Quatre mots sur `A` qui n’appartiennent pas à `L`

```text
b
ab
aaa
bbabb
```

### Justification

```text
Les mots de L sont exactement les mots sur A qui contiennent deux lettres a.
Les mots hors de L contiennent zéro, une, trois lettres a ou plus.
```

---

## Question 3 — Commencer par `a` et finir par `b`

Soit :

```text
A = {a, b}
L = { w ∈ A* | w commence par a et se termine par b }
```

### Quatre mots de `L`

```text
ab
aaab
abbbaab
abbbbbabbbabab
```

### Quatre mots sur `A` qui n’appartiennent pas à `L`

```text
ba
abba
baaab
abbbbaba
```

### Justification

```text
Un mot appartient à L s’il commence par a et se termine par b.
Si une des deux conditions manque, le mot n’appartient pas à L.
```

---

## Question 4 — Contenir au moins un `b`

Soit :

```text
A = {a, b}
L = { w ∈ A* | w contient au moins une lettre b }
```

### Quatre mots de `L`

```text
ab
abb
aaaaaab
baaaaab
```

### Quatre mots sur `A` qui n’appartiennent pas à `L`

```text
aaaa
a
aaa
aaaaaaaaa
```

### Justification

```text
Les mots de L contiennent au moins un b.
Les mots hors de L ne contiennent aucun b.
```

---

## Question 5 — Longueur paire et fin par `ab`

Soit :

```text
A = {a, b}
L = { w ∈ A* | w est de longueur paire et se termine par ab }
```

Un mot appartient à `L` s’il vérifie deux conditions :

```text
1) le mot est de longueur paire ;
2) le mot se termine par ab.
```

### Quatre mots de `L`

```text
ab
abab
aaab
bbab
```

### Quatre mots sur `A` qui n’appartiennent pas à `L`

```text
ba
baba
bbba
aaba
```

### Justification

```text
Un mot appartient à L s’il vérifie les deux conditions :
il est de longueur paire et il se termine par ab.
```

---

# Partie 2 — Automates

## Question 6 — Automate non déterministe et non complet

Automate :

```text
État        a        b
→ 0        {0}     {0,1}
* 1        {1}      ∅
```

<svg width="720" height="260" viewBox="0 0 720 260" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_q6" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>
  <line x1="80" y1="130" x2="145" y2="130" stroke="black" stroke-width="2" marker-end="url(#arrow_q6)"/>
  <circle cx="190" cy="130" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="190" y="137" text-anchor="middle" font-size="22">0</text>
  <circle cx="490" cy="130" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="490" cy="130" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="490" y="137" text-anchor="middle" font-size="22">1</text>
  <path d="M165 95 C105 35, 275 35, 215 95" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q6)"/>
  <text x="190" y="50" text-anchor="middle" font-size="20">a</text>
  <path d="M165 165 C105 225, 275 225, 215 165" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q6)"/>
  <text x="190" y="220" text-anchor="middle" font-size="20">b</text>
  <path d="M225 130 C310 85, 370 85, 455 130" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q6)"/>
  <text x="340" y="88" text-anchor="middle" font-size="20">b</text>
  <path d="M465 95 C405 35, 575 35, 515 95" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q6)"/>
  <text x="490" y="50" text-anchor="middle" font-size="20">a</text>
  <text x="490" y="210" text-anchor="middle" font-size="16">pas de transition avec b</text>
</svg>

### Déterminisme

```text
L’automate n’est pas déterministe car, depuis l’état 0 avec la lettre b, il y a deux transitions possibles : vers 0 et vers 1.
```

### Complétude

```text
L’automate n’est pas complet car, depuis l’état 1 avec la lettre b, il n’y a aucune transition.
```

---

## Question 7 — Mots reconnus

Automate :

```text
État        a        b
→ 0         1        0
  1         1        2
* 2         1        0
```

<svg width="850" height="320" viewBox="0 0 850 320" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_q7" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>
  <line x1="50" y1="155" x2="115" y2="155" stroke="black" stroke-width="2" marker-end="url(#arrow_q7)"/>
  <circle cx="160" cy="155" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="160" y="162" text-anchor="middle" font-size="22">0</text>
  <circle cx="410" cy="155" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="410" y="162" text-anchor="middle" font-size="22">1</text>
  <circle cx="660" cy="155" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="660" cy="155" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="660" y="162" text-anchor="middle" font-size="22">2</text>
  <path d="M135 120 C75 60, 245 60, 185 120" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q7)"/>
  <text x="160" y="75" text-anchor="middle" font-size="20">b</text>
  <path d="M198 155 L372 155" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q7)"/>
  <text x="285" y="135" text-anchor="middle" font-size="20">a</text>
  <path d="M385 120 C325 60, 495 60, 435 120" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q7)"/>
  <text x="410" y="75" text-anchor="middle" font-size="20">a</text>
  <path d="M448 155 L622 155" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q7)"/>
  <text x="535" y="135" text-anchor="middle" font-size="20">b</text>
  <path d="M625 180 C555 245, 515 245, 445 180" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q7)"/>
  <text x="535" y="245" text-anchor="middle" font-size="20">a</text>
  <path d="M630 195 C480 310, 300 310, 190 190" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q7)"/>
  <text x="400" y="305" text-anchor="middle" font-size="20">b</text>
</svg>

### Déterminisme et complétude

```text
L’automate est déterministe et complet.
```

Il est déterministe car il y a une seule transition pour chaque état et chaque lettre.

Il est complet car il y a une transition pour chaque état et chaque lettre.

### Parcours des mots

```text
ε : on reste en 0.
L’état 0 n’est pas final, donc ε est refusé.
```

```text
a : 0 --a--> 1.
L’état 1 n’est pas final, donc a est refusé.
```

```text
ab : 0 --a--> 1 --b--> 2.
L’état 2 est final, donc ab est accepté.
```

```text
abb : 0 --a--> 1 --b--> 2 --b--> 0.
L’état 0 n’est pas final, donc abb est refusé.
```

```text
aab : 0 --a--> 1 --a--> 1 --b--> 2.
L’état 2 est final, donc aab est accepté.
```

```text
baab : 0 --b--> 0 --a--> 1 --a--> 1 --b--> 2.
L’état 2 est final, donc baab est accepté.
```

---

## Question 8 — État initial final

Automate :

```text
État        a        b
→* 0        1        0
   1        1        2
 * 2        1        0
```

<svg width="850" height="320" viewBox="0 0 850 320" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_q8" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>
  <line x1="50" y1="155" x2="115" y2="155" stroke="black" stroke-width="2" marker-end="url(#arrow_q8)"/>
  <circle cx="160" cy="155" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="160" cy="155" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="160" y="162" text-anchor="middle" font-size="22">0</text>
  <circle cx="410" cy="155" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="410" y="162" text-anchor="middle" font-size="22">1</text>
  <circle cx="660" cy="155" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="660" cy="155" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="660" y="162" text-anchor="middle" font-size="22">2</text>
  <path d="M135 120 C75 60, 245 60, 185 120" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q8)"/>
  <text x="160" y="75" text-anchor="middle" font-size="20">b</text>
  <path d="M198 155 L372 155" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q8)"/>
  <text x="285" y="135" text-anchor="middle" font-size="20">a</text>
  <path d="M385 120 C325 60, 495 60, 435 120" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q8)"/>
  <text x="410" y="75" text-anchor="middle" font-size="20">a</text>
  <path d="M448 155 L622 155" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q8)"/>
  <text x="535" y="135" text-anchor="middle" font-size="20">b</text>
  <path d="M625 180 C555 245, 515 245, 445 180" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q8)"/>
  <text x="535" y="245" text-anchor="middle" font-size="20">a</text>
  <path d="M630 195 C480 310, 300 310, 190 190" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_q8)"/>
  <text x="400" y="305" text-anchor="middle" font-size="20">b</text>
</svg>

### Déterminisme et complétude

```text
L’automate est déterministe et complet.
```

### Parcours des mots

```text
ε : on reste en 0.
L’état 0 est final, donc ε est accepté.
```

```text
b : 0 --b--> 0.
L’état 0 est final, donc b est accepté.
```

```text
ab : 0 --a--> 1 --b--> 2.
L’état 2 est final, donc ab est accepté.
```

```text
aabb : 0 --a--> 1 --a--> 1 --b--> 2 --b--> 0.
L’état 0 est final, donc aabb est accepté.
```

```text
bab : 0 --b--> 0 --a--> 1 --b--> 2.
L’état 2 est final, donc bab est accepté.
```

```text
bbabb : 0 --b--> 0 --b--> 0 --a--> 1 --b--> 2 --b--> 0.
L’état 0 est final, donc bbabb est accepté.
```

---

## Question 9 — Langage reconnu : au moins un `a`

Même automate que l’exemple type 1.

Automate :

```text
État        a        b
→ 0         1        0
* 1         1        1
```

### Déterminisme et complétude

```text
L’automate est déterministe et complet.
```

### Langage reconnu

```text
L = b* a A*
```

### Phrase en langage ordinaire

```text
L’automate reconnaît les mots qui contiennent au moins une lettre a.
```

### Exemples acceptés

```text
a
ba
aaabbababba
abababa
```

### Exemples refusés

```text
ε
b
bb
bbbb
```

---

## Question 10 — Langage reconnu : `a*b+`

Même automate que l’exemple type 2.

Automate :

```text
État        a        b
→ 0         0        1
* 1         2        1
  2         2        2
```

### Déterminisme et complétude

```text
L’automate est déterministe et complet.
```

### Langage reconnu

```text
L = a* b+
```

### Phrase en langage ordinaire

```text
L’automate reconnaît les mots composés de zéro ou plusieurs a suivis d’un ou plusieurs b.
```

### Autre phrase correcte

```text
L’automate reconnaît les mots qui contiennent au moins un b et qui n’ont plus de a après le premier b.
```

### Exemples acceptés

```text
b
bb
ab
aaabb
```

### Exemples refusés

```text
ε
a
ba
aba
```

---

## Question 11 — Complémentaire

Soit :

```text
A = {a, b}
L = { w ∈ A* | w contient au moins un a }
```

Le complémentaire de `L` dans `A*` est :

```text
A* \ L = { w ∈ A* | w ne contient aucun a }
```

Donc :

```text
A* \ L = b*
```

### Exemples dans `L`

```text
a
ababbb
aaaa
ba
```

### Exemples dans le complémentaire

```text
ε
b
bb
bbb
```

---

## Question 12 — Décrire des expressions

### Expression 1

```text
L1 = A* ab
```

Réponse :

```text
L1 est l’ensemble des mots qui se terminent par ab.
```

Exemples :

```text
ab
aaaab
```

---

### Expression 2

```text
L2 = a A* b
```

Réponse :

```text
L2 est l’ensemble des mots qui commencent par a et se terminent par b.
```

Exemples :

```text
ab
aaaaab
```

---

### Expression 3

```text
L3 = b* a b*
```

Réponse :

```text
L3 est l’ensemble des mots qui contiennent exactement un seul a.
```

Exemples :

```text
bbbbbbabbbbbb
bbabb
```

---

### Expression 4

```text
L4 = b* a b* a b*
```

Réponse :

```text
L4 est l’ensemble des mots qui contiennent exactement deux lettres a.
```

Exemples :

```text
aa
babab
```

---

## Question 13 — Nombre pair de `a`

Même automate que l’exemple type 3.

Automate :

```text
État        a        b
→* 0        1        0
   1        0        1
```

### Déterminisme et complétude

```text
L’automate est déterministe et complet.
```

### Langage reconnu

```text
L = { w ∈ A* | |w|a est pair }
```

### Phrase en langage ordinaire

```text
L’automate reconnaît les mots qui contiennent un nombre pair de lettres a.
```

### Justification

```text
L’état 0 signifie que le nombre de a lus est pair.
L’état 1 signifie que le nombre de a lus est impair.
Avec b, on ne change pas d’état.
Avec a, on change d’état.
Comme l’état 0 est final, les mots acceptés sont ceux qui contiennent un nombre pair de a.
```

### Exemples acceptés

```text
ε
b
aa
baab
```

### Exemples refusés

```text
a
ab
baa
bab
```

---

## Question 14 — Nombre impair de `b`

Même automate que l’exemple type 4.

Automate :

```text
État        a        b
→ 0         0        1
* 1         1        0
```

### Déterminisme et complétude

```text
L’automate est déterministe et complet.
```

### Langage reconnu

```text
L = { w ∈ A* | |w|b est impair }
```

### Phrase en langage ordinaire

```text
L’automate reconnaît les mots qui contiennent un nombre impair de lettres b.
```

### Justification

```text
L’état 0 signifie que le nombre de b lus est pair.
L’état 1 signifie que le nombre de b lus est impair.
Avec a, on ne change pas d’état.
Avec b, on change d’état.
Comme l’état 1 est final, les mots acceptés sont ceux qui contiennent un nombre impair de b.
```

### Exemples acceptés

```text
b
ab
baaa
abbba
```

### Exemples refusés

```text
ε
a
bb
abba
```

---

# Partie 3 — TD5 officiel

# TD5 — Exercice 3

## Énoncé

On considère l’automate suivant sur l’alphabet :

```text
A = {a, b}
```

Transitions :

```text
1 --a--> 2
2 --b--> 3
3 --a--> 3
3 --b--> 3
```

<svg width="820" height="230" viewBox="0 0 820 230" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_td5ex3" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>
  <line x1="60" y1="115" x2="125" y2="115" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex3)"/>
  <circle cx="170" cy="115" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="170" y="122" text-anchor="middle" font-size="22">1</text>
  <circle cx="410" cy="115" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="410" y="122" text-anchor="middle" font-size="22">2</text>
  <circle cx="650" cy="115" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="650" cy="115" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="650" y="122" text-anchor="middle" font-size="22">3</text>
  <path d="M208 115 L372 115" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex3)"/>
  <text x="290" y="95" text-anchor="middle" font-size="20">a</text>
  <path d="M448 115 L612 115" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex3)"/>
  <text x="530" y="95" text-anchor="middle" font-size="20">b</text>
  <path d="M625 80 C565 20, 735 20, 675 80" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex3)"/>
  <text x="650" y="35" text-anchor="middle" font-size="20">a,b</text>
</svg>

État initial :

```text
1
```

État final :

```text
3
```

Questions :

```text
1) Expliquer pourquoi l’automate n’est pas complet.
2) Quel langage reconnaît-il ?
3) Donner un automate complet équivalent.
```

---

## Réponse complète

### 1) Pourquoi l’automate n’est pas complet ?

```text
L’automate n’est pas complet car, depuis l’état 1, il n’y a aucune transition avec la lettre b.
Il n’est pas complet aussi car, depuis l’état 2, il n’y a aucune transition avec la lettre a.
```

Phrase générale :

```text
Un automate est complet si, pour chaque état et chaque lettre de l’alphabet, il existe au moins une transition.
Ici, certaines transitions manquent, donc l’automate n’est pas complet.
```

---

### 2) Quel langage reconnaît-il ?

Pour être accepté, un mot doit suivre ce début de parcours :

```text
1 --a--> 2 --b--> 3
```

Une fois arrivé dans l’état final `3`, on peut lire n’importe quelle suite de `a` et de `b`.

Donc :

```text
L = ab A*
```

Phrase en langage ordinaire :

```text
L’automate reconnaît les mots qui commencent par ab.
```

Exemples acceptés :

```text
ab
aba
abb
abba
ababab
```

Exemples refusés :

```text
ε
a
b
aa
ba
aab
```

---

### 3) Automate complet équivalent

On ajoute un état puits `P`.

Transitions complètes :

```text
1 --a--> 2
1 --b--> P

2 --a--> P
2 --b--> 3

3 --a--> 3
3 --b--> 3

P --a--> P
P --b--> P
```

<svg width="850" height="390" viewBox="0 0 850 390" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_td5ex3_complete" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>
  <line x1="60" y1="120" x2="125" y2="120" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex3_complete)"/>
  <circle cx="170" cy="120" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="170" y="127" text-anchor="middle" font-size="22">1</text>
  <circle cx="410" cy="120" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="410" y="127" text-anchor="middle" font-size="22">2</text>
  <circle cx="650" cy="120" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="650" cy="120" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="650" y="127" text-anchor="middle" font-size="22">3</text>
  <circle cx="410" cy="295" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="410" y="302" text-anchor="middle" font-size="22">P</text>
  <path d="M208 120 L372 120" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex3_complete)"/>
  <text x="290" y="100" text-anchor="middle" font-size="20">a</text>
  <path d="M448 120 L612 120" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex3_complete)"/>
  <text x="530" y="100" text-anchor="middle" font-size="20">b</text>
  <path d="M190 150 C250 225, 310 265, 372 290" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex3_complete)"/>
  <text x="270" y="225" text-anchor="middle" font-size="20">b</text>
  <path d="M410 158 L410 257" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex3_complete)"/>
  <text x="430" y="215" font-size="20">a</text>
  <path d="M625 85 C565 25, 735 25, 675 85" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex3_complete)"/>
  <text x="650" y="40" text-anchor="middle" font-size="20">a,b</text>
  <path d="M385 330 C325 375, 495 375, 435 330" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex3_complete)"/>
  <text x="410" y="370" text-anchor="middle" font-size="20">a,b</text>
</svg>

État initial :

```text
1
```

État final :

```text
3
```

Justification :

```text
L’état P est un état puits.
Une fois arrivé dans P, on y reste pour toutes les lettres.
Cet automate est complet et reconnaît le même langage que l’automate initial.
```

---

# TD5 — Exercice 4

## Énoncé

On considère l’automate `A` sur l’alphabet :

```text
A = {a, b, c}
```

États :

```text
0, 1, 2, 3
```

État initial :

```text
0
```

État terminal :

```text
3
```

Transitions :

```text
(0, a, 0)
(0, a, 1)
(0, b, 0)
(0, c, 0)

(1, a, 2)
(1, b, 2)
(1, c, 2)

(2, a, 3)
(2, b, 3)
(2, c, 3)
```

<svg width="920" height="260" viewBox="0 0 920 260" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_td5ex4" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>
  <line x1="50" y1="130" x2="115" y2="130" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex4)"/>
  <circle cx="160" cy="130" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="160" y="137" text-anchor="middle" font-size="22">0</text>
  <circle cx="390" cy="130" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="390" y="137" text-anchor="middle" font-size="22">1</text>
  <circle cx="620" cy="130" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="620" y="137" text-anchor="middle" font-size="22">2</text>
  <circle cx="820" cy="130" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="820" cy="130" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="820" y="137" text-anchor="middle" font-size="22">3</text>
  <path d="M135 95 C75 35, 245 35, 185 95" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex4)"/>
  <text x="160" y="48" text-anchor="middle" font-size="20">a,b,c</text>
  <path d="M198 130 L352 130" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex4)"/>
  <text x="275" y="110" text-anchor="middle" font-size="20">a</text>
  <path d="M428 130 L582 130" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex4)"/>
  <text x="505" y="110" text-anchor="middle" font-size="20">a,b,c</text>
  <path d="M658 130 L782 130" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5ex4)"/>
  <text x="720" y="110" text-anchor="middle" font-size="20">a,b,c</text>
</svg>

Questions :

```text
1) Cet automate est-il complet ? déterministe ? Justifier.
2) Les mots baba et cabcb sont-ils reconnus par A ?
3) Décrire L(A) en langage ordinaire.
```

---

## Réponse complète

### 1) L’automate est-il complet ?

```text
L’automate n’est pas complet car, depuis l’état 3, il n’y a aucune transition avec a, b ou c.
```

Phrase générale :

```text
Un automate est complet si, pour chaque état et chaque lettre de l’alphabet, il y a au moins une transition.
Ici, depuis l’état 3, aucune transition n’est définie.
Donc l’automate n’est pas complet.
```

---

### 2) L’automate est-il déterministe ?

```text
L’automate n’est pas déterministe car, depuis l’état 0 avec la lettre a, il y a deux transitions possibles : vers 0 et vers 1.
```

Phrase générale :

```text
Un automate est déterministe s’il a un seul état initial et si, pour chaque état et chaque lettre, il y a au plus une transition.
Ici, depuis l’état 0 avec la lettre a, il y a deux choix possibles.
Donc l’automate n’est pas déterministe.
```

---

### 3) Le mot `baba` est-il reconnu ?

Parcours acceptant :

```text
baba : 0 --b--> 0 --a--> 1 --b--> 2 --a--> 3.
```

Réponse :

```text
L’état 3 est final, donc baba est reconnu par A.
```

Important :

```text
Comme l’automate est non déterministe, il suffit qu’il existe un parcours acceptant pour que le mot soit accepté.
```

---

### 4) Le mot `cabcb` est-il reconnu ?

On essaie le parcours qui utilise la transition vers `1` au moment du `a` :

```text
cabcb : 0 --c--> 0 --a--> 1 --b--> 2 --c--> 3.
```

Mais il reste encore la lettre `b` à lire.

Depuis l’état `3`, il n’y a aucune transition.

Donc :

```text
cabcb est refusé.
```

Réponse complète :

```text
Le mot cabcb n’est pas reconnu par A, car le seul parcours qui peut arriver à l’état final 3 y arrive avant la fin du mot, et il reste une lettre à lire.
```

---

### 5) Description de `L(A)`

Pour arriver à l’état final `3`, il faut faire :

```text
0 --a--> 1 --A--> 2 --A--> 3
```

Avant ce `a`, on peut lire n’importe quel mot et rester dans l’état `0`.

Donc :

```text
L(A) = A* a A A
```

Phrase en langage ordinaire :

```text
L’automate reconnaît les mots dont la troisième lettre en partant de la fin est a.
```

Autre phrase correcte :

```text
L’automate reconnaît les mots qui contiennent un a suivi exactement de deux lettres à la fin du mot.
```

Exemples acceptés :

```text
aba
baba
caab
cbacc
```

Exemples refusés :

```text
ε
a
ab
cabcb
```

---

## Réponse modèle complète pour TD5 Exercice 4

```text
L’automate n’est pas complet car, depuis l’état 3, il n’y a aucune transition avec a, b ou c.

L’automate n’est pas déterministe car, depuis l’état 0 avec la lettre a, il y a deux transitions possibles : vers 0 et vers 1.

baba : 0 --b--> 0 --a--> 1 --b--> 2 --a--> 3.
L’état 3 est final, donc baba est reconnu par A.

cabcb : 0 --c--> 0 --a--> 1 --b--> 2 --c--> 3.
Mais il reste encore la lettre b à lire, et depuis l’état 3 il n’y a aucune transition.
Donc cabcb n’est pas reconnu par A.

L(A) = A* a A A.
L’automate reconnaît les mots dont la troisième lettre en partant de la fin est a.
```

---

# Ce qu’il faut retenir

```text
1) Pour vérifier si un automate est complet, on cherche les transitions manquantes.
2) Pour vérifier si un automate est déterministe, on cherche les doubles transitions avec la même lettre depuis le même état.
3) Pour savoir si un mot est reconnu, il faut lire tout le mot et finir dans un état final.
4) Dans un automate non déterministe, un mot est accepté s’il existe au moins un parcours acceptant.
5) Pour décrire L(A), il faut écrire une règle générale en langage ordinaire.
```




## Dessin — Longueur paire

À mettre après la table de la section **3) Automate pour les mots de longueur paire**.

<svg width="720" height="270" viewBox="0 0 720 270" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_len_pair" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>

  <line x1="80" y1="135" x2="145" y2="135" stroke="black" stroke-width="2" marker-end="url(#arrow_len_pair)"/>

  <circle cx="190" cy="135" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="190" cy="135" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="190" y="142" text-anchor="middle" font-size="22">0</text>

  <circle cx="500" cy="135" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="500" y="142" text-anchor="middle" font-size="22">1</text>

  <path d="M225 120 C315 45, 375 45, 465 120" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_len_pair)"/>
  <text x="345" y="55" text-anchor="middle" font-size="20">a,b</text>

  <path d="M465 150 C375 225, 315 225, 225 150" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_len_pair)"/>
  <text x="345" y="220" text-anchor="middle" font-size="20">a,b</text>
</svg>

---

## Dessin — Nombre de `b` multiple de 3

À mettre après la table de la section **4) Automate pour les mots dont le nombre de b est multiple de 3**.

<svg width="860" height="330" viewBox="0 0 860 330" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_b_mod3" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>

  <line x1="50" y1="160" x2="115" y2="160" stroke="black" stroke-width="2" marker-end="url(#arrow_b_mod3)"/>

  <circle cx="160" cy="160" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="160" cy="160" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="160" y="167" text-anchor="middle" font-size="22">0</text>

  <circle cx="430" cy="160" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="430" y="167" text-anchor="middle" font-size="22">1</text>

  <circle cx="700" cy="160" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="700" y="167" text-anchor="middle" font-size="22">2</text>

  <path d="M135 125 C75 65, 245 65, 185 125" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_b_mod3)"/>
  <text x="160" y="78" text-anchor="middle" font-size="20">a</text>

  <path d="M405 125 C345 65, 515 65, 455 125" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_b_mod3)"/>
  <text x="430" y="78" text-anchor="middle" font-size="20">a</text>

  <path d="M675 125 C615 65, 785 65, 725 125" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_b_mod3)"/>
  <text x="700" y="78" text-anchor="middle" font-size="20">a</text>

  <path d="M198 160 L392 160" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_b_mod3)"/>
  <text x="295" y="138" text-anchor="middle" font-size="20">b</text>

  <path d="M468 160 L662 160" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_b_mod3)"/>
  <text x="565" y="138" text-anchor="middle" font-size="20">b</text>

  <path d="M675 195 C535 295, 325 295, 185 195" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_b_mod3)"/>
  <text x="430" y="300" text-anchor="middle" font-size="20">b</text>
</svg>

---

## Dessin — Mots qui se terminent par `b`

À mettre après la table de la section **5) Automate pour les mots qui se terminent par b**.

<svg width="720" height="270" viewBox="0 0 720 270" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_end_b" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>

  <line x1="80" y1="135" x2="145" y2="135" stroke="black" stroke-width="2" marker-end="url(#arrow_end_b)"/>

  <circle cx="190" cy="135" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="190" y="142" text-anchor="middle" font-size="22">0</text>

  <circle cx="500" cy="135" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="500" cy="135" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="500" y="142" text-anchor="middle" font-size="22">1</text>

  <path d="M165 100 C105 40, 275 40, 215 100" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_end_b)"/>
  <text x="190" y="55" text-anchor="middle" font-size="20">a</text>

  <path d="M475 100 C415 40, 585 40, 525 100" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_end_b)"/>
  <text x="500" y="55" text-anchor="middle" font-size="20">b</text>

  <path d="M228 135 L462 135" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_end_b)"/>
  <text x="345" y="113" text-anchor="middle" font-size="20">b</text>

  <path d="M462 165 C375 230, 315 230, 228 165" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_end_b)"/>
  <text x="345" y="230" text-anchor="middle" font-size="20">a</text>
</svg>

---

## Dessin — Mots non vides qui ne se terminent pas par `b`

À mettre après la table de la section **6) Automate pour les mots non vides qui ne se terminent pas par b**.

<svg width="860" height="340" viewBox="0 0 860 340" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_non_empty_not_b" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>

  <line x1="50" y1="170" x2="115" y2="170" stroke="black" stroke-width="2" marker-end="url(#arrow_non_empty_not_b)"/>

  <circle cx="160" cy="170" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="160" y="177" text-anchor="middle" font-size="22">0</text>

  <circle cx="430" cy="95" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="430" cy="95" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="430" y="102" text-anchor="middle" font-size="22">1</text>

  <circle cx="430" cy="245" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="430" y="252" text-anchor="middle" font-size="22">2</text>

  <path d="M195 155 C265 110, 335 95, 392 95" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_non_empty_not_b)"/>
  <text x="285" y="105" text-anchor="middle" font-size="20">a</text>

  <path d="M195 185 C265 230, 335 245, 392 245" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_non_empty_not_b)"/>
  <text x="285" y="240" text-anchor="middle" font-size="20">b</text>

  <path d="M405 60 C345 0, 515 0, 455 60" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_non_empty_not_b)"/>
  <text x="430" y="18" text-anchor="middle" font-size="20">a</text>

  <path d="M405 280 C345 335, 515 335, 455 280" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_non_empty_not_b)"/>
  <text x="430" y="323" text-anchor="middle" font-size="20">b</text>

  <path d="M455 125 C555 165, 555 175, 455 215" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_non_empty_not_b)"/>
  <text x="555" y="172" text-anchor="middle" font-size="20">b</text>

  <path d="M405 215 C305 175, 305 165, 405 125" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_non_empty_not_b)"/>
  <text x="305" y="172" text-anchor="middle" font-size="20">a</text>
</svg>





## Dessin — Mots contenant au moins un `b`

À mettre après la table de la section **7) Automate pour les mots contenant au moins un b**.

<svg width="720" height="230" viewBox="0 0 720 230" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_atleast_b" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>

  <line x1="80" y1="115" x2="145" y2="115" stroke="black" stroke-width="2" marker-end="url(#arrow_atleast_b)"/>

  <circle cx="190" cy="115" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="190" y="122" text-anchor="middle" font-size="22">0</text>

  <circle cx="500" cy="115" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="500" cy="115" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="500" y="122" text-anchor="middle" font-size="22">1</text>

  <path d="M165 80 C105 20, 275 20, 215 80" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_atleast_b)"/>
  <text x="190" y="35" text-anchor="middle" font-size="20">a</text>

  <path d="M228 115 L462 115" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_atleast_b)"/>
  <text x="345" y="93" text-anchor="middle" font-size="20">b</text>

  <path d="M475 80 C415 20, 585 20, 525 80" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_atleast_b)"/>
  <text x="500" y="35" text-anchor="middle" font-size="20">a,b</text>
</svg>

---

## Dessin — Mots contenant exactement un `b`

À mettre après la table de la section **8) Automate pour les mots contenant exactement un b**.

<svg width="860" height="270" viewBox="0 0 860 270" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_exactly_one_b" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>

  <line x1="50" y1="135" x2="115" y2="135" stroke="black" stroke-width="2" marker-end="url(#arrow_exactly_one_b)"/>

  <circle cx="160" cy="135" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="160" y="142" text-anchor="middle" font-size="22">0</text>

  <circle cx="430" cy="135" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="430" cy="135" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="430" y="142" text-anchor="middle" font-size="22">1</text>

  <circle cx="700" cy="135" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="700" y="142" text-anchor="middle" font-size="22">2</text>

  <path d="M135 100 C75 40, 245 40, 185 100" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_exactly_one_b)"/>
  <text x="160" y="55" text-anchor="middle" font-size="20">a</text>

  <path d="M405 100 C345 40, 515 40, 455 100" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_exactly_one_b)"/>
  <text x="430" y="55" text-anchor="middle" font-size="20">a</text>

  <path d="M675 100 C615 40, 785 40, 725 100" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_exactly_one_b)"/>
  <text x="700" y="55" text-anchor="middle" font-size="20">a,b</text>

  <path d="M198 135 L392 135" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_exactly_one_b)"/>
  <text x="295" y="113" text-anchor="middle" font-size="20">b</text>

  <path d="M468 135 L662 135" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_exactly_one_b)"/>
  <text x="565" y="113" text-anchor="middle" font-size="20">b</text>
</svg>

---

## Dessin — Mots contenant au plus un `b`

À mettre après la table de la section **9) Automate pour les mots contenant au plus un b**.

<svg width="860" height="270" viewBox="0 0 860 270" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_atmost_one_b" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>

  <line x1="50" y1="135" x2="115" y2="135" stroke="black" stroke-width="2" marker-end="url(#arrow_atmost_one_b)"/>

  <circle cx="160" cy="135" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="160" cy="135" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="160" y="142" text-anchor="middle" font-size="22">0</text>

  <circle cx="430" cy="135" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="430" cy="135" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="430" y="142" text-anchor="middle" font-size="22">1</text>

  <circle cx="700" cy="135" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="700" y="142" text-anchor="middle" font-size="22">2</text>

  <path d="M135 100 C75 40, 245 40, 185 100" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_atmost_one_b)"/>
  <text x="160" y="55" text-anchor="middle" font-size="20">a</text>

  <path d="M405 100 C345 40, 515 40, 455 100" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_atmost_one_b)"/>
  <text x="430" y="55" text-anchor="middle" font-size="20">a</text>

  <path d="M675 100 C615 40, 785 40, 725 100" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_atmost_one_b)"/>
  <text x="700" y="55" text-anchor="middle" font-size="20">a,b</text>

  <path d="M198 135 L392 135" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_atmost_one_b)"/>
  <text x="295" y="113" text-anchor="middle" font-size="20">b</text>

  <path d="M468 135 L662 135" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_atmost_one_b)"/>
  <text x="565" y="113" text-anchor="middle" font-size="20">b</text>
</svg>

---

## Dessin — Mots ne contenant aucun `b`

À mettre après la table de la section **10) Automate pour les mots ne contenant aucun b**.

<svg width="720" height="230" viewBox="0 0 720 230" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_no_b" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>

  <line x1="80" y1="115" x2="145" y2="115" stroke="black" stroke-width="2" marker-end="url(#arrow_no_b)"/>

  <circle cx="190" cy="115" r="38" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="190" cy="115" r="30" fill="none" stroke="black" stroke-width="2"/>
  <text x="190" y="122" text-anchor="middle" font-size="22">0</text>

  <circle cx="500" cy="115" r="38" fill="white" stroke="black" stroke-width="2"/>
  <text x="500" y="122" text-anchor="middle" font-size="22">1</text>

  <path d="M165 80 C105 20, 275 20, 215 80" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_no_b)"/>
  <text x="190" y="35" text-anchor="middle" font-size="20">a</text>

  <path d="M228 115 L462 115" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_no_b)"/>
  <text x="345" y="93" text-anchor="middle" font-size="20">b</text>

  <path d="M475 80 C415 20, 585 20, 525 80" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_no_b)"/>
  <text x="500" y="35" text-anchor="middle" font-size="20">a,b</text>
</svg>

---

## Dessin — Langage fini `L = {ab, ba}`

À mettre après la table de la section **11) Automate pour un langage fini**.

<svg width="980" height="420" viewBox="0 0 980 420" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_finite_ab_ba" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>

  <line x1="40" y1="200" x2="105" y2="200" stroke="black" stroke-width="2" marker-end="url(#arrow_finite_ab_ba)"/>

  <circle cx="150" cy="200" r="35" fill="white" stroke="black" stroke-width="2"/>
  <text x="150" y="207" text-anchor="middle" font-size="20">0</text>

  <circle cx="350" cy="115" r="35" fill="white" stroke="black" stroke-width="2"/>
  <text x="350" y="122" text-anchor="middle" font-size="20">1</text>

  <circle cx="350" cy="285" r="35" fill="white" stroke="black" stroke-width="2"/>
  <text x="350" y="292" text-anchor="middle" font-size="20">2</text>

  <circle cx="570" cy="115" r="35" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="570" cy="115" r="27" fill="none" stroke="black" stroke-width="2"/>
  <text x="570" y="122" text-anchor="middle" font-size="20">3</text>

  <circle cx="570" cy="285" r="35" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="570" cy="285" r="27" fill="none" stroke="black" stroke-width="2"/>
  <text x="570" y="292" text-anchor="middle" font-size="20">4</text>

  <circle cx="820" cy="200" r="35" fill="white" stroke="black" stroke-width="2"/>
  <text x="820" y="207" text-anchor="middle" font-size="20">P</text>

  <path d="M183 185 L317 130" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_finite_ab_ba)"/>
  <text x="250" y="135" text-anchor="middle" font-size="20">a</text>

  <path d="M183 215 L317 270" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_finite_ab_ba)"/>
  <text x="250" y="270" text-anchor="middle" font-size="20">b</text>

  <path d="M385 115 L535 115" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_finite_ab_ba)"/>
  <text x="460" y="95" text-anchor="middle" font-size="20">b</text>

  <path d="M385 285 L535 285" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_finite_ab_ba)"/>
  <text x="460" y="265" text-anchor="middle" font-size="20">a</text>

  <path d="M376 140 C480 220, 620 220, 785 200" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_finite_ab_ba)"/>
  <text x="575" y="215" text-anchor="middle" font-size="20">a</text>

  <path d="M376 260 C480 180, 620 180, 785 200" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_finite_ab_ba)"/>
  <text x="575" y="175" text-anchor="middle" font-size="20">b</text>

  <path d="M605 115 C700 120, 760 150, 795 175" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_finite_ab_ba)"/>
  <text x="710" y="120" text-anchor="middle" font-size="20">a,b</text>

  <path d="M605 285 C700 280, 760 250, 795 225" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_finite_ab_ba)"/>
  <text x="710" y="285" text-anchor="middle" font-size="20">a,b</text>

  <path d="M795 165 C735 105, 905 105, 845 165" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_finite_ab_ba)"/>
  <text x="820" y="120" text-anchor="middle" font-size="20">a,b</text>
</svg>






# TD5 — Exercice 5

## Construire un automate déterministe reconnaissant un langage fini

## Énoncé

Construire un automate déterministe qui reconnaît le langage fini :

```text
L = {a, ba, aba, bab, bbba}
```

On travaille sur l’alphabet :

```text
A = {a, b}
```

---

# 1. Idée importante

Le langage demandé est **fini**.

Cela veut dire qu’il contient seulement ces cinq mots :

```text
a
ba
aba
bab
bbba
```

Donc l’automate doit accepter **exactement** ces mots, et aucun autre.

Il ne doit pas accepter :

```text
b
aa
ab
baa
bbbb
abab
```

---

# 2. Pourquoi une boucle générale est fausse ?

Si on construit un automate comme ceci :

```text
0 --a--> 1
0 --b--> 1
1 --a--> 1
1 --b--> 1
```

et si l’état `1` est final, alors l’automate accepte presque tous les mots non vides.

Par exemple, il accepte :

```text
b
aa
ab
bb
aaa
```

Mais ces mots ne sont pas tous dans :

```text
{a, ba, aba, bab, bbba}
```

Donc ce type d’automate est faux.

---

# 3. Méthode correcte pour un langage fini

Pour un langage fini, il faut construire un **chemin exact** pour chaque mot accepté.

Ici, on doit avoir un chemin pour :

```text
a
ba
aba
bab
bbba
```

Chaque fin de mot accepté doit être un état final.

Toutes les mauvaises lettres doivent aller vers un **état puits** `P`.

Un état puits est un état dans lequel on reste pour toujours.

---

# 4. Construction des états

On construit l’automate comme un arbre de préfixes.

```text
0 = début

1 = on a lu a
2 = on a lu b

3 = on a lu ba
4 = on a lu ab

5 = on a lu aba
6 = on a lu bab

7 = on a lu bb
8 = on a lu bbb
9 = on a lu bbba

P = état puits
```

---

# 5. États finaux

Les mots acceptés sont :

```text
a
ba
aba
bab
bbba
```

Donc les états finaux sont :

```text
1, 3, 5, 6, 9
```

Car :

```text
1 correspond à a
3 correspond à ba
5 correspond à aba
6 correspond à bab
9 correspond à bbba
```

---

# 6. Table complète de l’automate

```text
État        a        b
→ 0         1        2
* 1         P        4
  2         3        7
* 3         P        6
  4         5        P
* 5         P        P
* 6         P        P
  7         P        8
  8         9        P
* 9         P        P
  P         P        P
```

---

# 7. Dessin de l’automate

<svg width="1100" height="560" viewBox="0 0 1100 560" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow_td5_ex5" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>

  <!-- initial arrow -->

  <line x1="40" y1="260" x2="105" y2="260" stroke="black" stroke-width="2" marker-end="url(#arrow_td5_ex5)"/>

  <!-- states -->

  <circle cx="150" cy="260" r="34" fill="white" stroke="black" stroke-width="2"/>
  <text x="150" y="267" text-anchor="middle" font-size="20">0</text>

  <circle cx="330" cy="145" r="34" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="330" cy="145" r="26" fill="none" stroke="black" stroke-width="2"/>
  <text x="330" y="152" text-anchor="middle" font-size="20">1</text>

  <circle cx="330" cy="375" r="34" fill="white" stroke="black" stroke-width="2"/>
  <text x="330" y="382" text-anchor="middle" font-size="20">2</text>

  <circle cx="530" cy="330" r="34" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="530" cy="330" r="26" fill="none" stroke="black" stroke-width="2"/>
  <text x="530" y="337" text-anchor="middle" font-size="20">3</text>

  <circle cx="530" cy="145" r="34" fill="white" stroke="black" stroke-width="2"/>
  <text x="530" y="152" text-anchor="middle" font-size="20">4</text>

  <circle cx="730" cy="145" r="34" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="730" cy="145" r="26" fill="none" stroke="black" stroke-width="2"/>
  <text x="730" y="152" text-anchor="middle" font-size="20">5</text>

  <circle cx="730" cy="330" r="34" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="730" cy="330" r="26" fill="none" stroke="black" stroke-width="2"/>
  <text x="730" y="337" text-anchor="middle" font-size="20">6</text>

  <circle cx="530" cy="470" r="34" fill="white" stroke="black" stroke-width="2"/>
  <text x="530" y="477" text-anchor="middle" font-size="20">7</text>

  <circle cx="730" cy="470" r="34" fill="white" stroke="black" stroke-width="2"/>
  <text x="730" y="477" text-anchor="middle" font-size="20">8</text>

  <circle cx="930" cy="470" r="34" fill="white" stroke="black" stroke-width="2"/>
  <circle cx="930" cy="470" r="26" fill="none" stroke="black" stroke-width="2"/>
  <text x="930" y="477" text-anchor="middle" font-size="20">9</text>

  <circle cx="930" cy="260" r="34" fill="white" stroke="black" stroke-width="2"/>
  <text x="930" y="267" text-anchor="middle" font-size="20">P</text>

  <!-- main accepted paths -->

  <path d="M180 242 L300 165" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5_ex5)"/>
  <text x="240" y="185" text-anchor="middle" font-size="18">a</text>

  <path d="M180 278 L300 357" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5_ex5)"/>
  <text x="240" y="345" text-anchor="middle" font-size="18">b</text>

  <path d="M360 360 L500 338" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5_ex5)"/>
  <text x="430" y="335" text-anchor="middle" font-size="18">a</text>

  <path d="M360 150 L500 145" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5_ex5)"/>
  <text x="430" y="130" text-anchor="middle" font-size="18">b</text>

  <path d="M560 145 L696 145" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5_ex5)"/>
  <text x="630" y="125" text-anchor="middle" font-size="18">a</text>

  <path d="M560 330 L696 330" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5_ex5)"/>
  <text x="630" y="310" text-anchor="middle" font-size="18">b</text>

  <path d="M360 390 L500 455" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5_ex5)"/>
  <text x="430" y="445" text-anchor="middle" font-size="18">b</text>

  <path d="M564 470 L696 470" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5_ex5)"/>
  <text x="630" y="450" text-anchor="middle" font-size="18">b</text>

  <path d="M764 470 L896 470" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5_ex5)"/>
  <text x="830" y="450" text-anchor="middle" font-size="18">a</text>

  <!-- wrong transitions to P -->

  <path d="M340 112 C460 40, 780 40, 910 230" fill="none" stroke="black" stroke-width="1.7" marker-end="url(#arrow_td5_ex5)"/>
  <text x="625" y="50" text-anchor="middle" font-size="16">a</text>

  <path d="M545 295 C630 240, 760 230, 896 255" fill="none" stroke="black" stroke-width="1.7" marker-end="url(#arrow_td5_ex5)"/>
  <text x="720" y="235" text-anchor="middle" font-size="16">a</text>

  <path d="M535 180 C630 245, 760 265, 896 260" fill="none" stroke="black" stroke-width="1.7" marker-end="url(#arrow_td5_ex5)"/>
  <text x="720" y="278" text-anchor="middle" font-size="16">b</text>

  <path d="M730 180 C760 230, 820 250, 896 260" fill="none" stroke="black" stroke-width="1.7" marker-end="url(#arrow_td5_ex5)"/>
  <text x="800" y="220" text-anchor="middle" font-size="16">a,b</text>

  <path d="M730 365 C760 330, 820 290, 896 270" fill="none" stroke="black" stroke-width="1.7" marker-end="url(#arrow_td5_ex5)"/>
  <text x="820" y="330" text-anchor="middle" font-size="16">a,b</text>

  <path d="M530 436 C590 360, 760 285, 896 265" fill="none" stroke="black" stroke-width="1.7" marker-end="url(#arrow_td5_ex5)"/>
  <text x="705" y="350" text-anchor="middle" font-size="16">a</text>

  <path d="M730 436 C760 365, 830 300, 900 275" fill="none" stroke="black" stroke-width="1.7" marker-end="url(#arrow_td5_ex5)"/>
  <text x="820" y="380" text-anchor="middle" font-size="16">b</text>

  <path d="M930 436 C920 370, 910 320, 920 295" fill="none" stroke="black" stroke-width="1.7" marker-end="url(#arrow_td5_ex5)"/>
  <text x="895" y="365" text-anchor="middle" font-size="16">a,b</text>

  <!-- loop on P -->

  <path d="M905 225 C845 165, 1015 165, 955 225" fill="none" stroke="black" stroke-width="2" marker-end="url(#arrow_td5_ex5)"/>
  <text x="930" y="180" text-anchor="middle" font-size="18">a,b</text>
</svg>

---

# 8. Vérification des mots acceptés

## Mot `a`

```text
a : 0 --a--> 1
```

L’état `1` est final, donc `a` est accepté.

---

## Mot `ba`

```text
ba : 0 --b--> 2 --a--> 3
```

L’état `3` est final, donc `ba` est accepté.

---

## Mot `aba`

```text
aba : 0 --a--> 1 --b--> 4 --a--> 5
```

L’état `5` est final, donc `aba` est accepté.

---

## Mot `bab`

```text
bab : 0 --b--> 2 --a--> 3 --b--> 6
```

L’état `6` est final, donc `bab` est accepté.

---

## Mot `bbba`

```text
bbba : 0 --b--> 2 --b--> 7 --b--> 8 --a--> 9
```

L’état `9` est final, donc `bbba` est accepté.

---

# 9. Vérification de quelques mots refusés

## Mot `b`

```text
b : 0 --b--> 2
```

L’état `2` n’est pas final, donc `b` est refusé.

---

## Mot `aa`

```text
aa : 0 --a--> 1 --a--> P
```

L’état `P` n’est pas final, donc `aa` est refusé.

---

## Mot `ab`

```text
ab : 0 --a--> 1 --b--> 4
```

L’état `4` n’est pas final, donc `ab` est refusé.

---

## Mot `bb`

```text
bb : 0 --b--> 2 --b--> 7
```

L’état `7` n’est pas final, donc `bb` est refusé.

---

# 10. Réponse modèle pour l’examen

```text
On construit un automate sous forme d’arbre de préfixes des mots du langage.
Les états finaux sont les états atteints après lecture complète des mots a, ba, aba, bab et bbba.
Toutes les transitions qui ne peuvent plus mener à un mot du langage vont vers l’état puits P.

Ainsi, l’automate reconnaît exactement le langage {a, ba, aba, bab, bbba}.
```

---

# 11. Ce qu’il faut retenir

Pour un langage fini, il ne faut pas mettre une boucle générale sur un état final.

Sinon, l’automate accepte trop de mots.

La bonne méthode est :

```text
1) construire un chemin exact pour chaque mot accepté ;
2) mettre final seulement les états correspondant aux fins des mots ;
3) envoyer les mauvaises transitions vers un état puits P ;
4) faire boucler P sur toutes les lettres.
```











