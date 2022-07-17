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


## Divide and Conquer