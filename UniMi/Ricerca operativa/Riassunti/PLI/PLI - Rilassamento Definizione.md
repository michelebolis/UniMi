Dato un problema $P = min\{z_P(x) : x \in X(P)\}$
un problema $R = min\{z_R(x) : x \in X(R)\}$ è un rilassamento di $P$ SE valgono
- $X(P) \subseteq X(R)$ //sulle regioni ammissibili
- $z_R(x) \leq z_P(x), \forall x \in X(P)$ //sugli obiettivi

OSS in caso di massimizzazione le disequazioni sono invertite

Corollario: $z^*_R \leq z^*_P$

`Un rilassamento è tanto migliore quando piu il suo valore ottimo è vicino a quello del problema originario` $z^*_P$
Ci sono molti tipi di versi di rilassamento:
- Rilassamenti combinatori: Il rilassamento combinatorio $C$ di un problema di  ottimizzazione combinatoria $P$ è ancora un problema di ottimizzazione combinatoria ma tipicamente molto piu facile da risolvere
- [[PLI - Rilassamento lineare continuo]]
- [[PLI - Rilassamento Lagrangeano]]
- [[PLI - Rilassamento surrogato]]

Si puo dimostrare che, scegliendo i migliori moltiplicatori $\lambda$, in caso di minimizzazione
$$z^*_{LP} \leq z^*_{LR} \leq  z^*_S \leq z^*$$
