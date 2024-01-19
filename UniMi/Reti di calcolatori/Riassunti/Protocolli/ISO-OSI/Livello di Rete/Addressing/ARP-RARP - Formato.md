
formato pacchetti 802.3

| Campo            |  Bytes   | Note    |
| ----------- | --- | --- |
| DA          | 6   |     |
| SA          | 6   |     |
| Type/lenght | 2   | 0806 = ARP    |

formato pacchetto ARP/RARP

| Campo                   | bit  |                                                                     |
| ----------------------- | ---- | ------------------------------------------------------------------- |
| HW type                 | 16   | specifica il tipo di indirizzo MAC                                  |
| Protocol Type           | 16   | indica il tipo di indirizzo di rete usato (es per IP è 0800 in HEX) |
| Operation               | 16   | di seguito le opzioni possibili                                                                    |
| Operation: ARP request  | 0001 |                                                                     |
| Operation: ARP reply    | 0002 |                                                                     |
| Operation: RARP request | 0003 |                                                                     |
| Operation: RARP reply   | 0004 |                                                                     |
| Sender MAC address      | 16   | MAC del gateway                                                     |
| Sender IP address       | 16   |                                                                     |
| Target MAC address      | 16   |                                                                     |
| target IP address       | 16   |                                                                     |

![[Pasted image 20231219092315.png|500]]