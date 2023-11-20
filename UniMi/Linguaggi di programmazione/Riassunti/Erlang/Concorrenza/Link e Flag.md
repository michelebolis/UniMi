Quando i due attori sono collegati, gli errori di uno affetta il comportamento dell'altro

`link(PID)` function aiuta a monitorare un attore attraverso lo scambio di messaggio
SE A è linkato a B, quando B muori, viene mandato un messaggio di uscita `{'EXIT', PID}`
SE abbiamo piu processi linkati, abbiamo un link set

I segnali di uscita sono generati da un processo che muore e sono mandati in broadcast a tutti i processi linkati
Il segnale di uscita può essere esplicitato con `exit(PID, X)`

es
```Erlang
-module(dies). 
-export([on_exit/2]). 
on_exit(Pid, Fun) -> 
	spawn(fun() -> 
		process_flag(trap_exit, true), 
		link(Pid), 
		receive {'EXIT', Pid, Why} -> Fun(Why) end 
	end).
```

```cmd
Pid = spawn(fun() -> receive X -> list_to_atom(X) end end).
dies:on_exit(Pid, fun(Why) -> io:format("~p died with:~p~n",[Pid, Why]) end).
```

`process_flag(trap.exit, true)`
Permette di flaggare il processo come di sistema, consentendolo di non morire quando riceve l'exit del processo a cui è linkato