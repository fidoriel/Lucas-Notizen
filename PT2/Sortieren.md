# Sortieren
## Begriffe
- Interne Sortierverfahren: In Hauptspeicherstrukturen (Felder, Listen)
- Externe Sortierverfahren: Datensätze auf externen Medien (Festplatte, „Magnetband“)
• Stabilität: Relative Reihenfolge nach erster Sortierung Bleibt erhalten erst Name dann Alter
- Inplace?

## Insertionsort
- Element aus altem Array in neues an richtiger Position
```
for element in old:
	suche Position
	alle nachfolgenden Elemente um 1 nach rechts
	element einfügen
```

## Shellsort
Zerlegung in kleine Teillisten => sortieren mit [[#Insertionsort]]
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
```
größtes Element suchen und mit letzter Stelle tauschen; bis Stelle n-1 wiederholen
```

## Bubblesort
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

## Mergesort
$O(n\cdot log(n))$
[[algo#Divide and Conquer]]

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
							
						}
	
	return merged_A;
}
```