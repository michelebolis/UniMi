
| **`trap_exit`** | **Exit signal** | **Action**                                |
| ----------- | ----------- | ------------------------------------- |
| true        | kill        | muore e propaga                       |
| true        | qualsiasi   | aggiunge {'EXIT, PID, X'} ai messaggi |
| false       | normal      | continua (NO propagazione)            |
| false       | kill        | muore e propaga                       |
| false            | qualsiasi            | muore e propaga                                      |

Situazioni:
- NON mi interessa se un processo crasha
```Erlang
PID = spawn(fun() -> ... end).
```
- Voglio che l'errore si propaghi
```Erlang
PID = spawn_link(fun() -> ... end).
```
- Voglio gestire l'errore
```Erlang
process_flag(trap_exits, true).
PID = spawn_link(fun() -> ... end).
```

es
```Erlang
-module(edemo1). 
-export([start/2]). 
start(Bool, M) -> 
	A = spawn(fun() -> a() end), 
	B = spawn(fun() -> b(A, Bool) end), 
	C = spawn(fun() -> c(B, M) end), 
	sleep(1000), status(b, B), status(c, C). 
a() -> process_flag(trap_exit, true), wait(a). 
b(A, Bool) -> process_flag(trap_exit, Bool), link(A), wait(b). 
c(B, M) -> link(B), 
	case M of 
		{die, Reason} -> exit(Reason); 
		{divide, N} -> 1/N, wait(c); 
		normal -> true 
	end.
wait(Prog) -> 
	receive 
		Any -> io:format("Process ~p received ~p~n", [Prog, Any]),
		wait(Prog) 
	end. 
sleep(T) -> 
	receive after T -> true end. 
status(Name, Pid) -> 
	case erlang:is_process_alive(Pid) of 
		true -> io:format("process ~p (~p) is alive~n", [Name, Pid]); 
		false -> io:format("process ~p (~p) is dead~n", [Name, Pid]) 
	end.
```

A processo di sistema linkato a B, B processo di sistema SE Bool è True e C muore con ragione M

- Quando C muore in modo normale, B non muore e quindi neanche A
```cmd
edemo1:start(false, {die, normal}).
```
- B non essendo di sistema, quando C muore per una ragione non normale, allora anche B muore MA A rimane viva perché è di sistema
```cmd
edemo1:start(false, {die, abc}).
```
- B non essendo di sistema, quando C muore per `{badarith, ...}` muore anche lui propagando a A
```cmd
edemo1:start(false, {divide, 0}).
```
- B essendo di sistema, cattura l'errore che non verrà propagato ad A
```cmd
edemo1:start(true, {divide, 0}).
```

Nota
`erlang:is_process_alive(Pid)` SE il processo è vivo, True ALTRIMENTI False