Il rilassamento surrogato $S$ di un problema di ottimizzazione lineare discreto $P$ si ottiene `sostituendo un insieme di vincoli con un loro combinazione convessa`
$$P: min\{z(x): Ax \leq b, x \in X \subseteq Z^n_+\}$$
$$S: min\{z(x) : \lambda ^TAx \leq \lambda^T b, x \in X \subseteq Z^n_+\}$$
con $\lambda \geq 0$

Esso soddisfa le condizioni per essere un rilassamento
- Vincoli: $Ax \leq b$ implica $\lambda ^TAx \leq \lambda^T b$ MA non viceversa
- Obiettivo: non cambia