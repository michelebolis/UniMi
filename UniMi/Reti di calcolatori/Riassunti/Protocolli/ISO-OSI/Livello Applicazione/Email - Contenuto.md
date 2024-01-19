Per permettere l'invio di diversi materiali multimediali, si utilizza il protocollo `MIME - Multipurpose Internet Mail Extension`

Header

| Campo | Descrizione |
| ---- | ---- |
| Content-Description | descrizione testuale |
| Content-Type | definisce il tipo di contenuto del body ; Boundary = "delimitatore" |
| Content-Transfer-Encoding | la codifica utilizzata |
| Content-length |  |

Type è nel formato Tipo/sottotipo es Text/Plain o Multipart/Mized quando allego qualcosa
La [[Codifica Base64]] è usata per mandare blocchi di dati in binario, aumentando pero la dimensione del messaggio