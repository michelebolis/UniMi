- Tupla
Non posso aggiungere elementi: numero fissato di oggetti

```erlang
{}. %tupla vuota
{123, "walter", cazzola}. %tupla con cazzola un atomo
```

Possono subire un pattern matching strutturale
```erlang
{{1, 2}, 3} == {1, {2, 3}}. %false perche non hanno la stessa struttura
```



- Lista 
Usate per conservare un numero variabile di oggetti, infatti hanno una dimensione dinamica

```erlang
[]. %lista vuota
[1 | [2]]. %lista [1, 2]
length([{1, 2}, ok, []]). %3
A = [$a, $b], B = [$b, $c].
A ++ "" ++ B. % ++ operatore di concatenazione tra liste. Ris: "abbc"
A -- B. % -- operatore di sottrazione tra liste. Ris: "ac"
```

```erlang
[B | L] = [a, b, c].
{X, X} = {B, B}. % Ris: {a, a}
{A1, _, [B1|_], {B1}} = {abc, 23, [22,x], {22}}.
```

B sarà la testa della lista mentre L sarà il resto della lista
Quello che non considero nel pattern matching lo rappresenterò con \_

