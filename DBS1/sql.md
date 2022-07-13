## Syntax
**SQL IST NICHT CASE SENSITIVE**

`SELECT` relation.spaltenname
`FROM` relation
`WHERE` spaltenname Vergleichsoperator 'String'

###### Erweiterung der Projektion
``SELECT`` Titel, Länge * 0.016667 ``AS`` Stunden, ‘std.‘ ``AS`` inStunden
``FROM`` Film

### Operatoren
**Gleich =**
**Ungleich <>**
<, >, <=, >=
auch für Lexikografische Vergleiche
Attribut muss nicht zwingend in `SELECT` vorkommen
###### String Concatination
Vorname || ' ' || Nachname = `Felix Naumann`

##### Bool
Constraints werden evaluiert, nur wenn TRUE in Endrelation
**TRUE, FALSE, NOT, OR, AND**

##### LIKE
```
SELECT Titel
FROM Film
WHERE Titel LIKE 'Star ____';
```
Star Wars und Star Trek
`_` beliebig
`*` Sequenz von 0 ode rmehr

### Zeit
Datumskonstante:
- DATE ‘YYYY-MM-DD‘
- DATE ‘1948-05-14‘

Zeitkonstante
- TIME ‘HH:MM:SS.S‘
- TIME ‘15:00:02.5‘

Timestamp
TIMESTAMP ‘1948-05-14 15:00:02.5‘

Vergleiche möglich

### NULL
NULL oder ⊥

Prüfung auf NULL:
X IS NULL

Vergleiche mit NULL => Unknown