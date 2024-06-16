- Tangenza tra due circonferenze: la distanza tra i due centri deve essere uguale alla somma dei rispettivi raggi
$$raggio_1 + raggio_2 = sqrt((x[1] - x[2])^2 + (y[1] - y[2])^2)$$
- Non tangenza tra due circonferenze: uguale alla tangenza ma invece dell'uguale scrivere $\leq$
- Imporre che una $x$ variabile sia multiplo di $n$: uso una variabile integer $y$ definisco $x = y*n$ 
- Distanza tridimensionale tra due punti
$$sqrt((X - x[a])^2 + (Y - y[a])^2 + (Z - z[a])^2)$$
- SE le mie variabili ($a$, $b$, $c$) rappresentano una retta, aggiungere il vincolo: (si assicura che la retta non sia degenere)
$$a^2 + b^2 = 1$$
- linearizzare la differenza in valore assoluto: (in questo caso M dato dalla distanza massima tra due punti)
$$... \geq - delta + M * w[i];$$
$$... \leq+ delta - M * w[i];$$
- Imporre che quando la distanza in valore assoluto sia minore di un k, allora c è un vincolo
{f1 in Frequenze, f2 in Frequenze : ($val[f1] > val[f2]$) and ($val[f1] - val[f2] < k$)} :

- Distanza tra un punto ($x_0$, $y_0$) e una retta $ax+by+c=0$ è data da:
$$\frac{ax_0+by_0+c}{\sqrt{a^2+b^2}}$$
OSS se sto lavorando al variare del punto, posso tralasciare il denominatore che è uguale

- Punti interni ad un rettangolo: rappresento i lati come rette in modo tale che un punto è interno SE
$$a[r] * x[p] + b[r] * y[p] + c[r] \geq 0$$
MA nel caso del rettangolo servono vincoli di perpendicolarita tra rette:
$$a[0] * a[1] + b[0] * b[1] = 0;$$
e vincolo di antiparallele (per $r \leq 1$ con $r := 0..3$)
$$a[r] * a[r+2] + b[r] * b[r+2] = -1$$ 
- Punti interni ad un triangolo: i punti devono essere una combinazione convessa dei vertici (per ogni i in Punti) 
$$x[i] = \sum_{j \in Vertici} lambda[i,j] * xx[j]$$
Stessa cosa da applicare alle $y$ con poi il vincolo che per ogni i in Punti:
$$ \sum_{j \in Vertici} lambda[i,j] = 1$$
- Come scalare o traslare una funzione: dichiarare 4 variabili $a$, $b$, $c$, $d$
$$c + b * f((x-a)/d)$$
- Quando in un set nei dati, devo scorrere a due a due (ATT solo in AMPL):
sum {t in Tappe\[v\]: ord(t) > 1} distanza\[prev(t), t\];

- Quando ho uno stoccaggio che tra i vari istanti di tempo resta, allora dichiaro una variabile che indica la quantita in stoccaggio nel periodo (dopo aver tolto o aggiunto merce). Si aggiungerà un vincolo per l istante 1 mentre per gli altri si guarderà alla rimanenza nell'istante $t-1$
- SE per una variabile binaria, quando è 1 si devono disattivare dei vincoli, allora dichiaro una variabile $M$ grande in modo tale che la sottraggo ($M*x$) nella disequazione