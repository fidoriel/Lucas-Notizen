Datenbank für Multi-User
### ACID Bedingung
- Atomicity: Transaktion ganz oder gar nicht
- Consistency: Datenbank vor Beginn und nach Ende in einem konsistenten Zustand => alle [[Glossar#Integritätsbedingungen|Integritätsbestimmungen]] erfüllt
- Isolation: Transaktion sollte eindruck haben dass sie die Einzige ist
	- Viele parallele Transaktionen
- Durability: Ergebnis einer Transaktion dauerhat in DB gespeichert

#### Serialisierbarkeit
BSP:
Bevor der eine Reserviert hat, wird dem anderen ein leerer Platz angezeigt => beide Reservieren

READ_UNCOMMITED
READ_COMMITED
REPETABLE_READ
SERIALIZABLE
!todo

#### Phantom Read => Neue Tupel aber bei Read nicht erfasst
Non-Repetable Reads =>$T_1$ grteift auf Wert zu, der aber währen er $T_2$ verändert worden ist, ergo zwei verschiedene Werte

#### Dirty Read
![[Dirty Read.png]]
Transaktion nicht Commited, $T_2$ hat trotzdem Werte weiterverarbeitet

### Non Repetable Read
![[NonRepetable.png]]
Daten verändern sich zwischen Reads


### Lost Update 
![[Lost Update.png]]

### Ablauf

```
START TRABSACTION

// alles was ACID Bedingung erfüllen soll
// Zusammenfassen in einen logischen Block

COMMIT // wenn OK
ROLLBACK oder ABORT // wenn Problem
```

Abweichungen von ACID können angegeben werden => speed
`read uncommited` => Zugriff auf nicht freigegebene Daten (`read only/read write`)
`read committed` => nur geschriebene Werte => [[#Non Repetable Read]]
`repetable read` => [[#Phantom Read Neue Tupel aber bei Read nicht erfasst|phantom read]]
`serializable` => default nur zu beginn der Transaktion commites sind und waren + eigene änderungen
![[Isolationsebenen.png]]

#### Schedule
Ablaufplan bestehend aus einer Reihe von Transaktionen

#### Serieller Schedule
Schedule in dem Transaktionen vollständig hintereinander Ausgeführt werden.

#### Serialisirbarer Schedule
[[#Serieller Schedule]] dessen Effekt identisch zu einem belibigen anderen [[#Serieller Schedule]] ist

#### Konfliktäquivivalenter Schedule
Zwei schedules bei denne die Reihenfolge aller konfliktgierender Aktion gleich ist.

#### Konfliktserialisierbarer Schedule
Schedule , der konfliktäquivivalent zu einem seriellen schedule ist. 

### Legal
wenn Gesperrtes objekt nicht erneut gesperrt ist.

### 2 Phase Locking
Alle Sperren einer Transaktion erfolgen vor der ersten Freigabe einer Sperre; es ermöglicht Konfliktserialisierbarkeit

#### Deadlock
- Serialiserer erkennt und mach rollback

### Optimistisches, Pessimistisches Unlocking
##### Optimistisch
- nach der letzten Operation
- gute Performance
- Anomalien bei Rollback
	- Weil schon weitergearbeitet wurde

#### Pessimistisch
- Unlock nach commit
	- Keine Anomalien

### Konfliktgraph
$T_2$ liest alten Wert deswegen $T_2$->$T_1$
Wenn Zyklenfrei([[Trees]]) => Konfliktserialisierbar

### Parse Baum
- Vorne mit root Anfangen
- jeden Operator in Teilbäume

- Gewicht an Vertices anhängen
	- Kosten nach oben Ausrechnen