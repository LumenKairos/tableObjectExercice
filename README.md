# tableObjectExercice

Toutes les pages devront avoir un code html ou des components react pour démontrer que les fonctionnalités présentes existent.

ex 00
===

rendu : /ex00.html

- La page doit exposer un namespace Tableau

Ce namespace doit exposer un constructeur 'create'
```javascript
  var tableau = Tableau.create(tableName) // si tableName existe, _name doit prendre la valeur de tableName.
```
propriétés publiques :
```javascript
  row // default : 0
  col // default : 0
  size // row * col
```
propriétés privées d'un objet tableau:
```javascript
  _name // default : 'myTable'
  _data // default : [[]]
  _colHeaders // default : []
  _rowHeaders // default : []
```
methodes publiques :

```javascript
  tableau.addRow('rowName'); // crée une nouvelle row, rowName. Si une row portant déja ce nom existe, le comportement est indeterminé
  tableau.addCol('colName'); // nouvelle colonne
  tableau.deleteRow('rowName'); // Supprime la row rowName. Si une row portant ce nom n'existe pas, le comportement est indeterminé
  tableau.deleteCol('colName'); // Supprime colonne

// ces méthodes doivent mettre row, col, size, colHeaders, rowHeaders et _data à jour
```

ex 01
===

rendu : /ex01.html

Le tableau de l'exercice précédent doit être repris et amélioré.

Objets :

un nouveau constructeur doit être écrit à la racine du namespace Tableau
Cellule

```javascript
  var cell = new Tableau.Cellule(value) //value is optional
  cell.value // the cell value, default is undefined
```
Méthode :

Modifier addRow(), etc. tel que chaque création de ligne ou de colonnes s'accompagne de l'allocation de cellules nécéssaires

getTable() :

```javascript
  tableau.getTable() // retourne un objet
  //{
  //  tableName: string
  //  rowHeaders: string array
  //  colHeaders: string array
  //  data: array d'array d'objet cellule
  //}
```

ex 02
===

rendu : /ex02.html

Le tableau de l'exercice précédent doit être repris et amélioré.

L'objectif de cet exercice est de permettre de créer des filtres

Propriétés privées : array de string
_hiddenCol, _visibleCol, _hiddenRow, _visibleRow

Nouvelles methodes :
hideCol(colName), hideRow(rowName), showCol(colName), showRow(rowName)

Pour toutes ces méthodes, si on tente de cacher un élément caché ou inexistant, ou de montrer un élément visible ou inexistant, le comportement est indéterminé.
Sinon, le nom de la ligne ou colonne affichée ou cachée doit être retiré d'un array et ajouté à l'autre.

Par défaut, quand une nouvelle colonne ou ligne est créée, son nom est ajouté à l'array de colonnes ou lignes visibles.

Modifier getTable()

Cette méthode doit désormais retourner un array n'ayant que les colonnes et lignes visibles.
