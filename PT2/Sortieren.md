# Sortieren
## Begriffe
- Interne Sortierverfahren: In Hauptspeicherstrukturen (Felder, Listen)
- Externe Sortierverfahren: Datensätze auf externen Medien (Festplatte, „Magnetband“)
• Stabilität: Relative Reihenfolge nach erster Sortierung Bleibt erhalten erst Name dann Alter
- Inplace?

## Insertionsort
=> Stabil
- Element aus altem Array in neues an richtiger Position
$O(n^2)$
```
for element in old:
	suche Position
	alle nachfolgenden Elemente um 1 nach rechts
	element einfügen
```

## Shellsort
=> Nicht Stabil
Zerlegung in kleine Teillisten => sortieren mit [[#Insertionsort]]
$O$ ist etwas Schwierig => kommt auf daten an
Mit Sprungweite $h$
```
Sortieren von 2, 5, 3, 4, 3, 9, 3, 2, 5, 4, 1, 3

In Spalten mit Sprungweite h = 4 => Vertical Sortieren
2 5 3 4        2 4 1 2
3 9 3 2  →     3 5 3 3
5 4 1 3        5 9 3 4

Spalten mit Sprungweite h = 2
2 4         1 2
1 2         2 3
3 5   →     3 4
3 3         3 4
5 9         3 5
3 4         5 9

Normales Insertionsort bei H h = 1
1 2 2 3 3 4 3 4 3 5 5 9  →   1 2 2 3 3 3 3 4 4 5 5 9
```

## Selectionsort
=> Stabil
```
größtes Element suchen und mit letzter Stelle tauschen; bis Stelle n-1 wiederholen
```

## Bubblesort
=> Stabil
$O(n^2)$ ohne Optimierungen
```
for (int x = len-1; x>0; --x)
	for (int i = 0; i<x; i++)
		if ary[i] > ary[i+1]
			swap ary[i] ary[i+1]
			swapped = true
		if swapped == false => break // fertig sortiert => optimierung
```

Optimierung 2:
swapped könnte durch letztes zu tauschendes Element $(i+1)$ sortiert werden da $[i+1,end]$ bereits sortiert
$O(\frac{n^2}{2})$

## Mergesort
=> Stabil
$O(n\cdot log(n))$
[[algo#Divide and Conquer]]
- Rekursives Teilen der Listen und 2, Bzw. Einelementige Listen sortieren => diese Weitersortieren
![[Mergesort.png]]
```
vector<T> merge_sort(vector<T>& A) {
	int N = A.size();
	
	// ein-elementig Liste sind (trivialerweise) sortiert
	if(N==1) return A;
	
	// halbieren der Liste 
	int m = N/2;
	vector<T> A_L = left_part(A, m);
	vector<T> A_R = right_part(A, m);
	
	// recursives Sortieren der Teillisten
	vector<T> sorted_A_L = merge_sort(A_L);
	vector<T> sorted_A_R = merge_sort(A_R);
	
	// merge of resulting lists
	vector<T> merged_A = // merge(sorted_A_L, sorted_A_R);
						[](vector<T> sorted_A_L, vector<T> sorted_A_R)
						{
							vector<T> sorted;
							// sortieren der Listen
							while(sorted_A_L.size()>0 && sorted_A_R.size()>0)
							{
								if(sorted_A_L[0] < sorted_A_R[0])
								{
									sorted.push_back(sorted_A_L[0]);
									sorted_A_L.erase(sorted_A_L.begin());
								}
								else
								{
									sorted.push_back(sorted_A_R[0]);
									sorted_A_L.erase(sorted_A_R.begin());
								}
							}
						// da nur bis zum Ende der kurzen Liste
						// Sortiert lane anhängen
						if(sorted_A_R.empty() == false)
						{
							sorted += sorted_A_R
						}
						
						if(sorted_A_L.empty() == false)
						{
							sorted += sorted_A_L
						}
						
						return sorted;
						}
	
	return merged_A;
}
```

## Quicksort
=> nicht Stabil
$O(2𝑛 log2 𝑛)$
Teilen der Liste in zwei durch Pivot, rekursiv tauschen bis fertig r = 0 < 0 = l
```
 func quicksort(links, rechts)
     if links < rechts
	     pivot = mittig_von(links, rechts)
         quicksort(links, pivot - 1)
         quicksort(pivot + 1, rechts)
     ende
 ende
```