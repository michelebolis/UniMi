Verificare in maniera esaustiva che P(d) sia corretto per ogni $d \in D$ è impossibile.

Il criterio di selezione è il ragionamento o le regole che utilizziamo nel selezionare un sottoinsieme di D (per approssimare il test ideale)

Un criterio C si dice `affidabile` SE presi T1 e R2 in base al criterio C, ALLORA o entrambi hanno successo o nessuno dei due ha successo
$$affidabile(C, P)<->(\forall T_1 \in C, \forall T_2 \in C, successo(T_1, C) <->successo(T_2, C) )$$

Un criterio C si dice `valido` SE quando P non è corretto, ALLORA esiste almeno un T selezionato in base a C, che ha successo per il programma P
$$valido(C, P) <-> (!ok(P, D) -> \exists T \in C \text{ t.c. } successo(T,P))$$

ATTENZIONE
$$[affidabile(C, P) \wedge valido(C, P) \wedge T \in C \wedge \neg successo(T, P)] -> ok(P,D) $$
SE usiamo un test con un criterio affidabile e valido, il test non trova errori MA il criterio selezionerebbe test ideale che non esistono

[[Es Criterio di selezione]]
[[Criterio di selezione - Ragionamento]]
[[Criteri di selezione]]

