Per il teorema di Taylor
$$f(x^{(k)} + s_kd^{(k)}) = f(x^{(k)}) + s_kd^{(k)T} \bigtriangledown f(x^{(k)}) + ...$$
`Questa approssimazione decresce piu rapidamente nella direzione opposta a quella del gradiente`
$$d^{(k)} = - \frac{\bigtriangledown f(x^{(k)})}{||\bigtriangledown f(x^{(k)})||}$$
Vantaggio: questo metodo (steepest descent method) `richiede solo il calcolo del gradiente e non delle derivate seconde`