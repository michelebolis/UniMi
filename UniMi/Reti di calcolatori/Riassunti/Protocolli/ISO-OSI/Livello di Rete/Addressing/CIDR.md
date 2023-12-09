Classless Inter Domain Routing
A varie organizzazioni vengono dati una certa porzione di indirizzamento libera

Le tabelle di routing contengono l'indirizzo base, quanti bit utilizza la maschera (che definisce la divisione tra NetID e HostID), la maschera stessa 

Vantaggi: uso piu efficiente dello spazio di indirizzamento
Svantaggio: complicazione del routing dei pacchetti in quanto devo potenzialmente scorrere tutte le entry per trovare il SubNet giusto

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

