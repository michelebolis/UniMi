SE h non perfetta
Una collisione si verifica quando dovendo inserire o cercare una chiave x la posizione h(x) è occupata da un'altra chiave y
OSS non è detto h(x)= h(y)

Convivere con le collisioni
- Fare in modo che avvengano raramente: h deve sparpagliare le chiavi nella tabella in modo che le collisioni siano poco probabili
- Avere una strategia per gestire le collisioni nel caso accadano

$h: U -> {0,…,m-1}$ funzione di hash
Per $x \in U, P(x)$ probabilità che scegliendo $x$ a caso una chiave da $U$ si scelga $x$
Per $i=0,…,m-1, Q(i)= \sum_{x:h(x)=i} P(x)$ probabilità che una chiave scelta a caso da $U$ abbia valore hash $i$
La funzione hash è UNIFORME SE $Q(i)$ è la stessa per ogni $i$ cioè $Q(i)=\frac{1}{m}$

Es $U=[0, 1)$ numeri reali con m=10. h: U-->{0, …, 9}; $h(x)=[10x]$ h è uniforme se OGNI x ha la stessa probabilita di essere scelto
U=Cognomi con m=26 con h(x)=#lettera(1a lettera); h non è uniforme

es


Requisiti di una buona funzione di hash
- Uniforme per evitare collisioni
- Veloce da calcolare

Metodi
- [[Collisioni - Metodo della divisione]]
- [[Collisioni - Metodo del ripiegamento]]


Tecnica di gestione: esterna o interna
- Esterna: [[Tabella di hash - Lista di collisione]]
- Interna: Tabelle di hash - Indirizzamento aperto

Inserimento di elemento di chiave: SE $h(k)$ è gia occupata si cerca un'altra posizione libera utilizzando una strategia predefinita (es la prima posizione libera successiva MOD m, scansione lineare)

Utilizziamo una funzione ausiliaria $c(k, i)$ con $k$ chiave e $i\geq0$ ordine nella scansione

Per trovare il posto in cui collocare l'elemento di chiave k si scandiscono nell'ordine le posizioni di indici $c(k, 0), …, c(m-1)$ sino a trovare una posizione libera

La funzione ausiliaria deve verificare
$c(k, 0)= h(k)$
${c(k,0), …, c(k, m-1)}= \{0, …, m-1\}$

Es
Scansione lineare $c(k, i)= (h(k) + i) \text{ MOD } m$
Possibilità di agglomerazione primaria
Scansione quadratica $c(k, i)= \lfloor (h(k) + c_1*i + c_2*i) \rfloor \text{ MOD } m$
Con $c_1, c_2$ opportuni
SE $h(k_1)=h(k_2)$ la sequenza di celle scandita è la stessa
Possibilita di agglomerazione secondaria

es
Hashing doppio $c(k, i)= (h(k) + ih'(k)) \text{ MOD } m$
Dove $h': U --> {0, …, m-1}$ una seconda funzione di hash
Situazione ideale SE $h(k_1)=h(k_2)$ ALLORA $h'(k_1)\neq h'(k_2)$
Possibilita di agglomerazione secondaria
