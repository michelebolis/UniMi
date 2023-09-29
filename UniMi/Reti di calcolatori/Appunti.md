Libri:
- Networking e Internet Pearson 5a edizione
- secondo libro solo ultima parte del corso
NO LUCIDI

Esame:
- Teoria: risposta libera a 10 domande di ragionamento in 1ora e mezza (60%)
- Lab: 2 parti (40%)


Come Far parlare la macchina A con la macchina B?
Nei Server all'inizio risiedevano solo i contenuti: la macchina A poteva depositare contenuti o richiederli. 

La rete permette di far comunicare le macchina con le macchine server
Oggi i contenuti delle macchine server sono cambiati, infatti non sono solo di archiviazione ma è anche sistema che eroga servizi per l'utente

I sistemi-cloud sono sistemi di rete connessi ad altissima velocita per erogare servizi all'utente attraverso il plugin installato sulla macchina dell'utente
I sistemi cloud pero ora sono usati per quei servizi che non hanno problemi di tempo, infatti per ogni richiesta è necessario un Δt, che è variabile (es contenuto richiesto contemporaneamente da molti utenti).

Se tempo è troppo variabile diventa un problema

Il cloud si sposta sempre piu vicino all'utente. Si copia il contenuto in vari punti strategici attraverso un servizio di CDL Content Delivery L, e successivamente sarà necessario un updating.

Requisiti della rete:
- Affidabilità: se A manda un contenuto a S o viceversa, quel trasferimento è privo di errori. 
	Ci possono essere diversi livelli di tolleranza dell'errore 
- Sicurezza: ma non è un problema di chi progetta la rete, è di chi progetta l'applicazione
- Prestazioni: misurabili 
	- nella **velocità di trasferimento** in funzione del bit rate dei canali
	- ... verificare se la mia rete riesce ad erogare all'utente finale la velocita promessa
- Indirizzamento: la rete deve poter indirizzare il contenuto al destinatario connesso. 
	==Ogni destinatario o mittente deve essere indirizzabile==. 
- Qualità di servizio QoS: deve riuscire ad erogare i servizi date le specifiche dell'applicazione (es tempo massimo, tolleranza degli errori...) 

Livelli della rete
1. Rete-di-accesso: qualsiasi sistema di rete (es LAN) che collega le macchine e consente di aggregare tutto il traffico da e verso la rete. Tipi di aggregatori di traffico
		1. Rete locali fissi
		2. Rete locali wireless
		3. Rete cellulare: è mobile fino a che manda il traffico ad una rete locale wireless (antenna)
2. Rete-fissa: è la rete Internet ma puo essere anche presente all'interno delle rete di accesso

Non posso tirare un filo per ogni dispositivo
Dobbiamo utilizzare dei concentratori
Per collegare i concentratori delle due reti, dati i loro indirizzi R1 e R2, non posso usare direttamente un cavo ma userò altri concentratori

La rete è quindi un insieme interconnesso di concentratori di traffico, router, che consentono di raggiungere una destinazione con un cammino multi hop (multi salto).

Router: consentono di trovare il percorso migliore per raggiungere una destinazione in quel momento.

Requisiti della rete:
- Indirizzamento
- Instradamento: sarà necessario un algoritmo di instradamento
- Affidabilità: (o forse non conviene alla rete, verra demandata al TCP, affidabile se END to END)
- QoS


Un router ha delle linee di ingresso e delle linee d'uscita, entrambi bidirezionali (porte I/O). 
I router ha un piccolo SW di instradamento che processerà le code di ingresso e uscita legate alle porte. 

I problemi sono il numero di porte e la velocita in cui operano i link di uscita e ingresso.
Il router decide in che porta mandare il contenuto in coda di uscita in base ad una tabella in cui si specifica istante per istante, il percorso migliore per ogni indirizzo raggiungibile.
SE una delle code/buffer è pieno, butto via il contenuto. Uno dei problemi dei router è la gestione della memoria. 

Si decise quindi di ==frammentare il contenuto in dimensioni massime fisse== creando pacchetti in modo da avere una gestione del traffico semplificata. 
Questa frammentazione deve avvenire lato del mittente, aggiungendo un header o intestazione con delle informazioni necessarie per il funzionamento della rete, quali l indirizzo. 

Man mano che il pacchetto viene processato dai router  aumenta di dimensione, diminuendo quando arriva al destinatario (fragmentation-assembly-deassembly)


Rete a commutazione di pacchetti:
