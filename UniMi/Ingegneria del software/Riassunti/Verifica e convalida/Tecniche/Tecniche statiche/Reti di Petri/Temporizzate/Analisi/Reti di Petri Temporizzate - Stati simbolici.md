Nelle reti TB si attua una rappresentazione simbolica degli stati in modo da togliere la `difficolta di distinguere tra gettoni con timestamp diversi`
Uno `stato simbolico` rappresenta un insieme di possibili stati con in comune lo stesso numero di gettoni in ogni posto/marcatura
Uno stato simbolico è una coppia $[\mu, C]$ dove
- $\mu$ è la `marcatura simbolica` che associa un `multiset di identificatori simbolici ai posti`
- C sono i `vincoli`, disequazioni che rappresentano le relazioni tra gli identificatori simbolici

Assumiamo che $tf_t$ sia un intervallo con estremi inclusi esprimibili mediante espressioni lineari funzioni dei tempi dei token in ingresso e di tempi assoluto
Con $tmin_t$ il limite inferiore e $tmax_t$ il limite superiore,
$$tf_t = \{X | X \geq tmin_t \wedge X \leq tmax_t\}$$
