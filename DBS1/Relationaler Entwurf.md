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

## ER Umwandlung
- Relationen: Attribute und FKs hinzufügen, PK unterstreichen
- Kapazität beachten: [[Glossar#Kapazitätserhöhende Schlüssel|Kapazitätserhöhende Schlüssel]] sowie [[Glossar#Kapazitätsvermindernde Abbildung|Kapazitätsvermindernse Abbildung]]
- Bei Doppelnamen von Attributen oder Relationen: Umbenennung
- Falls meherere [[Relationaler Entwurf#IST]]: PK mehrfach übernehmen => Umbenennung

### Zusammenlegen
- Prüfung von Zusammenlegbaren Entitäten bzw. Relationen
![[Zusammenlegen.png]]
bei 1:n, die eins an n anhängen => film(__titel__, __jahr__,...,besitzendes_studio)
bei 1:1 direkte Aufteilung
bei m:n ==nicht möglich==

### IST-Umwandlung
#### Nullwerte
- alle nicht benötigten Attribute


## ER Syntax
![[ER.png]]
![[ER2.png]]

### IST Spezialisierung
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

![[SchwacheEntität.png]]


