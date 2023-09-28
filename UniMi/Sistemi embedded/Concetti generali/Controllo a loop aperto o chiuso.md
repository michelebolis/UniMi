 Modello per rappresentare il funzionamento del sistema definisce una funzione di trasferimento *f(U(t), C(t), A(t))* con:

* U vettore delle variabili di uscita
* C vettore delle variabili di controllo
* A vettore delle variabili d'ambiente  

per **controllo a loop chiuso** ( f(C(t),A(t),U(t)) ) intendiamo un sistema la cui variazione di stato nel tempo dipende dalle variabili di ingresso(C), dalle variabili ambientali(A) (es umidità) e dalle variabili di uscita precedenti(U). (Esempio PIR: variazione di calore perciò deve conoscere la rilevazione precedente)  
per **controllo a loop aperto** ( f(C(t),A(t)) ) intendiamo un sistema la cui variazione di stato nel tempo dipende solo dalle variabili di ingresso e da quelle ambientali. (Esempio: LED)  
Il problema del controllo a loop aperto è che non c'è nessun controllo dell'efficacia dell'azione. (es con motore step non siamo sicuri che mantenga una velocità stabilita poichè se aggiungessimo un carico, questa rallenterebbe a fronte di un input invariato)

Un modello di controllo è il [[PID]]