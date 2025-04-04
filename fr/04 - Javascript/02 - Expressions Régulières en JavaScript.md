
# Expressions Régulières en JavaScript

Les expressions régulières (regex) sont des outils puissants utilisés pour la correspondance de motifs, la validation et la manipulation de chaînes de caractères. Ce cours couvre les sujets avancés des regex et montre comment les utiliser efficacement en JavaScript.

## Table des Matières
1. [Introduction aux Expressions Régulières](#introduction-aux-expressions-régulières)
2. [Syntaxe de Base et Motifs](#syntaxe-de-base-et-motifs)
3. [Caractères Spéciaux : `.`, `^`, `$`, `[]`, `()`, `|`](#caractères-spéciaux-.,-^,-$,-[],-(),-|)
4. [Quantificateurs : `*`, `+`, `?`, `{n,m}`](#quantificateurs-,-+,--,-{n,m})
5. [Classes de Caractères : `\d`, `\w`, `\s`, etc.](#classes-de-caractères-\d,-\w,-\s,-etc)
6. [Ancres : `^`, `$`, `\b`, `\B`](#ancres-^,-$,-\b,-\B)
7. [Groupes et Capture](#groupes-et-capture)
8. [Assertions : Lookahead et Lookbehind](#assertions-lookahead-et-lookbehind)
9. [Flags : `g`, `i`, `m`, `s`, `y`](#flags-g,-i,-m,-s,-y)
10. [Utilisation du Constructeur `RegExp` vs Notation Littérale](#utilisation-du-constructeur-regexp-vs-notation-littérale)
11. [Tester les Motifs avec `test()` et `exec()`](#tester-les-motifs-avec-test-et-exec)
12. [Remplacer avec `replace()` et les Groupes de Capture](#remplacer-avec-replace-et-les-groupes-de-capture)
13. [Correspondance de Plusieurs Occurrences](#correspondance-de-plusieurs-occurrences)
14. [Considérations sur la Performance des Regex](#considérations-sur-la-performance-des-regex)

---

## Introduction aux Expressions Régulières
Les expressions régulières sont des motifs utilisés pour faire correspondre des combinaisons de caractères dans des chaînes. Elles sont largement utilisées pour la recherche, la validation et la manipulation de texte.

Exemple :
```javascript
let regex = /world/;
let result = regex.test("Hello, world!");  // true
```

---

## Syntaxe de Base et Motifs
Les motifs regex sont définis en les encadrant par des barres obliques (`/motif/`). Les motifs de base correspondent à des séquences de caractères exactes.

Exemple :
```javascript
let regex = /abc/;
console.log(regex.test("abcdef"));  // true
console.log(regex.test("defabc"));  // false
```

---

## Caractères Spéciaux : `.`, `^`, `$`, `[]`, `()`, `|`
Les caractères spéciaux ont des significations particulières. Ceux-ci incluent le point `.` (n'importe quel caractère), `^` (début de chaîne), `$` (fin de chaîne), les crochets `[]` (classes de caractères), les parenthèses `()` (groupement) et la barre verticale `|` (alternative).

Exemple :
```javascript
let regex = /^a.b$/;  // Correspond à une chaîne commençant par 'a', suivie de n'importe quel caractère, et se terminant par 'b'
console.log(regex.test("axb"));  // true
console.log(regex.test("ab"));   // false

let altRegex = /cat|dog/;
console.log(altRegex.test("dog"));  // true
```

---

## Quantificateurs : `*`, `+`, `?`, `{n,m}`
Les quantificateurs définissent le nombre de fois qu'un élément du motif doit apparaître. `*` signifie 0 ou plus, `+` signifie 1 ou plus, `?` signifie 0 ou 1, et `{n,m}` signifie entre `n` et `m` occurrences.

Exemple :
```javascript
let regex = /a{2,4}/;  // Correspond à 'aa', 'aaa' ou 'aaaa'
console.log(regex.test("aaa"));  // true
console.log(regex.test("a"));    // false
```

---

## Classes de Caractères : `\d`, `\w`, `\s`, etc.
Les classes de caractères définissent un ensemble de caractères à faire correspondre. `\d` correspond aux chiffres, `\w` correspond aux caractères de mot et `\s` correspond aux caractères d'espacement.

Exemple :
```javascript
let regex = /\d+/;  // Correspond à un ou plusieurs chiffres
console.log(regex.test("12345"));  // true
console.log(regex.test("abc"));    // false
```

---

## Ancres : `^`, `$`, `\b`, `\B`
Les ancres sont utilisées pour faire correspondre des positions dans les chaînes. `^` correspond au début, `$` correspond à la fin, `\b` correspond aux limites de mots et `\B` correspond aux limites de non-mots.

Exemple :
```javascript
let regex = /^hello/;  // Correspond à 'hello' au début d'une chaîne
console.log(regex.test("hello world"));  // true
console.log(regex.test("world hello"));  // false

let wordBoundaryRegex = /\bcat\b/;
console.log(wordBoundaryRegex.test("my cat is cute"));  // true
```

---

## Groupes et Capture
Les parenthèses `()` sont utilisées pour grouper des motifs. Les groupes de capture stockent le contenu correspondant pour une utilisation ultérieure.

Exemple :
```javascript
let regex = /(\d{3})-(\d{2})-(\d{4})/;
let result = regex.exec("123-45-6789");
console.log(result[1]);  // 123 (premier groupe capturé)
```

---

## Assertions : Lookahead et Lookbehind
Les assertions permettent de faire correspondre un motif uniquement s'il est suivi (lookahead) ou précédé (lookbehind) par un autre motif, sans consommer de caractères.

Exemple :
```javascript
let lookaheadRegex = /(?=\d{3})\d+/;  // Lookahead positif pour un nombre à trois chiffres
console.log(lookaheadRegex.test("12345"));  // true

let lookbehindRegex = /(?<=@)\w+/;  // Lookbehind positif pour '@'
console.log(lookbehindRegex.test("user@example.com"));  // true
```

---

## Flags : `g`, `i`, `m`, `s`, `y`
Les flags modifient le comportement des regex. `g` est pour les correspondances globales, `i` pour l'insensibilité à la casse, `m` pour le multi-lignes, `s` pour le dot-all (correspond à la nouvelle ligne) et `y` pour les correspondances persistantes.

Exemple :
```javascript
let regex = /hello/i;  // Recherche insensible à la casse
console.log(regex.test("Hello"));  // true
```

---

## Utilisation du Constructeur `RegExp` vs Notation Littérale
Vous pouvez créer des motifs regex en utilisant des littéraux (`/motif/`) ou le constructeur `RegExp` (`new RegExp("motif")`).

Exemple :
```javascript
let regexLiteral = /abc/;
let regexConstructor = new RegExp("abc");

console.log(regexLiteral.test("abc"));  // true
console.log(regexConstructor.test("abc"));  // true
```

---

## Tester les Motifs avec `test()` et `exec()`
La méthode `test()` renvoie `true` si le motif correspond, et `false` sinon. La méthode `exec()` renvoie un tableau des résultats correspondants ou `null`.

Exemple :
```javascript
let regex = /\d+/;

// Using test()
console.log(regex.test("abc123"));  // true

// Using exec()
let result = regex.exec("abc123");
console.log(result[0]);  // "123"
```

---

## Remplacer avec `replace()` et les Groupes de Capture
La méthode `replace()` vous permet de remplacer les motifs correspondants par un nouveau texte. Vous pouvez également utiliser des groupes capturés pour référencer des parties de la correspondance.

Exemple :
```javascript
let regex = /(\d{3})-(\d{2})-(\d{4})/;
let replaced = "123-45-6789".replace(regex, "$1.$2.$3");
console.log(replaced);  // "123.45.6789"
```

---

## Correspondance de Plusieurs Occurrences
Le flag `g` vous permet de faire correspondre plusieurs occurrences d'un motif dans une chaîne.

Exemple :
```javascript
let regex = /\d+/g;
let result = "The numbers are 123, 456, and 789.".match(regex);
console.log(result);  // ["123", "456", "789"]
```

---

## Considérations sur la Performance des Regex
Les performances des regex peuvent varier en fonction de la complexité du motif. Évitez les motifs trop complexes ou le backtracking inutile, et envisagez d'utiliser des quantificateurs non gourmands.

Exemple :
```javascript
let regex = /.*a.*b/;  // Peut entraîner un backtracking excessif sur de grandes chaînes
console.log(regex.test("aaabbb"));  // true
```

---

## Conclusion

### Points Clés à Retenir :
1. Les expressions régulières sont puissantes pour la correspondance de motifs et la manipulation de texte.
2. Les caractères spéciaux et les quantificateurs définissent comment les motifs sont mis en correspondance dans les chaînes.
3. Les assertions, les flags et les groupes de capture améliorent la fonctionnalité des regex.
4. Les méthodes `test()` et `exec()` sont essentielles pour la correspondance de motifs.
5. Tenez toujours compte des performances lors de l'écriture de motifs regex complexes.

### Exercice Pratique :
1. Écrivez une regex pour valider un numéro de téléphone au format `(XXX) XXX-XXXX`.
2. Utilisez `replace()` pour formater les dates de `MM-DD-YYYY` vers `YYYY/MM/DD`.
3. Créez une regex pour faire correspondre les adresses e-mail valides et utilisez `test()` pour valider une chaîne d'e-mail.
