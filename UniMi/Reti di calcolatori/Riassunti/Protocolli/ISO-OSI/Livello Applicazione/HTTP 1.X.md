E' un protocollo pensato per `richiesta-risposta da client a server `
Tutto `in ASCII`
Formato dei messaggi:
header: composto da $N$ linee simboleggiate da un `\n`

| Tipologia messaggio | Esempio |
| ---- | ---- |
| Richiesta: \<metodo HTTP> \<URL> \<versioneProtocollo>  | es GET /index.html HTTP/1.1 (metodi: GET/POST/PUT/DELETE/...) |
| Risposta: \<codice> \<testo del codice> | es 200 OK / 404 NOT FOUND |

---

Header `richiesta`:

| Campo header  | Descrizione |
| ---- | ---- |
| User-Agent | informazioni sul browser (versione) e la piattaforma (PC, desktop) |
| Accept | tipi di pagine che puo gestire |
| Accept-Charset | es UTF8 |
| Accept-Ecoding | che encoding usa |
| Accept-Language | il inguaggio natura che gestisce |
| If-Modified-Since | risponde solo se è modificato dalla data |
| Host | nome del DNS |
| Authorization | per mettere utente-password |
| Referrer | SE richiesta arriva da richiesta precedente |
| Cookie | per informazioni di stato |

---

Header `risposta`:

| Campo header | Descrizione |
| ---- | ---- |
| Server | info sul server |
| Content-.. | informazioni sul contenuto |
| Last-Modified |  |
| Expires | da quando non è piu valida la pagina |
| Location | per redirect |

Gli header non standard hanno della forma $X-...$
Header e body sono delimitati da linea vuota
Il body termina con linea vuota