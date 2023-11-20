Si basa sul concetto di Erlang nodes, singola VM che comunica con altra VM in esecuzione sullo stesso pc o su altri

es
```Erlang
-module(kvs). 
-export([start/0, store/2, lookup/1]). 
start() -> register(kvs, spawn(fun() -> loop() end)). 
store(Key, Value) -> rpc({store, Key, Value}). 
lookup(Key) -> rpc({lookup, Key}). 
rpc(Q) -> 
	kvs ! {self(), Q}, 
	receive 
		{kvs, Reply} -> Reply 
	end. 
loop() -> 
	receive 
		{From, {store, Key, Value}} -> 
			put(Key, {ok, Value}), From ! {kvs, true}, loop(); 
		{From, {lookup, Key}} -> From ! {kvs, get(Key)}, loop() 
	end.
```

```cmd1
erl -sname server
kvs:start().
kvs:lookup(weather).
```

```cmd2
erl -sname client
rpc:call(server@surtur, kvs, store, [weather, sunny]).
rpc:call(sif@surtur, kvs, lookup, [weather]).
```

`erl -sname nomeTerminale`: permette di avere un terminale server con un nome specifico che poi richiamerò da un altro terminale client
`rpc:call` libreria standard
I cookie si utilizzano per comunicazione ssh

Erlang Node è una VM Erlang con il proprio indirizzo e set di processi
SE abbiamo tanti nodi, abbiamo un cluster
Le primitive nei sistemi distribuiti, hanno un argomento in piu, cioè il Node
- `spawn(Node, Mod, Func, ArgList)-> Pid`
- `spawn_link(Node, Mod, Func, ArgList)-> Pid`
- `disconnect_node(Node) -> bools() | ignored`
- `monitor_node(Node, Flag) -> true`
- `{RegName, Node} ! Msg`

es
```Erlang
-module(ddemo). 
-export([rpc/4, start/1]). 
start(Node) -> spawn(Node, fun() -> loop() end). 
rpc(Pid, M, F, A) -> 
	Pid ! {rpc, self(), M, F, A}, 
	receive {Pid, Response} -> Response end. 
loop() -> 
	receive 
		{rpc, Pid, M, F, A} -> 
			Pid ! {self(), (catch apply(M, F, A))},
			loop() 
	end.
```

apply(M, F, A) permette di eseguire la funzione F del modulo M con parametri A
guardare in libreria rpc e global

due Node per comunicare devo avere lo stesso cookie
erl -setcookie "Cookie"
erlang:set_cookie(node(), "Cookie")
Problema: posso eseguire qualsiasi cosa

