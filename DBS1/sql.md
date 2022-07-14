## Querieng
**SQL IST NICHT CASE SENSITIVE und endet mit ;**

`SELECT` relation.spaltenname
`FROM` relation
`WHERE` spaltenname Vergleichsoperator 'String'
Relationsname bei uneindeutigen Attributnamen

###### Lesereihenfolge
6. SELECT
1. FROM
2. WHERE
3. GROUP BY
4. HAVING
5. ORDER BY

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
`SUM, AVG, MIN, MAX, COUNT, VAR, STDDEV`
`SELECT COUNT(DISTINCT Schauspieler) AS Count_Schauspieler FROM spielt_in`
``NULL`` wird Ignoriert

### Grouping
```
SELECT StudioName, SUM(Länge)
FROM Film
GROUP BY StudioName
```
==Nicht aggregierte SELECT Attribute müssen bei GROUP BY erscheinen==

#### HAVING
==BENÖTIGT GROUP BY==
```
SELECT Name
FROM Manager, Film
WHERE ManagerID = ProduzentID
GROUP BY Name
HAVING SUM(Länge) > 1000
```
HAVING Aggregation bezieht sich auf aktuelle Gruppe
Nur Gruppierungsattribute dürfen un-aggregiert in HAVING Klausel erscheinen
(wie bei SELECT-Klausel)

## Insertion/Creation

### Insert
```
INSERT INTO spielt_in(FilmTitel, FilmJahr, Schauspieler)
VALUES (‘Star Wars‘, 1977, ‘Alec Guinness‘);
```
Attibutliste weglassen wenn alle Atribbute gesetzt
alle nichtgesetzten Attribute => ``NULL``

Erst GESAMTE Anfrage ausführen
```
INSERT INTO Studio(Name)
SELECT DISTINCT StudioName
FROM Film
WHERE StudioName NOT IN
	(SELECT Name
	FROM Studio);
```
### Löschen
`DELETE FROM R WHERE`
### Update
`UPDATE R SET Name = 'Felix' WHERE …`

## Datatypes
- CHAR(n) => fixe Zeichenlänge
- VARCHAR(n) => variabel max n Zeichen
- BIT(n) => Wie char aber Bits
- BOOLEAN => UNKNOWN = TRUE
- INT/INTEGER/SHORTINT => 8 bzw. 4 Byte
- FLOAT/REAL
- DECIMAL(n,d) => DECIMAL(7,2) – 7 Stellen, davon 2 Nachkommastellen
- CLOB => Character Large Object
- BLOB => Binary Large Object
- DATE

###### Casting
`CAST(i AS VARCHAR)`

## Tabellen
`CREATE TABLE X(X BOOLEAN, Y VARCHAR(10) DEFAULT 'abc', Datum DATE);`
`DROP TABLE X;`

##### Verändern
`ALTER TABLE Schauspieler DROP Geburtstag;`
`ALTER TABLE Schauspieler ADD Telefon CHAR(6);`
`ALTER TABLE Schauspieler MODIFY Telefon CHAR(10);`

#### Optionen
```
PRIMARY KEY
UNIQUE
FOREIGN KEY … REFERENCES …
NOT NULL
CHECK
CREATE ASSERTION
CREATE TRIGGER

=> `CREATE TABLE X(ID INTEGER PRIMARY KEY, X BOOLEAN, Y VARCHAR(10) DEFAULT 'abc', Datum DATE);`
```

## Indices
Andere Datenstruktur => Beschläunigung
```
CREATE INDEX JahrStudioIndex
ON Film(Jahr, Studioname); // Reihenfolge wichtig für Baum

DROP INDEX JahrIndex;
```
Indexwahl gut überlegt? Speicherbedarf

Anfrage          | Kein Index | SchauspielerIndex | Filmindex | Beide Indizes
---------------- | ---------- | ----------------- | --------- | --------------
Schauspieler = s | 10 | 4 | 10 | 4
FilmTitel = t AND FilmJahr = j | 10 | 10 | 4 | 4
INSERT INTO spielt_in | 2 | 4 | 4 | 6
Gesamtkosten | 2+8p1+8p2 | 4+6p2 | 4+6p1 | 6-2p1-2p2
p1: Anteil Anfrage 1
p2: Anteil Anfrage 2
1‒p1‒p2: Anteil Anfrage 3
!todo

## Sichten
Nutzer sollen nicht Merken, dass sie auf einer Sicht sind
Inertions? => Manchmal OK => verstößt gegen sicht?
```
CREATE VIEW ParamountFilme AS
SELECT Titel, Jahr, Zahl 16
FROM Film
WHERE StudioName = ‘Paramount‘; // SFW BLOCK ist die Bedingung der Sicht, die Query
```
Mehere Tabellen in einer Sicht

Umbenennung der Attribute
```
CREATE VIEW FilmeProduzenten(FilmTitel, Produzentenname) AS
SELECT Titel, Name
FROM
Film, Manager
WHERE ProduzentID = ManagerID;
```

### Update => SFW Block
- Kein JOIN, Mengenoperationen => Welchen Teil der Sicht
- kein DISTINCT => welches Tupel
- keine Aggregatfunktion im Select => kann nicht geändert werden
- GROUP BY und HAVING verboten
- FROM nur eine Relation => sonst Änderung Unklar
- keine JOINs

#### Tupelmigration
- Bei Tupeländerung verstößt geändertes Tupel gegen VIEW Bedinung => es ist nicht mehr
- sichtbar. `WHERE X = 10` aber x auf 11 geändert
- Verhindern mit `WITH CHECK OPTION;`

### Materialisierte Sicht
- Berechnete Werte, z.B. Bilanz in View => gespeichert
- wann Updaten
- Joins und Agggregate schwierig

#### Local-As-View
Abbilden verschiedener Datenquellen auf eine View