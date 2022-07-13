## Syntax

`SELECT` relation.spaltenname
`FROM` relation
`WHERE` spaltenname Vergleichsoperator 'String'

###### Erweiterung der Projektion
``SELECT`` Titel, Länge * 0.016667 ``AS`` Stunden, ‘std.‘ ``AS`` inStunden
``FROM`` Film