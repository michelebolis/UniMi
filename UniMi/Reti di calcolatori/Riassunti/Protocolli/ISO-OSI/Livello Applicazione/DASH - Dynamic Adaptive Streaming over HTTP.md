Come funzionano i video on demand
All'inizio la qualità è bassa e se ci sono problemi di rete, la qualità è adattiva

Client: decodifica i frame, solitamente sono definiti come differenze in pixel rispetto al precedente. Gestisce inoltre perdita dei pacchetti e il jitter (Tipicamente vengono bufferizzate parti del video)


Standard DASH Dynamic Adaptive Streaming over HTTP
E' adattivo rispetto alle condizioni di rete e utilizza HTTP
Lo stesso stream di bit, che rappresenta il video, viene codificato con diverse qualità partendo da una qualità "massima" es in FULL HD con 1Mb/s, FULL HD con 4 Mb/s...
Viene diviso lo stream in Chunk, tipicamente di 5/10 secondi

All'inizio dello stream, viene scaricato un manifest MPD (Media Presentation Description) contenente le versioni disponibili per il video (stessa cosa per l audio) fornendo gli URL base, quanto sono lunghi i singoli Chunk (per dimensionare il proprio buffer e per gestirlo in modo dinamico) 
Obiettivo: evitare buffering ("pause")

All'interno del playback buffer si cerca di mantenere un certo tempo di visualizzazione (l avanzamento della barra si ferma quando è in pausa il video in modo da non scaricare piu del necessario). MA quando il numero di chunk va sotto la soglia, si richiede altri chunk.
La parte Dynamic è del client che decide la qualità di chunk da richiedere, cioe gradualmente si cerca di ottimizzare il buffer garantendo un qualità decente evitando il buffering scegliendo a quale URL del manifest richiedere i chunk n-esimi.