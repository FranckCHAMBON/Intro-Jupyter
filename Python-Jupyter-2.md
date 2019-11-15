---
export_on_save:
  html: true
---

![Humans outnumbered by Lego people](assets/equations.png "https://xkcd.com/2034/")

# Écrire des mathématiques simples avec Jupyter {ignore=true}

@import "assets/Jupyter.svg" {width="300px" height="200px" title="Logo de Jupyter" alt="logo de Jupyter"}

## Sommaire {ignore=true}

[TOC]



Dans la plupart des pages HTML, on peut écrire des maths avec les bonnes balises et les bonnes commandes.

\[\sum\limits_{k\in\mathbb N^*} \frac 1 {k^2} = \frac {\pi^2}6 \quad \text{: Problème de Bâle, résolu par Leonhard Euler.}\]

Commençons par un tour d'horizon des possibilités en [comparant les deux moteurs](https://www.intmath.com/cg5/katex-mathjax-comparison.php "KaTeX vs MathJax") de rendu les plus répandus.

> Nous allons voir comment écrire des maths, en commençant par les choses les plus simples, et cela pourra faire office de révisions pour certains. Chaque partie contient des exercices à réaliser.  
**Ouvrir une feuille de calcul [Jupyter](https://jupyter.org/try), et c'est parti !**

## I] La balise math `$` ; pour écrire des nombres
Il y a deux façons de placer des maths dans un document Jupyter :
* Au milieu du texte qu'on écrit ; en ligne.
    + Dans ce cas : `$`_<code math à écrire là>_`$`
    + C'est la méthode qui est employée la plus fréquente,
        - mais parfois, on trouve `\(`_<code math à écrire là>_`\)`
        - avec Moodle, il s'agira de `$$`_<code math à écrire là>_`$$`
* Dans un paragraphe dédié, centré ; en mode équation.
    + la méthode obligatoire pour Jupyter est `$$`_<code math à écrire là>_`$$`,
        - mais on trouve souvent `\[`_<code math à écrire là>_`\]` pour les documents LaTeX



> **Attention** : pas d'espaces après la balise ouvrante, ni avant la balise fermante.

#### Exemples
```markdown
$$x+y= y + x$$
```
$$x+y= y + x$$

```markdown
La somme de $123$ et 123 est égale à $123 +123$.
```
La somme de $123$ et 123 est égale à $123 +123$.

#### Remarques
* Avec le premier exemple, on voit que l'espacement est correct, indépendamment de la source. C'est bien !
* Avec le second exemple, bien voir la différence d'écriture des deux premiers $123$. Dans un souci de cohérence, il vaut mieux :
    + mettre tous les nombres avec lesquels ont fait du calcul entre balises maths. Même status, même écriture...
    + Pour des années, ou des numéros de page (par exemple), on peut les écrire sans balises maths. Tant qu'on ne fait pas de calcul avec ensuite. Sauf besoin spécifique.
* LaTeX gère finement les espaces de manière globale.
    + Conseil : écrire de manière à aérer le code, qu'il soit lisible.
    + Le moteur de rendu choisira les bonnes tailles d'espaces à afficher. C'est un principe de fonctionnement.


#### Motivation
L'inspiration du HTML vient de TeX, inventé par [Donald Knuth](https://fr.wikipedia.org/wiki/Donald_Knuth "Article Wikipedia").

Écrire un document en utilisant LaTeX est une nécessité pour beaucoup d'étudiants en thèse, et nombre de professionnels. Ce n'est pas [un apprentissage rapide](https://fr.wikibooks.org/wiki/LaTeX), mais cela permet d'obtenir une très grande qualité.

> Utiliser Markdown, avec quelques connaissances de la balise maths LaTeX, permet de créer facilement des documents scientifiques honorables. Avec Jupyter, on peut facilement alterner entre cellule de texte et cellule de code.


#### Plus de détails sur les espaces
* Comme dans les balises HTML, la gestion des espaces est laissé au moteur de rendu, pour chaque cas.
* Dans les balises maths, entre deux lettres ou chiffres, les espaces sont ignorés.
* Pour modifier de l'espace que LaTeX a prévu, il y a plusieurs possibilités complexes :
    + l'espace fine `\,` ($\frac3{18}$ de em)
    + l'espace fine négative `\!` ($\frac{-3}{18}$ de em)
    + l'espace moyenne `\:` ($\frac4{18}$ de em)
    + l'espace large `\;` ($\frac5{18}$ de em)
    + le cadratin `\quad` ($1$ em)
    + le double cadratin `\qquad` ($2$ em)
    + Le em étant une unité, la largeur de la lettre M avec la police courante.
* Il y a un moyen simple de créer une [espace insécable](https://fr.wikipedia.org/wiki/Espace_ins%C3%A9cable) en mode mathématique :
    + `~` est une bonne idée pour le séparateur des milliers.
    + `~` est une bonne idée pour séparer un nombre et son unité.

##### Exemples :
|Code|Résultat affiché|
|---|---:|
|`$12 34 56 78 90$` | $12 34 56 78 90$|
|`$123~456~789$` | $123~456~789$|
|`$12~34~56~78~90$` | $12~34~56~78~90$|
|`$123.456~\mathrm{m}$`|$123.456~\mathrm{m}$|
|`$47.02~\mathrm{m}^2$`|$47.02~\mathrm{m}^2$|

Les deux derniers exemples seront revus à la fin de cette page.




## II] Les 4 opérations et les nombres
Dans une cellule Markdown, à l'intérieur de balises math,
* L'addition s'obtient avec `+`
* La soustraction s'obtient avec `-`
* La multiplication s'obtient avec `\times`
* La division s'obtient avec `\div`

> Remarque 1 : D'ici quelques ~~temps~~ années les claviers respectant la nouvelle norme AFNOR donneront accès rapidement à ×, ÷, et seront plus commodes pour écrire certaines lettres comme É, È, Ç, ...

> Remarque 2 : Dans une cellule de code Python, c'est plus facile :
* La multiplication s'obtient avec `*`
* La division s'obtient avec `/`


#### Exemple
```markdown
$[5 + 3\times8 - (1 + 35\div5)](18  -  5 \times 2)$
```

$[5 + 3\times8 - (1 + 35\div5)](18  -  5 \times 2)$

#### Exercice 1
![un calcul](images/calcul1.png)

1. Calculer avec une cellule Python l'expression numérique précédente,
2. puis afficher cette expression avec son résultat dans une cellule Markdown.

#### Exercice 2
![un calcul](images/calcul2.png)
1. Calculer avec une cellule Python l'expression numérique précédente.
2. Compléter alors le code `$3 + ... \approx \pi$`
3. (maths) Écrire le membre de gauche comme une seule fraction.
4. Pour les plus curieux à ce sujet, [un peu de lecture](https://fr.wikipedia.org/wiki/Fraction_continue#D%C3%A9veloppement_en_fraction_continue_du_nombre_%CF%80 "Article Wikipédia")

## III] Du calcul littéral
On peut bien sûr utiliser des variables mathématiques, elles seront écrites en italique, avec une police un peu différente.
* Dans l'exemple 1, comparer les lettres `a` (dans «on a», et dans «$ka+kb$»).
* Dans l'exemple 2, noter qu'il faut une espace après `\times`, sinon la commande `\timesH` est cherchée et non trouvée.

#### Exemple 1
```markdown
Pour tous nombres $k$, $a$, $b$, on a :  
$k(a+b) = ka + kb$
```
> Pour tous nombres $k$, $a$, $b$, on a :  
$k(a+b) = ka + kb$

#### Exemple 2
```markdown
Le volume d'un pavé droit de longueur $L$, de hauteur $H$ et
de profondeur $P$ est  
$V = L \times H \times P$
```
> Le volume d'un pavé droit de longueur $L$, de hauteur $H$ et
de profondeur $P$ est  
$V = L \times H \times P$

#### Remarque
Si on souhaite mieux écrire une formule d'aire ou de volume, on devine la nécessité :
* de savoir écrire des fractions,
* de savoir écrire des parenthèses à la bonne taille,
* de savoir écrire des puissances,
* de savoir écrire en indice,
* de savoir faire une écriture scripte : $\mathscr V$ pour volume, $\mathscr A$ pour aire, $\mathscr C$ pour cercle, ...
* de savoir écrire quelques lettres grecques, comme $\pi$ ou $\alpha$.

Voilà donc la suite de notre programme. Pas d'exercices ici, mais plein ensuite !



## IV] Les fractions ; `$\dfrac{ }{ }$`

|Code|Résultat affiché|
|----|--------:|
|`$\dfrac{num}{den}$` | $\dfrac{num}{den}$ |
|`$\dfrac{22}{7}$` | $\dfrac{22}{7}$ |
|`$5+\dfrac{x+7}{x-1}$` | $5+\dfrac{x+7}{x-1}$|


#### Exercice 1
Écrire dans une cellule Markdown, les règles fondamentales sur les écritures fractionnaires :

> ![règles fractions](images/fractions1.png)

Voici un code à copier/coller/compléter.

```markdown
Pour $a$, $b$, $c$ et $d$ des nombres, avec $b$ et $d$ non nuls, on a :

$\dfrac{a}{b} + $

$\dfrac{a}{b} \times $

$a\div$
```


#### Exercice 2
Recréer en Markdown, et vérifier les résultats ci-dessous :

> ![fraction approchant pi](images/fraction2.png)


#### Remarques
* Si le contenu d'un paramètre entre accolades n'est qu'un seul caractère, les accolades ne sont pas nécessaires.
* Si ce caractère est un chiffre, on peut même le coller à `\dfrac`

Exemples :

>|Code|Résultat|
>|----|--------:|
>|`$\dfrac12$` | $\dfrac12$ |
>|`$\dfrac1x$` | $\dfrac1x$ |
>|`$\dfrac ab$` | $\dfrac ab$ |



## V] Les parenthèses à la bonne taille
Si on veut placer un bloc (une expression) entre parenthèses, et que l'expression est plus haute que la normale (avec des fractions par exemple), alors les parenthèses normales ne sont pas assez hautes.
> `$( \dfrac ab )$` donne $( \dfrac ab )$ ; qui est disgracieux.

> `$\left( \dfrac ab \right)$` donne $\left( \dfrac ab \right)$ ; qui est correct




## VI] Les puissances `$a^n$` pour $a^n$
> De manière générale `$base^{ exposant }$` donne $base^{ exposant }$

Les accolades sont nécessaires pour des exposants qui ont plus d'un caractère.

#### Exercice 1
Retrouver les formules apprises au collège sur les puissances, puis compléter le code ci-dessous.
```markdown
Pour tous nombres $a$, $b$, $c$ (non nul), et tous entiers $n$, $m$, on a :

$a^n \times a^m = $

$a^n \times b^n = $
```
L'objectif étant d'obtenir le résultat (à compléter) ci-dessous :

> ![formules puissances](images/puiss1.png)

#### La Racine carrée
En anglais _**sq**uare __r__oo**t**_ ; `sqrt` est massivement utilisé.

Exemple : `$\sqrt{ radicande }$` donne $\sqrt{ radicande }$

#### Exercice 2
![exo pythagore](images/pyth1.png)

En vous inspirant du modèle ci-dessus, rédiger une solution au problème suivant :
> $RST$ est un triangle rectangle en $R$, avec $RT = 21$, $RS=28$. Calculer $ST$.

On pourra utiliser, modifier, et compléter le code suivant :

```markdown
> $ABC$ est un triangle rectangle en $A$, avec $AB = 45$, $AC=28$. Calculer $BC$.
> **Réponse** :
> $ABC$ est un triangle rectangle en $A$, d'après le théorème de Pythagore, on a :
> $BC^2 = $

```

> **Remarque** : le principe d'utiliser, modifier, compléter du code est largement utilisé dans l'enseignement. Il faut cependant savoir que certains codes sont protégés par du droit d'auteur. Les logiciels libres permettent aux utilisateurs avertis de pouvoir améliorer le code et d'en faire profiter tout le monde.


## VII] Les indices `$a_n$` pour $a_n$
Mêmes principes que pour les exposants.
> `$bloc_{ indice }$` donne $bloc_{ indice }$

**Attention** à un point particulier, `indice` est ici en mode mathématique, tout comme `bloc`.
> Pour écrire `indice` comme du texte, on utilise la commande `\text{ }`
>
>`$bloc_\text{ indice }$` donne $bloc_\text{ indice }$


## VIII] Écriture scripte, pour aires, volumes, cercles...
Pour démarquer certaines lettres, en mode **math**-ématique, on utilise l'écriture **scr**-ipte,
> d'où la commande `$\mathscr{ }$`.

|Code|Affichage associé|
|----|-----:|
|`Le cercle $\mathscr C$`|Le cercle $\mathscr C$|
|`Le volume $\mathscr V$`|Le volume $\mathscr V$|
|`L'aire $\mathscr A_{RST}$`|L'aire $\mathscr A_{RST}$|
|`L'aire $\mathscr A_\text{triangle}$`|L'aire $\mathscr A_\text{triangle}$|

> Noter dans les deux derniers exemples, que `RST` est bien en mode math, alors que
`\text{triangle}` produit du texte dans le mode math. C'est bien la bonne méthode.

#### Exercice (un peu long):
Écrire de belles formules pour :
* Le carré
    * Le périmètre d'un carré de côté $a$.
    * L'aire d'un carré de côté $a$.
* Le rectangle
    * Le périmètre d'un rectangle de côtés $a$ et $b$.
    * L'aire d'un rectangle de côtés $a$ et $b$.
* Le triangle
    * Le périmètre d'un triangle de côtés $a$, $b$ et $c$.
    * L'aire d'un triangle de côté $a$ et de hauteur associée $h$.
* Le cercle
    * La circonférence d'un cercle de rayon $r$.
    * L'aire d'un cercle de rayon $r$.
* Les volumes pour
    + Un pavé droit de côtés $L$, $H$, $P$.
    + Un prisme droit dont la base a une aire $\mathscr A_\text{base}$, et une hauteur $h$ associée.
    + Une pyramide dont la base a une aire $\mathscr A_\text{base}$, et une hauteur $h$ associée.
    + Une boule de rayon $r$.


#### Remarque sur les unités
On devrait utiliser une [espace fine insécable](https://fr.wikipedia.org/wiki/Espace_ins%C3%A9cable) entre la partie numérique et l'unité.

* Pour simplifier, on peut utiliser une espace-mot insécable à la place.
* Pour écrire les unités, on pourra donc suivre les exemples :

|Code|Affichage produit|
|---|---:|
|`$41~\text{km}$`|$41~\text{km}$|
|`$35~\text{m}^2$`|$35~\text{m}^2$|


## IX] Pour aller plus loin
* Avec ce qui a été vu précédemment, on peut écrire une large partie d'un cours de mathématique au collège.
* Une autre page traitera des mathématiques du lycée, en seconde pour commencer.
* Une partie de cette [section](https://fr.wikibooks.org/wiki/LaTeX/%C3%89crire_des_math%C3%A9matiques) est valable pour le mode mathématique en Markdown.
La [suite](https://fr.wikibooks.org/wiki/LaTeX/Math%C3%A9matiques) pourra être utile.



TODO
## Exercice de création d'un carnet complet.