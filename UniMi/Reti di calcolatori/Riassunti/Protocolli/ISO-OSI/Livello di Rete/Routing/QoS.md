I router devono rispettare i QoS
Oltre ai pacchetti con il payload ci sono anche pacchetti di controllo 
Il resto dei pacchetti va nel flusso dati
Estratto il packet classifier (TOS bit) dall header, viene fatto uno scheduling sulla coda in base alla politica di scheduling

Il classifier decide in quale coda inviare il pacchetto
Le code di I/O per ogni porta di I/O sono diverse in base alla qualita di servizio che vogliono offrire
Un router ha tante code quanti sono i servizi che puo offrire


| Tipo di traffico - Esigenze  | Affidabilita | Delay | Jitter | Banda |
| ------------------ | ------------ | ----- | ------ | ----- |
| email              | Alta         | Basso | Basso  | Basso |
| web (come FTP)     | Alta         | Basso | Basso  | Medio |
| FTP                | Alto         | Basso | Basso  | Medio |
| audio streaming    | Basso        | Medio | Alto   | Basso |
| video streaming    | Basso        | Alto      | Alto       | Alto      |
| Internet telephone | Basso        |       |        |       |
| video conference   | Basso        | Alto      | Alto       | Alto      |

Jitter: tempo da quando il messaggio parte a quando arriva al destinatario
NON tutti i pacchetti hanno lo stesso ritardo

La digitalizzazione di un segnale analogico passa da campionamenti. Decido una frequenza di osservazione e ad ogni bit campione il valore di tensione, producendo un byte 
Piu è la frequenza di campionamento maggiore è la qualita


8000 campioni al secondo ( uno ogni 125microsecondi) per garantire...
Dato che ogni campione produce un byte, al secondo produco 64KB (minimo di banda per avere una qualita minima). Alternativa 16000 campioni al secondi quindi 128KB
PCM Pulse Code Modulation
Anche in ricezione dovro avere la stessa frequenza di arrivo dei messaggi, quindi uno orgni 125microsecondi (CBR Constant Bit Rate in ricezione)

Anche perche audio e video hanno un Jitter sensibile
Per garantire questo requisito su Internet, viene delegato al SW: Buffer di playout, permette di bufferizzare e risolvere la scarsa qualita della rete (dimensionamento in base alla qualita della rete)

La coda di output dei router è gestita con due blocchi
- Servizio affidabile: solitamente pacchetti generati dal [[TCP]]
- Servizio sensibile al delay, [[UTP]]