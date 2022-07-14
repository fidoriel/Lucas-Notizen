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
=> Generische Speicherung in Graphstruktur
![[XML_Relational.png]]
Wiederherstellbar durch[[Trees#Traversierung]] mit [[Trees#Tiefensuche depth first search DFS]]  => öffnen und Schließen

#### Strukturbasiert
=> Ableiten des Datenschemas
- Daten verständlich

#### Textbasiert
=> Plaintext