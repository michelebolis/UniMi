```Erlang
-module(chat_client). 
-export([start/1,connect/5]). 
start(Nick) -> connect("localhost", 2223, "AsDT67aQ", "general", Nick).

connect(Host, Port, HostPsw, Group, Nick) -> 
	% spawn del middleman 
	spawn(fun() -> handler(Host, Port, HostPsw, Group, Nick) end). 
handler(Host, Port, HostPsw, Group, Nick) -> 
	process_flag(trap_exit, true), 
	start_connector(Host, Port, HostPsw), 
	disconnected(Group, Nick).

start_connector(Host, Port, Pwd) -> 
	% linking tra middleman e il server
	S = self(), 
	spawn_link(fun() -> try_to_connect(S, Host, Port, Pwd) end).

disconnected(Group, Nick) -> 
	receive 
		{connected, MM} -> % from the connection process 
			io:format("connected to server\nsending data\n"), 
			lib_chan_mm:send(MM, {login, Group, Nick}), 
			wait_login_response(MM); 
		{status, S} -> 
			io:format("~p~n",[S]), 
			disconnected(Group, Nick); 
		Other -> 
			io:format("chat_client disconnected unexpected:~p~n",[Other]), 
			disconnected(Group, Nick) 
	end.

try_to_connect(Parent, Host, Port, Pwd) -> 
	%% Parent è il Pid del processo che sta usando try_to_connect, 
	% quindi il middleman 
	case lib_chan:connect(Host, Port, chat, Pwd, []) of 
		{error, _Why} -> 
			Parent ! {status, {cannot, connect, Host, Port}}, 
			sleep(2000), 
			try_to_connect(Parent, Host, Port, Pwd); 
		{ok, MM} -> 
			lib_chan_mm:controller(MM, Parent), 
			Parent ! {connected, MM}, %% to disconnected 
			exit(connectorFinished) 
	end. 

sleep(T) -> receive after T -> true end.

wait_login_response(MM) -> 
	receive 
		{chan, MM, ack} -> active(MM); 
		{'EXIT', _Pid, connectorFinished} -> wait_login_response(MM); 
		Other -> 
			io:format("chat_client login unexpected:~p~n",[Other]), 
			wait_login_response(MM) 
	end.
active(MM) -> 
	receive 
		{msg, Nick, Str} -> 
			lib_chan_mm:send(MM, {relay, Nick, Str}), 
			active(MM); 
		{chan, MM, {msg, From, Pid, Str}} -> 
			io:format("~p@~p: ~p~n", [From,Pid,Str]), 
			active(MM); 
		{close, MM} -> exit(serverDied); 
		Other -> 
			io:format("chat_client active unexpected:~p~n",[Other]), 
			active(MM) 
	end.
```
