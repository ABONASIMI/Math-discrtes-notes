
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
