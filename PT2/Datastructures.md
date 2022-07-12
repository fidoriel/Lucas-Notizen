## Datastructures
- [[OOP|Kapselung]]
- Keine Offenlegung der Implementierung (Opaque Type)
- Abstraktion: Definition der Schnittstelle (Interface)
- Festlegung der Menge in einer Algebra => Signaturen, Konstruktoren und Axiome
- Modularisierung: Wiederverwendbar
- Integrität: erprobt, bewährt effizient
- Information Hiding: Implementierungsdetails versteckt => Getrennte Weiterentsicklung

In C++:
```
- Dynamic Array (std::vector<T>)
• Static Array (std::array<T,N>)
• Stack (std::stack<T>)
• Queue (std::queue<T>)
• Double-Ended Queue (std::deque<T>)
• Priority Queue (std::priority_queue<T>)
• Single-Linked List (std::forward_list<T>)
• Double-Linked List (std::list<T>)

Assoziative Container
• Key-Sorted Associative Map of Unique Key-Value Pairs (std::map<K, T>)
• Key-Sorted Associative Map of Key-Value Pairs (std::multimap<K, T>)
• Key-Sorted Collection of Unique Keys (std::set<K>)
• Key-Sorted Collection of Keys (std::multiset<K>)
• Unordered Associative Map of Unique Key-Value Pairs (std::unordered_map<K, T>)
• Unordered Associative Map of Key-Value Pairs (std::unordered_multimap<K, T>)
• Unordered Collection of Unique Keys (std::unordered_set<K>)
• Unordered Collection of Keys (std::unordered_multiset<K>)
```

### Stack
- Last in => first out (LiFo)
- Push => hinzufügen
- Pop => letztes Lesen und Entfernen
![[Stack.png]]

### Queue
- First in => First out (FiFo)
![[Queue.png]]

#### Deque
- Elemente können von beiden Seiten effizient hinzugefügt (push_front, push_back) und entfernt(pop_front, pop_back) werden
- belibiges insert und erase
![[Deque.png]]

#### Piority Queue
- Elemente werden durch Prisorität einsortiert
- push fügt hinzu und sortiert
- pop entfernt Element mit höchster Priorität in Kkonstanter Zeit

### Linked List
#### Single
- Struct mit Pointer auf nächsten Struct
- Letztes Struct zeigt auf NULL
- Hinzufügen unt entfernen überall möglich
	- worst case Laufzeit $O(1)$ weil durchiterieren
![[SingleLinkedList.png]]

#### Double
- Laufen in beide Richtungen möglich
	- Aufwand zum einfügen geringer als bei SingleLinkedList
![[DoubleLinkedList.png]]

### Map
- Schlüssel Wert Paare
- Zugriff über Schlüssel
- $O(log n)$
- [[Trees#Traversierung|Traversierung]] in sortierter Reihenfolge

#### Unordered Map
- Schlüssel intern über Hash Table in Buckets
- Keine Sortierte Traversierung
- Schneller als [[#Map]] jedoch mehr Speicher

### Set
- Speichert Schlüssel
- enthalten oder nicht enthalten
- $O(log𝑛)$

### Dynamisches Array
- => vector
- 