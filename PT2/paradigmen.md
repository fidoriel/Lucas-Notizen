# Paradigmen
- Grundsätzliches Muster oder Denkweise für eine grundsätzliches Herangehen => Lehrmeinung oder Weltanscheuung
- Theoretische Grundlage

# Imerpativ
- Folgen von Funktionsaufrufen
- Seiteneffekte => Global Vars
- nahe Von Neumann
- Benennung, Typisierung => Deklaration/Wertzuweisung
- Zustandsfunktion => $Z:X\rightarrow W$ = Zustand: Variablenname -> Wert
- Ausdrücke Funktionsaufrufe mit Werten und Variablen
- Auswertung => Zustandsabhänig von Variablen
- Kopie-Semantik => $x=x+y$ Variable als Initialwerit bei Zustandsänderung
- Referenz-Semantik => Zustandsänderung bei Original, durch Referenz

### Anweisungskategorien
• Variablendeklaration und Initialisierung
• Funktionsdeklaration und Implementierung
• Kontrollanweisungen (if/switch, for/while/do-while/goto/return/break/continue,
throw/catch)
• Sequenzbildung (scopes, namespaces)
• Zuweisungen von Werten an Variablen (assignment operators)

#### Strukturiert
=> ohne Goto

#### Prozedural
=> in Unterprogrammen hirachisch Guppiert (=Funktionen)

#### Funktionssignatur
- Ausrufsskelett

#### Implementierung
- Scope => Ausfufe ohne Kenntnis der Implementierung aber [[#Funktionssignatur]]

#### Aufruf 
- Aufruf z.B. `main` => weitere Aufrufe => Callgraph

#### Modular
=> Prozeduren und Daten in logischen Einheiten

# Deklarativ
=> Berechnung von Werten nach erstellten Regeln
#### Logisch
- Logische aussagen Schlussfolgerungen

#### Funktional
- geschachtelten oder rekursiven Aufrufen ohne Seiteneffekte

# Objektorientiert
- Methodden und Daten => Kapselung

# Nebenläufig
=> Parallel

# Reflektiv
- Verändern eigene Struktur

# Generisch
- Wiederverwendbar