

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



## Tableau des expressions classiques en langages formels

| Expression | Signification en français | معنی ساده |
|---|---|---|
| `A` | alphabet | مجموعه حروف مجاز |
| `A*` | tous les mots possibles sur `A` | همه کلمات ممکن با حروف `A` |
| `ε` | mot vide | کلمه خالی، طول `0` |
| `a*` | zéro ou plusieurs `a` | صفر یا چندتا `a` |
| `b*` | zéro ou plusieurs `b` | صفر یا چندتا `b` |
| `a+` | un ou plusieurs `a` | حداقل یک `a` |
| `b+` | un ou plusieurs `b` | حداقل یک `b` |
| `ab` | un `a` suivi d’un `b` | اول `a` بعد `b` |
| `a* b+` | zéro ou plusieurs `a`, puis un ou plusieurs `b` | اول فقط `a`ها، بعد فقط `b`ها، حداقل یک `b` لازم است |
| `b* a b*` | zéro ou plusieurs `b`, puis un `a`, puis zéro ou plusieurs `b` | دقیقاً یک `a` |
| `b* a b* a b*` | mots avec exactement deux `a` | دقیقاً دو `a` |
| `A* a A*` | mots contenant au moins un `a` | حداقل یک `a` دارد |
| `A* b A*` | mots contenant au moins un `b` | حداقل یک `b` دارد |
| `a A*` | mots qui commencent par `a` | با `a` شروع می‌شود |
| `b A*` | mots qui commencent par `b` | با `b` شروع می‌شود |
| `A* a` | mots qui se terminent par `a` | با `a` تمام می‌شود |
| `A* b` | mots qui se terminent par `b` | با `b` تمام می‌شود |
| `a A* b` | mots qui commencent par `a` et se terminent par `b` | با `a` شروع و با `b` تمام می‌شود |
| `A* ab` | mots qui se terminent par `ab` | با `ab` تمام می‌شود |
| `ab A*` | mots qui commencent par `ab` | با `ab` شروع می‌شود |
| `(ab)*` | répétition de `ab` zéro ou plusieurs fois | تکرار `ab`: مثل `ε`, `ab`, `abab` |
| `(a\|b)*` | tous les mots sur `{a,b}` | مثل `A*` وقتی `A = {a,b}` |
| `A* \ L` | complémentaire de `L` dans `A*` | همه کلمات داخل `A*` که در `L` نیستند |



