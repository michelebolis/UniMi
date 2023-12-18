E' un protocollo pensato per richiesta-risposta da client a server 
Tutto in ASCII
Formato dei messaggi
- header: composto da N linee simboleggiate da un \\n
	- prima linea distingue richiesta e risposta
		- Richiesta: \<metodo HTTP> \<URL> \<versioneProtocollo> 
		- es GET /index.html HTTP/1.1 (metodi: GET/POST/PUT/DELETE/...)
		- Risposta: \<codice> \<testo del codice>
		- es 200 OK / 404 NOT FOUND
	- Header per la richiesta
		- User-Agent: informazioni sul browser (versione) e la piattaforma (PC, desktop)
		- Accept: tipi di pagine che puo gestire
		- Accept-Charset: es UTF8
		- Accept-Ecoding: che encoding usa
		- Accept-Language: il inguaggio natura che gestisce
		- If-Modified-Since: risponde solo se è modificato dalla data
		- Host: nome del DNS
		- Authorization: per mettere utente-password
		- Referrer: SE richiesta arriva da richiesta precedente
		- Cookie: per informazioni di stato
	- Header per la risposta
		- Server: info sul server
		- Content-..: informazioni sul contenuto
		- Last-Modified
		- Expires: da quando non è piu valida la pagina
		- Location: per redirect
	- Header user defined X-...
- body
Header e body delimitati da linea vuota
Body termina con linea vuota