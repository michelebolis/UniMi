OSS SE un test non rileva nessun malfunzionamento, non implica che il programma sia corretto

Un test `T` è ideale per `P` SE e SOLO SE $\neg successo(T, P) -> ok(P, D)$

Il superamento del test implica la correttezza del programma
In generale è impossibile trovare un test ideale

Test di Dijkstra: il test di un programma può rilevare la presenza di malfunzionamenti MA non esiste un algoritmo che dato un programma arbitrario `P` generi un test ideale finito (escludendo T = D)