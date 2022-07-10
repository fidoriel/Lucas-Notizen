##### Ziel
Entwurf wichtig, da mehrere Jahre in Verwendung
Keine redundaten Daten speichern

## Ablauf
### Anforderungsanalyse =>Informale Beschreibung
- Sammlung des Informationsbedarfs in Fachabteilungen
- Formale Beschreibung erstellen
- Trennen der Information über Daten (Datenanalyse) von den Information über Funktionen (Funktionsanalyse)

### Konzeptioneller Entwurf => Entity-Relationship-Diagram
- ER-Modell erstellen
- Modellierung von Sichten
- Konflikte erkennen
	- Synonyme, Homonyme
	- Bedingungskonflikte
	- Strukturkonflikte
	- Typkonflikte

### Verteilungsentwurf => Partitionierung
- Verteilung der Daten auf Server
	- Verschiedene Abteilungen mit verschiedenen Standorten?

### Logischer Entwurf => Relationenschemata
- Relationales Modell erstellen
- Normalisierung

### Datendefinition => SQL DDL
Erstellen von `CREATE TABLE` oder `CREATE VIEW`

### Physischer Entwurf => Parameter und Indizes
Erstellen von `CREATE INDEX` 

### Implementierung und Wartung => Installationen, Backups
=> Anpassung an Anforderungen
=> Tuning
=> Portierung

## ER
![[ER.png]]
![[ER2.png]]

### IST
- Subklassen fügen weitere Attribute hinzu
- Akzeptieren keine Mehrfachvererbung
![[ER_Subklassen.png]]

###  Kardinalitäten nach Naumann
Pfeil zeigt immer auf Entität
Pfeil mit Ausgefüllter Spitze: 0...1
kein Pfeil: m...n
Pfeil offen: genau 1

### Schwache Entität
- Kann nicht alleine durch PK identifiziert werden
- Benötigen FK zur identifikation => alle Attribute des PK, der starken Entität
- Alle, die Schwache Entität referenzieren brauchen alle Attribute des PK, also PK, der Starken Entität


