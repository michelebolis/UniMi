Formato frame

| Campo            | Dimensione | Descrizione                                        |
| ---------------- | ---------- | -------------------------------------------------- |
| DAddress/SAddress            | 48 bit     |                                                    |
| VLAN protocol ID | 16 bit     | settato a `8100Hex`                                  |
| PRI              | 3 bit      |                                                    |
| CFI              | 1 bit      |                                                    |
| VLAN identifier  | 12 bit     | permette l'identificazione della VLAN del mittente |
| length           | 16 bit     | lunghezza del payload                              |
| FCS              | 32 bit     |                                                    |

![[Pasted image 20231219134144.png]]
