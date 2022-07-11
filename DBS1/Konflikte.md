### ACID Bedingung
- Atomicity: Transaktion ganz oder gar nicht
- Consistency: Datenbank vor Beginn und nach Ende in einem konsistenten Zustand !todo
- Isolation: Transaktion sollte eindruck haben dass sie die EInzige ist
	- Viele parallele Transaktionen
- Durability: Ergebnis einer Transaktiondauerhat in DB

READ_UNCOMMITED
READ_COMMITED
REPETABLE_READ
SERIALIZABLE
!todo

#### Phantom Read => Neue Tupel aber bei Read nicht erfasst
Non-Repetable Reads =>$T_1$ grteift auf Wert zu, der aber währen er $T_2$ verändert worden ist, ergo zwei verschiedene Werte

#### Schedule
Ablaufplan bestehend aus einer Reihe von Transaktionen

#### Serieller Schedule
Schedule in dem Transaktionen vollständig hintereinander Ausgeführt werden.

#### Serialisirbarer Schedule
Schedule dessen Effekt identisch zu einem belibigen anderen schedule ist

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