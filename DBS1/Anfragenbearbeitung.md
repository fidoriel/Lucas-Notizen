Anfragebaum/Algebraischer Ausdruck
Ausführungskosten schätzen

Daten Resourcen nicht Exakt bekannt

Statistiken in DB
- Jeden Tag Mitternacht
- Nach 1000 Änderungen etc.

Projektion hat keine Kosten
Selektion
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

Selektionsfaktor auf Tupel
sf=1/|R|
Selektion auf ein Attribut A mit m verschiedenen Werden
sf = (|R|/m)/|R| = 1/|R|
Equijoin
sf = |R j S|/|R x S| = |S|/(|R|*|S|)

Abweichung von Normalverteilung sorgt für schlechte Schätzungen
=> Histogramm
=> Sampling 1% nehmen und Schätzen und dann Skalieren > Anfrageplanveränderung auf Basis der Daten

Histogramme gehen bei Joins in die Tiefe  z.B. Preisestufen und Verkäufe