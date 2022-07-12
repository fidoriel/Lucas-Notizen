### Parse Baum
- Syntaxprüfung durch EBNF-Gramatik
- Semantikprüfung
	- Existenz der Relation
	- Typenkorrekte Vergleiche
	- Aggregation korrekt
![[ParseTree.png]]
=> Umwandelung in Operatorbaum
=> Gewichte von unten an Kanten schreiben und nach oben Zusammenrechnen
![[OperatorTree.png]]

### Transformation
- ohne Semantikveränderung
- finden äuivivalenter Ausdrücke (=> auf jeder Instanz gleiche Ergebnisse)
	- kleine Zwischenergebnisse

![[Trans1.png]]
![[Trans2.png]]
Anfragebaum/Algebraischer Ausdruck
Ausführungskosten schätzen

$\cup, \cap, \times und \bowtie$ => kommutativ und assoziativ
![[Optimierungsregeln.png]]

### Optimierung

Kosten oder Regelbasiert
- Logische Optimierung => bester Ausführungsplan 
Daten Resourcen nicht Exakt bekannt
__nicht zu lange optimieren => kein Gewinn__

##### Statistiken in DB
- Histogramme
- Jeden Tag Mitternacht
- Nach 1000 Änderungen etc.

##### Kosten
- Projektion hat keine Kosten
- Selektion
	- Alle Daten lesen
	- Index beschläunigt
	- Kostentreiber Tupelweitergabe

Join
- Algorithmenkosten

Größte Kosten DiscIO Hauptspeicher billig

Join Quadratischer Vergleich, Skaliert linear
Hauptspeichergröße?

Wie groß ist der Qutput des nächsten Operators?

#### Selektivität
Kosten 
Projektion: 1
Selektion: Ausgabe/Eingabe
Join: Jointupel/Kreuzprodukt

Projektion
sf = 1
Selektionsfaktor (geschätzt, da Ergebnis nicht bekannt) auf Tupel
sf=1/|R|
sf= |sigma(R)/|R|
Selektion auf ein Attribut A mit m verschiedenen Werden
sf = (|R|/m)/|R| = 1/|R|
Equijoin
sf = |R j S|/|R x S| = |S|/(|R|*|S|) = 1/|R|

Abweichung von Normalverteilung sorgt für schlechte Schätzungen
=> Histogramm
=> Sampling 1% nehmen und Schätzen und dann Skalieren > Anfrageplanveränderung auf Basis der Daten

Histogramme gehen bei Joins in die Tiefe  z.B. Preisestufen und Verkäufe