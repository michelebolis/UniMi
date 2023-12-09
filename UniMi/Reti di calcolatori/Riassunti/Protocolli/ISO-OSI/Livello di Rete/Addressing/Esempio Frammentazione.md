se ho un host con TCP che produce dati da 7000B MA devo farceli stare su un token ring che li fa passare su 4kB e magari nella LAN destinazione ne fa passare al massimo 1kB

Deve frammentare i 7k in 4k e 3k (non viene frammentato in questo modo)
Bisogna tener presente che al payload bisogna aggiungere gli IP delle due macchine e altre info che in totale pesano 20B.
Il IP non gestisce una byte stream: si utilizza un fragment offset su 13bit MA la lenght è su 16bit. L'offset non viene contato sui byte ma sugli ottetti
QUINDI la dimensione deve essere un multiplo di 8
nel nostro caso è 3976 

MID = 0 SE il frammento è l ultimo del pacchetto

| Nome         | PKT ID | Fragment Offset | Tot length | Dati  | MID |
| ------------ | ------ | --------------- | ---------- | ----- | --- |
| 1° pacchetto | 20     | 0               | 7000B      | 3976B | 1   |
| 2° pacchetto             |  20      |  497               |  7000B          | 3024B      |    0 |

Frammentazione dei due pacchetti per la seconda rete nel router del destinatario

| Nome         | PKT ID | Fragment Offset | Tot length | Dati  | MID |
| ------------ | ------ | --------------- | ---------- | ----- | --- |
| 1° PKT 1a PT | 20     | 0               | 7000B      | 1480B | 1   |
| 1° PKT 2a PT | 20     | 185               | 7000B      | 1480B | 1   |
| 1° PKT 3a PT | 20     | 370               | 7000B      | 1016B | 1   |
| 2° PKT 1a PT | 20     | 497               | 7000B      | 1480B | 1   |
| 2° PKT 2a PT | 20     | 682               | 7000B      | 1480B | 1   |
| 2° PKT 2a PT | 20     | 807               | 7000B      | 64B | 0   |

Note: 
- Dati: 1480B (numero piu vicino a 1500-20 e divisibile per 8)
- Fragment Offset: 185 (=1480/8)