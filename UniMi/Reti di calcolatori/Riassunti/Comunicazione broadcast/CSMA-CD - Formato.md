Formato dei frame

| Campo            | Dimensione | Descrizione                                                                                                                |
| ---------------- | ---------- | -------------------------------------------------------------------------------------------------------------------------- |
| SFD              | `10101011`   | `Start Of Frame Delimiter` indica l'inizio                                                                                   |
| MAC Dest | 48 bit     |                                                                                                                            |
| MAC Sour     | 48 bit     |                                                                                                                            |
| Type/length      | 16 bit     | SE questa lunghezza è minore del minimo richiesto per un frame valido, allora viene aggiunta una sequenza di byte, padding |
| Data             |            |                                                                                                                            |
| FCS              | 32 bit     | contiene un CRC value per rilevare l errore                                                                                |


![[Pasted image 20231219133605.png|500]]
