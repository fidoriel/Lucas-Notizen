# EBNF
Grammatik
wie Regex
lvalue zu definierender Ausdruck
rvalue Definition
```
<hexchar>::= ( [0-9] | [a-f] | [A-F] )
<hex8bit>::= <hexchar> <hexchar>
<hex24rgb>::= "#" <hex8bit> <hex8bit> <hex8bit>
```

![[EBNF.png]]

## Loop
terminiert immer
Loop berechenbar falls als Loop formulierbar

## While
terminiert nicht immer => dynamisch Geprüft

$LOOP\subset WHILE$

## GOTO
terminieren nicht immer
$GOTO == WHILE$
