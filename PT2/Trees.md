## Grundlagen
ist ein gerichteter Graph $G=(V,E)$ mit $n$ Knoten und $m$ Kanten
G ist zusammenhängend und zyklenfrei (azyklisch)
Knoten $V=\{v_1,\ldots,v_n\}$
Kanten $E = \{e_1, \ldots,e_n\} \subseteq V \times V$
- falls $G$ nicht leer
    $n = m+1$
- zu je zwei Knoten existiert genau ein Pfad, der beide Knoten verbindet
- $G$ ist minimal zusammenhängend (eine Kante weniger => nicht zusammenhängend)
- $G$ ist maximal azyklisch (eine Kante mehr => nicht azyklisch)

## Knoten
- ein Knoten $v$ ist inzident mit Kante $e$, wenn $v \in e$ Wurzel
	- Knoten mit Eingangsgrad 0
- Blätter
	- Knoten mit Ausgangsgrad 0
- Inneren Knoten
	- Knoten mit Eingangsgrad 1 und Ausgangsgrad > 0

### Eltern- und Kind
Jeder Knoten außer die Wurzel hat genau einen Elternknoten
Alle Knoten mit gleichem Elternknoten werden Geschwister genannt

### Eigenschaften
- Tiefe eines Knotens
	- ist die Anzahl der Kanten bis zur Wurzel
- Höhe des Baums
	- ist die maximale Tiefe über alle Knoten
- Level
	- alle Knoten mit gleicher Pfadlänge von Wurzel bis zum Knoten

### Flussordnungszahl
- Maß für die Verzweigung
- Blattknoten haben Ordnung $1$
- Kindknoten mit gleicher Ordnung
    => Elternknoten erhalten Ordnung + 1
- Kindknoten mit unterschiedlicher Ordnung
	=> Elternknoten erhält höhere Ordnung

### Traversierung
Iteration durch alle Knoten eines Baums

#### Pruning
Auslassen von Unterbäumen

###### Tiefensuche
so tief wie möglich im Baum hinabsteigen
=> bis zu einem Blatt
=> erst dann Geschwisterknoten
=> durch Stack

###### Breitensuche
erst alle Knoten eines Levels, dann Knoten der darunter folgenden Level
=> durch Queue

### Speicherung
#### Adjazenzliste
für jeden Knoten Liste aller Nachbarn angeben

#### Adjazenzmatrix
für jeden Knoten alle Knoten angeben
=> hinterlegen, ob verbunden oder nicht verbunden
=> zweidimensionales Array

#### Kantenliste
nur Kanten speichern
=> falls Knoten nicht verbunden sind, werden sie nicht erfasst

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


