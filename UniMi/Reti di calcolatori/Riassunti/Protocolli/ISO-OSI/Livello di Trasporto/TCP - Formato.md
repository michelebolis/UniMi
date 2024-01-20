Formato header: (min di 20B)

| Campo | Dimensione | Descrizione |
| ---- | ---- | ---- |
| Porta sorgente | 16 bit | scelta dalla sorgente stessa |
| Porta destinazione | 16 bit | porta nota |
| Sequence number (SEQ) | 32 bit | indica l inizio dei byte che vengono trasmessi in un segmento TCP |
| ACK number | 32 bit | identifica il byte successivo che mi aspetto (es 10 vuol dire che ho mandato correttamente i primi 9 quindi mi aspetto il 10) |
| Flag bits | 6 bit | Elenco qui di seguito |
| 1. URG flag | 1 bit | urgente |
| 2. ACK flag | 1 bit | = 1 SE il campo `ACK number` deve essere controllato |
| 3. PSH flag | 1 bit | = 1 SE non bisogna aspettare che il buffer sia pieno per mandare i messaggi |
| 4. RST flag | 1 bit | abort |
| 5. SYN flag | 1 bit | usato in fase di creazione della connessione |
| 6. FIN flag | 1 bit | usato in fase di chiusura della connessione |
| Window size |  | numero di byte che posso trasmettere. Dipende dal buffer ricevente della socket |
| Checksum |  | per verificare se il segmento è corretto |
| Urgent pointer | 16 bit | usato un tempo per mandare CTRL C prima del comando che voglio annullare, è l offset dei dati dove iniziano i dati urgent |
| N [[TCP - Option]] | $N*32bit$ |  |
Il checksum non viene calcolato solo sul TCP ma sullo pseudo header: sul source IP, sul destination IP (dal DNS), protocol selector (6 per il TCP), la lunghezza del segmento + TCP header, opzioni dati ed eventualmente un padding

