!todo VL Montag einführung Bäume
Blattknoten = Ausgangsgrad von 0

Traversieren
	- Depth First Search DFS
	- Breath first search BFS
## Binary Tree
Ausgangsgrad eines Knotens Maximal 2
v(Knoten) = e(Kanten) - 1

## Rot Schwarz Baum
Wurzen ist Schwarz
Kein Rot auf Rot
Jeder Pfad gleich viele Schwarzknoten
Jeder Blattknoten ein Nil Knoten

max Tiefe: 2 x Schwarzhöhe
Schwarzhöhe zeigt niedrigstes Level

Suchaufwand $O(log(n))$

Einfügen:
Fall 1:
	- Eltern Schwarz, neues Kind Rot
Fall 2:
	- Eltern Rot, neues Kind Rot, Elterm, Onkel, Großeltern, Farben flippen
Fall 3:
	- Links Rotation !todo https://en.wikipedia.org/wiki/Red–black_tree
Fall 4:
	-Rechts Rotation !todo

## Balancierter Baum
Bläter sind Sortiert
Jeder Blattknoten hat die selbe Tiefe
Blatt mindestens 2 max 3 Werte
Wurzel | |30| |
Verweise | |13| |20| |27| |
Merken ob Verweis oder Wert

#### Plus Baum
Verweise zwischen Kindern => linked list

Vom Likesten Kind, den Rechtesten wert nach oben
Unterbefüllt?
	linken Wert nach oben, Kinderknoten verschwelzen

Vollbesetzter Baum mindestens n/2 Elemente Verschwinden
b+ Baum Nur indices Verändern

## K-Tree
N-Dimensional

Halbieren der Menge mit jedem Rekursiven schritt
X halbieren
Y Halbieren
...
ML
Entscheidungsbaum
Rekursiv

## Quadtree
Raum Rekuriv in Quadranten aufteilen
3D aufteilung => OctTree
Komprimierung

##### Z/Morton-Kurve
Quadrantenabarbeitungsreihenfolge Sw, Nw, Se, Ne

Barneys Hat
	!todo https://en.wikipedia.org/wiki/Barnes–Hut_simulation


