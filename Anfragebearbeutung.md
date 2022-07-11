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

Phantom Read => Neue Tupel aber bei Read nicht erfasst
Non-Repetable Reads =>$T_1$ grteift auf Wert zu, der aber währen er $T_2$ verändert worden ist, ergo zwei verschiedene Werte

Schedule
Ablaufplan bestehend aus einer Reihe von Transaktionen

Serieller Schedule
Schedule in dem Transaktionen vollständig hintereinander Ausgeführt werden.