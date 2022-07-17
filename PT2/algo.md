## Median
=> Sortieren und `ary[ary.size()]`

##### Median der Mediane
1. gesuchtM = `ary.size()/2` => Stelle im sortierten Array
2. Array in 5er Pakete
3. Pakete Sortieren
4. 3. Element ist Median
5. Median der Mediane nehmen
6. Elemente ``Einsortieren L < Median der Mediane < R``
7. Wenn ``L.size+1 == gesuchtM`` return Median der Mediane
8. Wenn ``gesuchtM <= L.size()`` => rekursiv mit L aufrufen
9. sonst rekursiv mit R aufrufen

## Greedy
- Heuristische Strategie => bei jedem Schritt sich dem lokalen optimum Annähern
- nächster Schritt immer näher an der Lösung => wahl des Größten gewinns
- Approximiert Lösung halbwegs muss aber nicht globales Maximum sein => kann auch schlecht sein
- geht nie zurück

### Funktionen benötigt bei Greedy
• Kandidatenmengen
• Auswahlfunktion => bestn Kandidaten
• Zulässigkeitsfunktion => Kandidat nützlich
• Bewertungsfunktion => Qualität der Lösung
• Lösungsfunktion => Fertig?
- Für Matroid-Probleme
- BSP: Coin Change

### Minimal Spaning Tree Prim
Gewichtete biderektionaler Graph
```
bk = {} // Menge der Besuchten Knoten
Zufällig Wurzelknoten => bk.push_back(Knoten)
Alle Kanten die von einem Knoten bk ausgehen (außer zu sich selbst)
Mit geingstem Gewicht zu bk hinzufügen

```

### Greedy Scheduling
Möglichst viele verschiedene Events => bestes Earliest FInith Time
```
passend: Ende Letzte <= Anfang neue => Interval mir kleinster Schlusszeit
```

## Divide and Conquer
Teilprobleme rekursiv Lösen
Top Down
[[Sortieren#Mergesort|Mergesort]]
##### Hanoi
```
void ToH(int n, int a, int b, int c)
{
if(n == 1)
	// move disc from a directly to c (no auxiliary stack required)
	std::cout << "Move " << (char)('A' + a) << "->" << (char)('A' + c)<<std::endl;
else
{
	ToH(n-1, a, c, b); // move n-1 stack of a to stack b
	ToH(1, a, b, c);
	// move remaining disc of a to c
	ToH(n-1, b, a, c); // move n-1 stack b to stack c
}
```


## Backtracing
- Tiefensuche
```
def backtracing(x):
	if gelöst(x):
		return false
	elif isLösung(x):
		print(x)
		return true
	else:
		s = möglicheLösung(x)
		while (s):
			if backtracing(s):
				return true
			s = nextMöglichLösung(s)
```

```
def reverse(x):
    if x:
	    y = x[0]
        reverse(x[1:])
	    print(y)

# wort invertieren
reverse("Nebel")
```

## Dynamic Programming
Bottom UP <=> Top Down [[#Backtracing]]
- Optimierungsprobleme
- Optimale Lösungen der Kleinsten Teilprobleme
- Zusammengesetzt

#### Rucksack
Gewicht, Value auf gegebene Capacity => Möglichst viel Value Mitnehmen
0-1 Genau ein mal oder kein Mal

nach $\frac{benefit(value)}{weight}$ abstiegend sortieren

Tabelle Füllen:
wenn zu füllende Kapazität < aktuelles Reihengewicht => Gewicht der vorherigen Reihe der Selben spalte
![[Knapsack 2.png]]
![[Knapsack.png]]

