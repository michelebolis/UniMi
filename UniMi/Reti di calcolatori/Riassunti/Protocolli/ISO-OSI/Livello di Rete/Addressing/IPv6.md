Abbiamo come min 40Byte per l header

Address da 16 byte l uno

  

Notiamo la divisione quasi geografica anche nel pacchetto

TLA -> NLA -> SLA

  

Upper bound del payload sempre di 64K

ToS rinominato in TrafficClass consente di classificare in base alle qualita di servizio richiesto mentre FlowLevel viene inserita dalla sorgente al proprio specifico flusso dati

  

NextHeader contiene l header di TCP di default

SE è invece un header diverso da quello TCP, vuol dire che è uno di quelli previsti dello standard

- Step by step (0)

​

- Source routing (43) (al massimo posso specificare 24 indirizzi nel campo opzione, quindi 48; avro poi un array di 24 bit che è 0 SE l IP deve essere raggiunto in modo approssimato mentre 1 in modo esatto)

- Esatto

- Approssimato

  

Notare che mancano i campi per la frammentazione, ma viene inclusa nella option

  

  

Come far interagire macchine IPv4 e IPv6

- Mettere un gategay v4-v6: PT ProtocolTransformation per trasformare un header in un altro header. Il NAT mappa da v4 a v6 e viceversa grazie a un pull da cui preleva degli IPv4/v6 da assegnare