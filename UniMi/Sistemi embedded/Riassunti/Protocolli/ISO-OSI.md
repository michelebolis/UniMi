* Standard ISO-OSI: regolamenta la struttura globale del sottosistema completo di comunicazione. ISO adotta un modello a strati ciascuno dei quali esegue una funzione predefinita.  
  Gli strati dell'ISO/OSI possono essere separati in due categorie
  * Media layer: funzioni dipendenti dalla rete
  * Host layer: funzioni orientate applicazione

  Livelli:

  * Applicazione: fornisce all'interfaccia verso l'utente una gamma di servizi distribuiti sulla rete. Protocolli: HTTP, SMTP, FTP, SNMP, DNS…
  * Presentazione: riguarda la rappresentazione dei dati durante il trasferimento. Negozia e seleziona la rappresentazione di trasferimento appropriata eseguendo la necessaria conversione
  * Sessione: consente a due entita di organizzare e sincronizzare il loro dialogo. Responsabile della creazione e terminazione di un canale di comunicazione
  * Trasporto: funge da interfaccia tra gli stati superiori e gli altri
   ○ Fornisce un sistema di trasferimento dei messaggi indipendente dal tipo di rete
   ○ Controllo dell'integrita
   ○ Si occupa di riordinare i pacchetti
   ○ Garantisce il trasporto senza errori, in sequenza, nessuna perdita, nessun duplicato, qualita del servizio
   ○ Protocolli: TCP, UDP
  * Rete: è responsabile dell'apertura e della chiusura di una connessione
    * Offre l'inoltro sulla rete, l'indirizzamento e il controllo del flusso
    * Si occupa di armonizzare le diverse reti
  * Data link: si basa sulla connessione fisica fornita dal tipo di rete per garantire un sistema affidabile di trasferimento
    * Raggruppa i bit ricevuti dallo strato superiore e li spedisce in frame
    * Permette di individuare gli errori e dell'eventuale ritrasmissione
    * Permette di connettersi e recapitare dati a un nodo adiacente nella rete
  * Fisico
