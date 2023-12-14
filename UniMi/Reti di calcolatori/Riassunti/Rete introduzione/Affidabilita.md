L'affidabilità, oltre ai messaggi, riguarda anche l'identificazione del malfunzionamento di un link.
Ci possono essere diversi livelli di tolleranza dell'errore (verra demandata al TCP, affidabile se END to END)

Tipi di allocazione
- allocazione a commutazione di circuito: è richiesta una comunicazione completa, senza interruzione del traffico (es voce)
- allocazione a commutazione di pacchetto: come condividere i canali a disposizione dei vari host
	Usiamo tecniche di multiplexing per condividere i canali da piu host 
	- time division multiplexing TDM: usata nell'ambito delle reti fisse, in particolare per l upload. MA non tiene conto della priorità

Controllo per garantire l'affidabilità della rete
- [[Controllo di flusso - Introduzione]]
- [[Controllo di congestione - Introduzione]]

La maggior parte delle rete mette a disposizione:
- Servizio non affidabile o best-try / best-efford
- Servizio affidabile: che permesse l'invio di un blocco mancate del pacchetto, portando pero ad un overhead necessario nei pacchetti