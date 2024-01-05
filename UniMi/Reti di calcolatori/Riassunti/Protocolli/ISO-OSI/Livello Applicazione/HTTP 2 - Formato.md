In HTTP 1.X si lavora con messaggi atomici (header+body).  L'header è tutto testuale occupando molto e si ripetono senza compressione 
In HTTP 2 invece un frame rappresenta un pezzo di un messaggio. 

| Tipo di frame | Descrizione |
| ---- | ---- |
| [[Frame Header]] | contiene l'header HTTP: il suo payload sono i vari header |
| [[Frame Data]] | contiene le informazioni della mail |
| [[Frame Setting]] | per cambiare informazioni durante lo scambio di messaggio |
| window update |  |
| [[Frame Push_Promise]] | permette di informare il client che arriveranno delle info (risposta senza richiesta) |
| Frame PING | con Type = 0x6 |

Formato header di un qualsiasi frame

| Campo             | Dimensione | Descrizione                                                 |
| ----------------- | ---------- | ----------------------------------------------------------- |
| Length            | 24 bit     | in modo che il ricevente sappia quando termina il messaggio |
| Type              | 8 bit      |                                                             |
| Flags             | 8 bit      | dipendono dal tipo di frame                                 |
| bit riservato     |            |                                                             |
| Stream identifier | 31 bit     | identifica in quale stream mettere il messaggio             |
| Payload                  |            |                                                             |
