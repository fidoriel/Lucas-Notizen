# EBNF
Grammatik
```
<hexchar>::= ( [0-9] | [a-f] | [A-F] )
<hex8bit>::= <hexchar> <hexchar>
<hex24rgb>::= "#" <hex8bit> <hex8bit> <hex8bit>
```

![[EBNF.png]]