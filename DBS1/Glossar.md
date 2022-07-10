## Constraints
### Schlüssel, ID oder PRIMARY KEY
- Ein oder mehrere Attribute, Verpflichtend für Entityp
- Minimale Menge von Attributen eines Tupels => keine zwei 
- Eindeutig fpr Indentifikation
- Einmalig
- Bei [[Relationaler Entwurf#IST|IST]]-Beziehungen muss die Wurzel-Superklasse sämtliche
Schlüsselattribute enthalten
- Bei [[Relationaler Entwurf#ER|ER]] Unterstreichen

### Referentielle Integrität
- Alle durch z.B. Fremdschlüssel referenzierten Entitäten Existieren
- Das Tupel, welches dem PK des FK enthält darf erst gelöscht werden wenn alle FKs weg sind

### Assertions
- Nebenbedinung für für Insertions
	- z.B. Arbeitnehmer muss >= 10.000€ verdienen