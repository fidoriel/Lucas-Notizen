## Programmierung/Schemata
LEI schema jede Entität in eine Zeile einer CSV
=> Geschachteltes XML

XML Bringt eigenes schema mit
Leere Daten ```<></>``` oder einfach weglassen

Mixed Content ist schwig, unstrukturierte Daten (Text)
Semistrukturiert => unwichtiges einfach weglassen

SAX Simple API for XML
- Ruft Callback auf wenn Tag gelesen

Document Object Model [[Trees|Tree]] Pasrsing

### Probleme
- keine Referentielle Intregrität
keine PKs, FKs

- bei Schachtelung
	=> keine m:n Beziehung => Nutzung von IDs 
	
### DTD
```
<!-- xyz DTD -->
<!ATTLIST x (y? z)>
<!ELEMENT y (#PCDATA)>
<!ELEMENT z CDATA #REQUIRED>
```

### XML Schema
.xsd
```
<xs:complexType name="X">
	<xs:sequence>
		<xs:choice>
			<xs:element ref="Y"
			<xs:element ref="Z"
		</xs:choice>
	</xs:sequence>
	<xselement ref="A"
</xs:complexType>
```

## Anfage
### XPath
![[XPath.png]]

![[XPathSyntax.png]]
![[XPathFunctions.png]]
**BSP**
```/bookstore/book[author/name='Plato']``` mit Pfadangabe
```//author[first-name='Herman']/last-name``` Bedingung beeinflusst Navigation


### XQuery
![[XQuery.png]]
XQueryX übersetzt XQuery in XML => Automatisch, nichtmehr einfach von Menschen erstellbar

## Kombinierung mit Relationalen Datenbanken
=> Neuer Datentyp XML
-  Werte in Spalte => String
- Normale Tabelle mit XML => [[#XQuery]] 

### Relational => XML
- XMLGEN => Generiert XML von Query
- XMLELEMENT => Erzeugt XML Element aus Werteliste
- XMLFORREST
- XMLCONCAT => Wald zusammenfügen
- XMLAGG => Aggregieren

### Anfragen an 
XML => Relationale Modell

#### Modellbasiert
##### Variante 1
=> Generische Speicherung in Graphstruktur
![[XML_Relational.png]]
Wiederherstellbar durch[[Trees#Traversierung]] mit [[Trees#Tiefensuche depth first search DFS]]  => öffnen und Schließen

Probleme mit Mixed Content:
```
<x>
	Text
	<y>
		Texty
	</y>
</x>
```

### Anfragen
XQuery => SQL => Schemata

##### Beispiel
Self Join => DOCIDs (Datei) => 
![[Anfragen.png]]

##### Variante 2
Aufteilung des Baumes in Ebenen
![[XMLAufteilung.png]]

#### Strukturbasiert
=> Ableiten des Datenschemas aus DTD/XML
- Mensch vergibt Datentypen
- Daten verständlich
- Thoretisch exisitierende Attribute fehlen => Hinzufügen wenn bemerkt
- Dokument nicht einfach herstellbar
- 
###### Eine Relation für alles
![[XML_in_eine_relation.png]]

###### Aufteilung in Relationen
![[XML_auteilung.png]]

###### Verwendung einer Spalte
einfach ein XML Feld in einer Relation

#### Textbasiert
=> Plaintext

### Indizierung von XML
- Preorder => Rangzahl von seinen Kindern
- Postorder => Rangzahl nach seinen Kindern

![[PrePostOrder.png]]
Quadranten entsprechen XPath 
![[Quadranten.png]]
- Speicherung einer Indextabelle mit Pre und Post
- => XML wieder Rekonstruirbar
- Durch StrukturXPath Anfragen Beantwortbat
```
// Preceding/Vorgänger für Following/Nachfolger < => >
SELECT DISTINCT p.pre
FROM context C, prepost P
WHERE P.pre < C.pre
AND P.post < C.post
ORDER BY P.pre
```
![[IndexXML.png]]

#### Berechnung zum Überspringen von decending Knots
![[Berechnung_pruning.png]]
Beschläunigt, da grauen bereich Skippen
Berechnung von:
- pre(g) = post(f) + h
- post(g) = pre(f) - h
```

// Pre
WHERE v*.pre > f.pre AND v*.post < f.post

// Post
WHERE v*.pre > f.pre AND v*.pre ≤ f.post + h AND v*.post ≥ f.pre ‒ h AND v*.post < f.post
```