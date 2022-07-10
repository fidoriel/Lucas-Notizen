## Constraints
### Schlüssel, ID oder PRIMARY KEY
- Ein oder mehrere Attribute, Verpflichtend für Entityp
- Minimale Menge von Attributen eines Tupels => keine zwei 
- Eindeutig fpr Indentifikation
- Einmalig
- Bei [[Relationaler Entwurf#IST|IST]]-Beziehungen muss die Wurzel-Superklasse sämtliche
Schlüsselattribute enthalten
- Bei [[Relationaler Entwurf#ER|ER]] Unterstreichen

##### Kapazitätserhöhende Schlüssel
![[Kapazitätserhöhung.png]]
##### Kapazitätsvermindernde Abbildung
![[Kapazitätsvermindernd.png]]
### Referentielle Integrität
- Alle durch z.B. Fremdschlüssel referenzierten Entitäten Existieren
- Das Tupel, welches dem PK des FK enthält darf erst gelöscht werden wenn alle FKs weg sind

### Assertions
- Nebenbedinung für für Insertions
	- z.B. Arbeitnehmer muss >= 10.000€ verdienen

### Domänen
> Wertebreiche
- Mengen $A_1, A_2,...A_n$
	- Datentypen z.B. $Bool, String, Integer$

### Tupel
- $(a_1, a_2,...a_n)$ => Daten
	- $True, Naumann, 42$
> Zeilen einer Tabelle

### Relation
- Einfache Tabellendarstellung
- Für Entities und Relationships
- Besteht aus Attributen und Tupeln

### Attibute
> Spaltenüberschrift
- Attibutwerte sind Atomar, z.B. Hausnummer, nicht Adresse

### Datenbankschema
> Besteht aus einem oder mehreren Relationenschemata

### Relationenschemata
> Name der Relation sowie Liste der Attribute mit Domäne