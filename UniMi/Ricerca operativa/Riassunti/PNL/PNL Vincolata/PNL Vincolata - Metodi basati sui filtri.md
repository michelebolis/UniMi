Negli algoritmi basati sui filtri `l'ottimalità e l'ammissibilità vengono trattate come due obiettivi`, come nella `programmazione multi obiettivo`, e vengono accettate le soluzioni $x$ non dominate, cioe quelle per cui non è stata trovata in precedenza alcuna soluzione $x'$ con $f(x') \leq f(x)$ e $h(x') \leq h(x)$ dove viene indicata la misura della violazione dei vincoli con
$$h(x)  = \sum_{i \in E}|c_i(x)|+\sum_{i \in I}[c_i(x)]^-$$
Quindi nella struttura dati filtro `salvo sia il valore della funzione obiettivo che la violazione dei vincoli`

Nei metodi `line search` una soluzione $x^{k+1} = x^k+\alpha_kp_k$ viene accettata SE $(f^{k+1}, h^{k+1})$ è una `coppia di valori non dominata`
Nei metodi `trust region` SE una soluzione $x^{k+1}$ non viene accettata, si `riduce il raggio e si ripete l'iterazione`

In entrambi i casi vengono intercalate `iterazioni di ripristino dell'ammissibilità dove viene minimizzata` SOLO $h(x)$
