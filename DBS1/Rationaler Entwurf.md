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

