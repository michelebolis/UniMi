Classless Inter Domain Routing
Sono state scartate le varie classi
A varie organizzazioni vengono dati una certa porzione di indirizzamento libera
ogni entry nei router dovrà avere un indirizzo di partenza e una maschera che filtrerà i bit di host ID

es Tabella di instradamento

| Location | IP inizio    | IP fine      | Tot indirizzi | Base                                    | Maschera |
| -------- | ------------ | ------------ | ------------- | --------------------------------------- | -------- |
| Milano   | 194.24.0.\_  | 194.24.7.\_  | 2048          | 1100 0010 0001 1000 0000 0000 0000 0000 | \\21     |
| Roma     | 194.24.16.\_ | 194.24.31.\_ | 4096          |                                         |          |
| Torino         | 194.24.8.0             | 194.24.11.\_             |   1024            |                                         |          |

Maschera \\n = n bit a 1 e 31-n bit a 0

Arriva pacchetto con indirizzo 194.24.17.4
SE applicando la maschera all'address ottengo l'indirizzo base della location, l'indirizzo appartiene a tale rete
Prova a mappare l indirizzo su Milano
1100 0010 0001 1000 0001 0001 0000 0100 base
1111 1111 1111 1111 1111 1000 0000 0000 maschera
1100 0010 0001 1000 0001 0000 0000 0000 base AND maschera

Non ottengo la base di Milano
Facendo la stessa cosa con Roma, ottengo l'indirizzo base di Roma
Il pacchetto viene quindi instradato verso il SubNet di Roma

Le tabelle di routing contengono quindi l'indirizzo base, quanti bit utilizza la maschera, la maschera stessa MA l'elaborazione della tabella è piu costosa in quanto devo potenzialmente scorrere tutte le entry per trovare il SubNet giusto

CIDR ha liberato molto indirizzi IPv4