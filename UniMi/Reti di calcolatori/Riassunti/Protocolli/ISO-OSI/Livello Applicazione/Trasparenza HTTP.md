Trasparenza tra 1 e 2 nell URL e nella porta utilizzata
E' il client HTTP che determina SE il server supporta HTTP/2
- Richiesta con GET / HTTP / 1.1; Connetion: Upgrade, HTTP2-Settings; Upgrade: h2c; HTTP2-Settings: ...
SOLO i server che supportano HTT2 comprendono HTTP2-Settings
- SE NON supporta: ritorna 200 OK
- SE lo supporta risponde sempre con HTTP 1.1 MA Connetion: Upgrade, Upgrade: h2c