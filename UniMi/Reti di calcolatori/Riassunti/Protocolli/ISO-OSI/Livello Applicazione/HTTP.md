HTTP Hyper Text Transfer Protocol
E' utilizzato oggi non solo per gli hyper text ma oggi anche per la parte di API REST
Da HTTP/1 a HTTP/2 utilizzano TCP
HTTP/3 invece usa CUIC-UDP

- HTTP/1.0 1996 da Berners-Lee RFC-1945
- HTTP/1.1 1997 RFC-2068
- HTTP/2 2015 RFC-7540
- HTTP/3 2022 RFC-9114

HTTPS quando si usano socket TLS
TLS Transport Layer Security: quando c è una richiesta HTTP, si chiede all entita TCP/UDP mentre con TLS HTTP passa prima per TLS, che aggiunge un proprio header, e poi si passa a TCP/UDP

HTTP e HTTPS incompatibili

[[HTTP 1.X]]

Cookie
Sono piccoli file che il server invia al client al fine di memorizzare informazioni che serviranno in seguito
Nella risposta c è Set-Cookie: cookie1=...; cookie2=...;
settati come chiave=valore

Quando il client effettua una richiesta, nell'header invia anche i Cookie


HTTP schema
...

[[HTTP 1.1]]
[[HTTP 2]]

[[Trasparenza HTTP]]
HTTP 3 gestisce piu efficientemente le funzionalita del 2 demandando a CUIC e utilizzando UDP
