## Syntax
**SQL IST NICHT CASE SENSITIVE und endet mit ;**

`SELECT` relation.spaltenname
`FROM` relation
`WHERE` spaltenname Vergleichsoperator 'String'
Relationsname bei uneindeutigen Attributnamen

##### Alias
`FROM X Y === FROM X AS Y`

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
###### Datumskonstante:
- ``DATE`` ‘YYYY-MM-DD‘
- ``DATE`` ‘1948-05-14‘

###### Zeitkonstante
- ``TIME`` ‘HH:MM:SS.S‘
- ``TIME`` ‘15:00:02.5‘

###### Timestamp
``TIMESTAMP`` ‘1948-05-14 15:00:02.5‘
Vergleiche möglich

### NULL
``NULL`` oder ⊥

Prüfung auf ``NULL``:
X ``IS NULL``

Vergleiche mit ``NULL`` => ``Unknown``
x+3 ergibt ``NULL``.
``NULL``+3 ist kein zulässiger Ausdruck.
x = 3 ergibt ``UNKNOWN``

###### Rechenregeln
``TRUE`` = 1
``FALSE`` = 0
``UNKNOWN`` = 1/2

``AND``: Minimum der beiden Werte
``OR``: Maximum der beiden Werte
``NOT``: 1 – Wert

`ÈXISTS` X falls X nicht leer 
x ``IN`` Y (kann auch ``NOT IN`` verwendet werden)
	x = ANY R: Entspricht x IN R
x > ``ALL`` R falls x > alle Werte in R

### Stortierung
``ORDER BY`` Länge ``ASC``, Titel ``DESC``;

### Join und Kreuzprodukt
```
SELECT Name
FROM Film, Manager // Kreuzprodukt
WHERE Titel = ‘Star Wars‘ // Selektionsbedingung
AND ProduzentID = ManagerID; // Joinbedingung
```

PROBLEME wenn eine Relation leer => verwendet Intersect => leere Menge
![[Joins.jpg]]

```
FROM Film CROSS JOIN spielt_in // Kreuzprodukt joint alles
FROM Schauspieler NATURAL JOIN Manager // joint auf gleichen Attributsnamen
```

### Mengenoperationen
==ALLES KLAMMERN==
- Vereinigung: ``UNION`` => wie logisches ``ODER``
- Vereinigung mit Duplication `UNION ALL`
- Schnittmenge: ``INTERSECT`` => wie logisches ``UND``
- Differenz: ``EXCEPT / MINUS`` => Multimenge: ``EXCEPT ALL``

```
(SELECT * FROM X)
mengenoperation
(SELECT * FROM Y)
```

### Subanfragen
Skalare Subanfragen geben ein Tupel mit einem Attribut zurück
```
SELECT Name
FROM Manager
WHERE ManagerID =
	( SELECT ProduzentID
	FROM Film
	WHERE Titel = ‘Star Wars‘ AND Jahr = ‘1977‘ );
```

Subanfregen in FROM nur mit alias
```
SELECT M.Name
FROM Manager M, (SELECT ProduzentID AS ID
	FROM Film, spielt_in
	WHERE Titel = FilmTitel AND
	Jahr = FilmJahrAND
	Schauspieler = ‘Harrison Ford‘) Produzent
WHERE M.ManagerID = Produzent.ID;
```

Korrelierte Subanfragen => Variablen vom äußeren Scope, ausgeführt für jedes Tupel
```
SELECT Titel, Jahr
FROM Film Alt
WHERE Jahr < ANY
	( SELECT Jahr
	FROM Film
	WHERE Titel = Alt.Titel);
```

### Selectbedingungen
`SELECT DISTINCT Attributnamen` => Teuer

#### Aggregation