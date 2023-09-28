 **I2C (Inter-Integrated Circuit)** bus seriale per comunicazioni a breve distanza. Solitamente usato all'interno dello stesso sistema.  
 È un bus "multi-master" dove i nodi possono essere:

* master: genera il serial clock (SCL - attivo-basso) che abilita l'invio di informazione e fa partire la comunicazione.
* slave: riceve il segnale di clock e risponde quando indirizzato dal master.
 Processo:

 1. Il master abilita il serial clock SCL
 2. il master disattiva il passaggio dati SDA per settare la condizione di start (SCL attivo, SDA disattivo)
 3. il master pecifica l'indirizzo dello slave di destinazione (7 bit) e 1 bit per il tipo di operazione (read/write)
 4. il master attende il segnale di ACK dello slave
 5. lo slave manda pacchetti da 8 bit seguiti da un segnale di ACK
 6. lo slave manda il segnale di fine trasmissione (stop condition) effettuando l'inverso dela condizione di start
