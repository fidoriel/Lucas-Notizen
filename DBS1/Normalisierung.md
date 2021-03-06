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
=> Bewahrung der Wiederherstellbarkeit der Daten
=> Bewahrung der FDs
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
Hülle von {A}
So lange FDs rekursiv der Hülle hinzufügen, bis nix mehr geht
**Beachtung der Transitivität**

Suchen nach einem Element, dass von nichts FD ist.
![[Huelle.png]]

#### Minimalen Schlüssel suchen
![[MinimalKey1.png]]
![[MinimalKey2.png]]

#### Amstrong Axiome
###### R1 Reflexivität
$$X\supseteq Y \Rightarrow X \rightarrow Y$$
###### R2 Akkumulation
$${X \rightarrow Y} \Rightarrow XZ \rightarrow YZ$$
###### R3 Transitivität
$${X \rightarrow Y, Y \rightarrow Z} \Rightarrow X \rightarrow Z$$
###### R4 Dekomposition
$${X\rightarrow YZ} \Rightarrow X\rightarrow Y$$
###### R5 Vereinigung
$${X \rightarrow Y, X \rightarrow Z} \Rightarrow X \rightarrow YZ$$
###### R6 Pseudotransitivität
$${X \rightarrow Y, WY \rightarrow Z} \Rightarrow WX\rightarrow Z$$

## Boyce Codd Normalform (BCNF)
In a Nutshell:
-   Die linke Seite jeder gültigen, nicht-trivialen FD muss ein Superschlüssel sein.

### 1NF
Atomare Werte => Adresse Teilen

### 2NF
Keine Abhänigkeiten vom Teil eines Schlüssels
![[2NF.png]]

### 3NF
keine Transitiven Abhänigkeiten
![[3NF.png]]

### 3NF und BCNF
Keine transitiven Anhänigkeiten innerhalb eines Schlüssels
