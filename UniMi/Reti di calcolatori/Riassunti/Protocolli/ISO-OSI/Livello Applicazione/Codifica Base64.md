I file allegati sono file binari che possono contenere qualsiasi cosa e quindi non abbiamo controllo sui possibili caratteri (potrebbe contenere \\n o un boundary)
Si attua quindi una codifica Base64
I caratteri ammessi in Base64 sono un sottoinsieme di quello ASCII

Vantaggio: ogni bit non andrà a interferire con i caratteri speciali delle mail

Procedimento: si prende lo stream di bit, lo si converte in gruppi da 6 bit (si fa eventualmente padding con il carattere = (0111101) ), lo si riporta al carattere ASCII e infine lo si converte ai bit corrispondenti

es
Codifica

| Fase                                                                            | bit                                                                     |
| ------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| Input                                                                           | 10010101110111000011101101011000                                        |
| Divido in gruppi da 8 bit                                                       | 10010101 11011100 00111011 01011000                                     |
| Aggiungiamo come padding (00111101) per avere il numero di bit divisibile per 6 | 10010101 11011100 00111011 01011000 00111101 00111101                   |
| Dividiamo in gruppi da 6 bit:                                                   | 100101 011101 110000 111011 010110 000011 110100 111101                 |
| Passiamo in esadecimale (es 100101 -> 10 0101 -> 25)                            | 25 1D 30 3B 16 03 34 3D                                                 |
| Codifico l'HEX nel carattere della tabella                                      | `l` `d` `w` `7` `W` `D` `0` `9`                                         |
| Riporto in bit i caratteri usando la codifica ASCII (primo bit sempre a 0)      | 01101100 01100100 01110111 00110111 01010111 01000100 00110000 00111001 |

Da 32 bit mandiamo 64 bit

Decodifica

| Fase                                        | bit                                                                     |
| ------------------------------------------- | ----------------------------------------------------------------------- |
| Input                                       | 0110110001100100011101110011011101010111010001000011000000111001        |
| Divido in gruppi da 8 bit                   | 01101100 01100100 01110111 00110111 01010111 01000100 00110000 00111001 |
| Converto da bit ad ASCII                    | `l` `d` `w` `7` `W` `D` `0` `9`                                         |
| Usando la tabella, converto in HEX          | 25 1D 30 3B 16 03 34 3D                                                 |
| Converto da HEX a binario                   | 100101 011101 110000 111011 010110 000011 110100 111101                 |
| Divido in gruppi da 8 bit                   | 10010101 11011100 00111011 01011000 00111101 00111101                   |
| Tolgo il padding SE gruppo è 00111101 (0 =) | 10010101 11011100 00111011 01011000                                     |

