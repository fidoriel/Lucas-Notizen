**Achtung Mengen oder Multimengen?**

## Union $\cup$
[[sql#Mengenoperationen]]
- Attributmengen müssen identisch sein => Casting und Umbenennung
- Duplicate eliminierung

## Difference $-, \textbackslash$
[[sql#Mengenoperationen]]
- Attributschematagleichheit
- Keine Kommutativität

## Schnittmenge $intersection, \cap$
[[sql#Mengenoperationen]]
- Attributschematagleichheit
- Keine Kommutativität
- Relationen müssen Identisch sein
- $R \cap S = R − (R − S)$ = S − (S − R)

## Projection $\pi$
[[sql#Selectbedingungen]]
- $\pi_{Attribut1, Attribut2}(Relation)$
- Umbenennung: $\pi_{Attribut1\rightarrow Y, Attribut2}(Relation)$
- Umbenennung/Rechnung/StringConcat($||$): $\pi_{x+y\rightarrow z}(Relation)$

## Selection $\sigma$
Selektion $\neq$ ``SELECT``
[[sql#where]]
- $\sigma_{attribut >= 100}$

## Natural Join $\bowtie$
[[sql#Join und Kreuzprodukt]]
![[Natural Join.png]]


## Cheatsheet
| Name                     | Symbol            | LaTeX                            | Alternativtext |
|--------------------------|-------------------|----------------------------------|----------------|
| Selektion                | &#x03c3;          | \sigma                           | SEL            |
| Projektion               | &#x03c0;          | \pi                              | PR             |
| Vereinigung              | &cup;             | \cup                             | UNION          |
| Durchschnitt             | &cap;             | \cap                             | INTERSECTION   |
| Mengendifferenz          | &#x2212;          | -                                | -              |
| kartesisches Produkt     | &#x2715;          | \times                            | X              |
| Umbenennung (+Zuweisung) | &#x03c1; &#x2190; | \rho \leftarrow                  | RENAME         |
| Division                 | &divide;          | \div                             | DIV            |
| Join                     | &#x22c8;          | \bowtie                          | JOIN           |
| Left Outer Join          | &#x27d5;          | {\tiny \textifsym{d|&gt;&lt;|}}  | LOJOIN         |
| Right Outer Join         | &#x27d6;          | {\tiny \textifsym{|&gt;&lt;|d}}  | ROJOIN         |
| Full Outer Join          | &#x27d7;          | {\tiny \textifsym{d|&gt;&lt;|d}} | FOJOIN         |
| Left Semi Join           | &#x22c9;          | \ltimes                          | LSJOIN         |
| Right Semi Join          | &#x22ca;          | \rtimes                          | RSJOIN         |
| Und                      | &#x2227;          | \land                            | AND            |
| Oder                     | &#x2228;          | \lor                             | OR             |
| Negation                 | &not;             | \neg                             | -              |
| Gr&ouml;&szlig;er-gleich | &#x2265;          | \geq                             | &gt;=          |
| Kleiner-gleich           | &#x2264;          | \leq                             | &lt;=          |
| Ungleich                 | &#x2260;          | \neq                             | =/=            |
| &Auml;quivalenz          | &#x2261;          | \equiv                           | EQ             |
| Existenzquantor          | &#x2203;          | \exists                          | EXISTS         |
| All-Quantor              | &#x2200;          | \forall                          | FORALL         |






