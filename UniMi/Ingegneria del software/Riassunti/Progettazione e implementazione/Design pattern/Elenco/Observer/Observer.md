Problema: una serie di elementi vanno tenuti sincronizzati, abbiamo uno stato comune che va mantenuto coerenti in tutti gli elementi
es visualizzare in diversi modi un dato

[[Observer - antipattern]]:

La soluzione è estrarre lo stato comune in un oggetto a parte, Subject, e gli Observer osserveranno tale stato.
Si sta quindi centralizzando la gestione dello stato

Ci sono classi apposite in java MA non sono thread-safe
NON si fa continuamente polling ma si usa un'architettura event-driven in cui gli Observer si registrano al Subject, che li informera quando avvengono cambiamenti di stato 
La sottoscrizione o la rimozione avviene attraverso `addObserver()` e `removeObserver()`
una volta modificato lo stato con setState() si utilizza un notifyObservers() che cicli sugli Observers richiamando update(Observable, Object) con
- Observable il Subject di cui è stato modificato lo stato
- Object la parte di stato modificata

![[Pasted image 20231109091949.png]]

Filosofie
- [[Observer - Push]]
- [[Observer - Pull]]
- [[Observer - Approccio ibrido]]