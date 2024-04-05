Assumendo $s_k=1$ e trascurando dal terzo ordine in poi nello sviluppo di Taylor si ha tale approssimazione
$$f(x^{(k)} + s_kd^{(k)}) = f(x^{(k)}) + s_kd^{(k)T} \bigtriangledown f(x^{(k)}) + \frac{1}{2}d^{(k)T} \bigtriangledown^2f(x^{k})d^{(k)}$$

La direzione che minimizza questa quantita
$$d^{(k)} = - \bigtriangledown^2f(x^{(k)})^{-1}\bigtriangledown f(x^{k})$$
Il metodo di Newton è piu veloce e accurato ma richiede il calcolo dell'Hessiano ($\bigtriangledown^2f(x^{(k)}$) e puo essere usato solo quando quest'ultimo è positivo
Sono stati ideati metodi quasi-Newton approssimando l'Hessiano e aggiornando ad ogni iterazione l inverso dell Hessiano