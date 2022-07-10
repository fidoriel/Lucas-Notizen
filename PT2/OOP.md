## OOP
- Kapselung
- Methodik:
	- [[#Analyse]]
	- [[#Desing]]
	- [[#Programmierung]]

- Konzepte:
	- Kapselung
	- Klassen
	- Polymorphie
	- Vererbung

### Analyse
- Objektmodell
- Relationen
- Klassen
=> UML

### Desing
- Softwarearchitketur
- Vorlage für Implementierung

### Programmierung
- Implenentierung

#### Konzeptbestandteile
- Instanz: Objekt mit Werten => erstellung in runtime
- Entität: Ausprägung der Anwendungsdomäne => [[Glossar#Domänen]]
• Identität: eindeutige, eigenständige unverwechselbare Einheit/Instanz
• Zustand: Attribute repräsentieren den Zustand
• Verhalten: Methoden
• Klasse: Objekt => Atribute, Typen und Methoden
• Schnittstelle: rpivate, public, protected
• Kapselung: nur Public Sichtbar nach außen
• Konstruktor: Initialisierungfunktion
• Destruktion: Zerstört Objekt und räumt auf

#### Kategorien
##### Elementare Klassen
- Eingebaute Datentypen
- z.B. Rationale Zahlen, HashKeys

##### Container-Klassen
- generisch
- Datentypen (Liste, Vector)

##### Anwendungsklassen
- Datenmodell des Entwicklers für die Domäne
- Kunde, Rechntung etc.

##### Wann?
- gleichartige datenstrukturen
- nichttriviale Daten
- nichttriviale Funktionalität
- Daten und Funktionen hängen zusammen
- Objektidentität => Zugriff auf Datenmenge

#### Allgemeines
- Typ = Klasse
- Mathoden können Attribute verändern
- Kapselung
- während runtime initialisiert
- Methoden = Verhalten, Funktionalität
- Klassenname = Typname des Objekts
- Nichtstatische Attribute => Variablen
- Nichtstatische Methoden => Funktionen
- Statische Attribute => Globale vars
- Statische Methoden => objektunabhänige Funktionen im Namensraum