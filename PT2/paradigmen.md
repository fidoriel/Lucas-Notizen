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
• Sequenzbildung (scopes, namespaces) => [[cpp#Namensräume]]
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

#### Top Down
[[#Implementierung]] beginnt bei `main` und wird durch Funktionen verfeinert

#### Modular
=> Prozeduren und Daten in logischen Einheiten
- Separat Entwickelt und Debugged

#### Abstraktion
- wiederverwendbare Einheiten, die Komplexität entfernen

# Deklarativ
=> Berechnung von Werten nach erstellten Regeln
## Funktional
- System von Axiomen
- keine Datentypen
- Funktionen ohne Namen => Auswertung in/out
- Funktionsdefinition und anwendung identisch
- Reihe von Geschachtelten Funktionnsaufrufe
- keine Seiteneffkete
- Keine Globale Datenmanipulation
- List inversion mit TailRecursion
- Immer Recursion
- Lazy Evaluation => Nur benötigtes Berechnet

#### Higher-Order Functions
Funktionen als Argumente oder Rückgabewerte

#### Faltungsfunktion
Funktion als Argument mit Liste => angewand auf jedes Element

#### Reine Funktionen
Nie Seiteneffekte
Nie veränderung des Zustands
Immer gleiches Resultat bei gleichem Input

#### Monaden
Kapseln nicht rein Funktionales Zeug => IO, Zustandsbehaftete Berechnungen, Zufall

#### Funktional Vergleich
![[Wichtige Konzepte Funktional.png]]
c++ Lamdas
`[](int x){ return 42; }`

#### Logisch
Scheme, Lisp, Haskell

- Logische aussagen Schlussfolgerungen
- Menge von Axiomen
-  Deduktiver Algorithmus = Logische Aussagen + Interpretationsalgorithmus + Anfrage
- nicht wie es audgeführt wird, sondern was gilt

##### Terminologie
- Prolog

- Fakten Atomare Formeln ohne Unbestimmte
- Regeln => Aussage
- Prämisse => Schlussfolgerung
- Atomare Formeln
- Auswerten der Regeln durch Verfahren
	- Intuitiv => Einsetzen
	- nicht deterministisch => Auflösen


# Objektorientiert
- Methodden und Daten => Kapselung

# Nebenläufig
=> Parallel

# Reflektiv
- Verändern eigene Struktur

# Generisch
- Wiederverwendbar

# Genetisch
- Abstammungshypothese => Mutation, gemeinsame Vorfahren
- Allmählichkeitshypothese => kleine Mutationen
- Selektionshypothese => Natual Selection, survival of the Fittest

## Bio
Genotyp => Gene
Phänotyp => Aussehen
Population
Individuum
Generation
Chromosom
Genom
Mutation

## Verwendung
Gute Approximation
Iterative Verbesserung


## Ablauf
1. Initialisierung => Zufall
2. Fittnesfunktion  => Gut genug? Abbruch
3. Selektion => Schlechte durch Fittnesbewertung raus
4. Rekombination => Neue Individuen, Rekombination
5. Mutation => Zufall

![[Gentische Algorithmen.png]]