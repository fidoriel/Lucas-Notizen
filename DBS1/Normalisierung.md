## Normalisierung
### Warum
- Redundante Informationen entfernen
- ABER Rekonstruktion möglich
- FDs: Funktionale Abhänigkeiten

### FDs
- Wenn zwei Tupel in der Attributmenge X über einstimmen, stimmen sie auch im Attribut y überein:
	$Titel, Jahr \rightarrow Länge$
- Aussagen über das Schema, nicht die Instanz
- Triviale FDs: $Titel, Jahr \rightarrow Jahr$
- [[Glossar#Schlüssel ID oder PRIMARY KEY|Schlüssel]]attribute bestimmen alle anderen Attribute funktional => aber auch Minimal
	- Können mehrere valide Schlüssel besitzen
		- {Titel, Jahr, SchauspName} ist ein Schlüssel und ein Superschlüssel
		- {Titel, Jahr, Länge, SchauspName} ist ein Superschlüssel aber nicht Minimal

#### Dekomposition und Vereinigung
###### Dekomposition
$A_1, A_2,...A_n \rightarrow B_1, B_2,...B_m \Rightarrow A_1, A_2,...A_n \rightarrow B_i$ für $i=1,...m$
###### Vereinigung
$A_1, A_2,...A_n \rightarrow B_i$ für $i=1...m \Rightarrow A_1, A_2,...A_n \rightarrow B_1, B_2,...B_m$ 

BSP:
$Titel, Jahr \rightarrow Länge$
$Titel, Jahr \rightarrow Typ$
$Titel, Jahr \rightarrow StudioName$
$\Leftrightarrow Titel, Jahr \rightarrow Länge, Typ, StudioName$

Mehreres ist vin Titel, Jahr abhänig. ABER:
Dekomposition funktionier nur rechts, nicht links, da evtl. linke attribute nicht eindutig Abhänig sind:

$Titel, Jahr \rightarrow Länge$
$\nRightarrow Jahr \rightarrow Länge$
$\nRightarrow Titel \rightarrow Länge$

### Hüllenbildung


