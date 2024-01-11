- Determinare massimo ritardo di propagazione associato con i seguenti canali di comunicazione: 
1. connessione attraverso linea telefonica di 1 Km  
2. connessione via canale satellitare di 50000 Km 

Nel primo caso il mezzo è in rame, perciò $v_p = 2*10^8m/s$; 
nel secondo caso è $v_p = 3*10^8m/s$. 
Perciò: 
1. $t_p = \frac {10^3 m}{2*10^8m/s} = 0.5*10^{-5} s$.  
2. $t_p = \frac {5*10^7 m} {3*10^8m/s} = 1.67 * 10^{-1} s$.

- Se data link layer usa bit stuffing e preambolo di frame è 01110, mostrare quale sequenza di bit è trasmessa a partire dai dati 0 1 1 1 0 0 1 0 1 1 1 1 1 1
01110 011*0*1001011*0*11*0*11*0* 01110 

- Un canale ha bit rate 4 Kbps e ritardo di propagazione di 20 msec. Per quale range di frame size Idle RQ ha efficienza almeno 50%?

$U >=50$ SE $\frac {t_x}{t_x+2t_p} = \frac {{x}/{b}}{{x}/{b} + 2t_p} = \frac {x}{x+2bt_p}>=0.5$ 
$0.5x >=bt_p$
$x >= 2·b·t_p = 8000*t_p = 8000*0.02 = 160 bit$

- Calcolare l'utilizzo di un canale avente banda di 6 Mbps e lunghezza del cavo in rame di 4 Km, ottenuto da un protocollo di livello Data Link che genera frame di taglia fissata 1.5 Kb e che adotta un approccio di tipo stop-and-wait (Idle RQ).

$t_p = \frac {4*10^3}{2*10^8} = 2*10^{-5}$
$t_x = \frac{1.5*10^3}{6*10^6} = 0.25*10^{-3}$
$U = \frac {0.25*10^{-3}}{0.25*10^{-3} + 4*10^{-5}}=\frac {1}{16*10^{-2}}$
