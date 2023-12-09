E' necessario permettere di lavorare tra due reti con indirizzi di livello diverso
1. Dual protocols
Sono presenti host con IPv4 e altri con IPv6. Il server ha sia un protocollo IPv4 e IPv6  in modo che riesca a leggere il campo version dei vari pacchetti e passare i pacchetti al corretto IP

2. Dual stacks and tunneling
Per interconnettere reti con rispettivamente IPv4 e IPv6, è necessario che il server, avendo sia un protocollo IPv4 che IPv6, applichi un tunneling dell'IPv6 in un IPv4

3. Translators
Alla ricezione di un pacchetto IPv6/IPv4, questo viene convertito in un pacchetto IPv4/IPv6 grazie a una NAT con un PT Protocol Translator

SE la NAT è utilizzata come gateway della rete, allora è una NAT-PT gateway
Per l'assegnazione degli IPv4, solitamente la NAT alloca un certo numero di HostId per le destinazioni da un pull, applicando un timeout a tali indirizzi