# TP_BI_Data_Analysis
## Yanis Jacob

### Question 3 : Valeurs manquantes
#### Y a-t-il des valeurs manquantes ? Si oui, lesquelles et combien ?

Pour repérer les valeurs manquantes, j’ai utilisé la combinaison `isnull().sum()`

`isnull()` retourne `True` pour chaque cellule vide et `sum()` additionne ces `True` (True = 1) pour obtenir le nombre de valeurs manquantes
#

### Question 4 : Histogrammes
#### Trace les histogrammes de total_bill et tip (20 classes chacun). Interprète la distribution.

Les histogrammes montrent que la plupart des additions sont entre 10 et 20 dollars et les pourboires entre 2 et 4 dollars 
#


### Question 8 : Proportion des fumeurs
#### Quel est le pourcentage de fumeurs dans l'échantillon ? Différence entre hommes et femmes ?

Le jeu de données contient environ 38% de fumeurs

La répartition est assez équilibrée entre homme et femme
#

### Question 9 : Boxplot des pourboires par jour
#### Quels jours présentent une plus grande variabilité ?

Les jours avec la plus grande variabilité de pourboires sont samedi et dimanche (boîtes plus larges)
Vendredi est le jour avec la répartition la plus stable
#

### Question 10 : Scatterplot
#### Quelle tendance observe-t-on ?

Le nuage de points montre une tendance globale : plus le montant de l’addition est élevé plus le pourboire a tendance à augmenter
#  

### Question 11 : Corrélations linéaires

Utilisation de `pearsonr()` pour mesurer la corrélation entre les variables.

- Entre `total_bill` et `tip` : le coefficient de corrélation est d’environ **0.67** avec une p-value très faible → il existe une corrélation linéaire **positive significative**
- Entre `size` et `tip` : le coefficient est plus faible (**0.489**) mais reste positif → les pourboires augmentent avec le nombre de personnes mais moins fortement

**Documentation:**
https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.pearsonr.html
#

### Question 13 : Différence entre fumeurs et non-fumeurs
#### Y a-t-il une différence significative entre les pourboires des fumeurs et non-fumeurs ?

Les non-fumeurs donnent en moyenne un pourboire de **2.99** Dollars contre **3.00** Dollars pour les fumeurs

Cette différence n'est pas significative
#

### Question 16 : Conversion en NumPy
#### Quelle est la forme du tableau ? Que représente chaque dimension ?

J’ai converti les colonnes `total_bill` et `tip` en un tableau NumPy 2D avec `.to_numpy()`

La forme du tableau est `(n, 2)` :
- chaque **ligne** (244) correspond à une observation (un client),
- chaque **colonne** (2) représente une des deux variables (`total_bill`, `tip`)
#

### Question 18 : Filtrage conditionnel avec NumPy
#### Quelle est leur moyenne ?

J’ai utilisé un masque booléen (`size >= 4`) pour extraire les pourboires des grandes tables (4 personnes minimum)

La moyenne de ces pourboires est d’environ **4.22 $**
#

### Question 19 : Indexation booléenne avec Pandas
#### Avec Pandas uniquement, sélectionne toutes les lignes où le pourboire représente plus de 20% de l’addition (tip_pct > 0.2). Combien de cas cela concerne-t-il ?

J’ai filtré les lignes où le pourboire représente plus de 20 % de l’addition (`tip_pct > 0.2`).

Cela concerne 39 cas
#

### Question 23 : Groupes et écart-type
#### Utilise Pandas pour grouper par day et afficher l’écart-type du tip_pct. Quel jour est le plus variable ?

J’ai calculé l’écart-type de `tip_pct` pour chaque jour avec `.groupby("day")["tip_pct"].std()`

Le jour avec la plus grande variabilité est le **dimanche**
#

### Question 25 : Jointure avec concaténation
#### Puis concatène-les verticalement et vérifie si l’index est bien conservé ou non.

J’ai séparé le DataFrame en deux groupes (`Male` et `Female`) puis je les ai concaténés verticalement avec `pd.concat()`.

Le nouvel index **n’est pas identique** à celui du DataFrame d’origine (`.index.equals(...)` retourne `False`) car la concaténation conserve les index initiaux de chaque sous-groupe sans les réordonner.

