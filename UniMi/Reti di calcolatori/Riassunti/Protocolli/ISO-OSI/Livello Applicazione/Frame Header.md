$Type = 0x1$

Flag type 
- `END_STREAM`: se devo mandare solo il frame header e poi termino lo stream
- `END_HEADER`: se non ci sono piu blocchi di header 
- PADDED
- PRIORITY
Payload
Padding length
bit E
`Stream Dependency` 31 bit: a quale stream dipendo
`Weigth` 8 bit: identifica il peso per il controllo di flusso
Header Block Fragment: sono contenuti gli header HTTP
Padding
