```Erlang
-module(chat_group). 
-export([start/2]). 
start(C, Nick) -> 
	process_flag(trap_exit, true), 
	lib_chan_mm:controller(C, self()), 
	lib_chan_mm:send(C, ack), 
	self() ! {chan, C, {relay, Nick, "I'm starting the group"}}, 
	group_controller([{C,Nick}]). 

delete(Pid, [{Pid,Nick}|T], L) -> {Nick, lists:reverse(T, L)}; 
delete(Pid, [H|T], L) -> delete(Pid, T, [H|L]); 
delete(_, [], L) -> {"????", L}. 

group_controller([]) -> exit(allGone); 
group_controller(L) -> 
	receive 
		{chan, C, {relay, Nick, Str}} -> 
			lists:foreach(fun({Pid,_}) -> 
				lib_chan_mm:send(Pid, {msg,Nick,C,Str}) end, L), 
			group_controller(L); 
		{login, C, Nick} -> 
			lib_chan_mm:controller(C, self()), 
			lib_chan_mm:send(C, ack), 
			self() ! {chan, C, {relay, Nick, "I'm joining the group"}}, 
			group_controller([{C,Nick}|L]); 
		{chan_closed, C} -> 
			{Nick, L1} = delete(C, L, []), 
			self() ! {chan, C, {relay, Nick, "I'm leaving the group"}}, 
			group_controller(L1); 
		Any -> 
			io:format("group controller received Msg=~p~n", [Any]), 
			group_controller(L) 
	end.
```