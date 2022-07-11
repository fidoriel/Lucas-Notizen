## Hashing
Körper $(K, +, *)$
Primzahlen, da sonst kein Körper
IBAN => Rolling Hash Function geht bei Ring kaputt
Normalerweise weder Injektiv, noch Bijektiv

##### Hash Key
>arithmetisch ganzzahliger Schlüssel für ein Objekt

###### Hash Function
> Schlüssel Basiert auch Charakteristischen Eigenschaften des Objekts

###### Hash Table
>Eintragen von Objekten in Datenstruktur, Nutzung des Hash Value als Index

###### Hash Collision
>der Hash Value ist nicht Unique (gibt Ausnahmen) und Zwei Objekte haben den gleichen Hash

###### Hashing
> Einfügen, Suchen und Löschen in die Hash Table => $O(log(n))$ sortieren Auswahl sehr langsam

###### Diffusion
>ähnliche Schlüssel verschiedene Hash Keys

###### Surjektiv
>Alle Hash Keys sollen aus den Schlüsseln möglich sein

###### Konfusion
>Hash Key keine Rückschlüsse auf Schlüssel

### Divisionsrestverfahren
h(k) = k mod m
m => Primzahl

###### Verfahren:
- mehrere Prim M values
- Bei k mod m Flag setzen, wenn einmal Null getroffen, nicht drin, wenn getroffen vielleicht => Hash Collosion
| 1 | 1 | 0 | 1 | 0 | 1 | 1|


### Cryptographie



