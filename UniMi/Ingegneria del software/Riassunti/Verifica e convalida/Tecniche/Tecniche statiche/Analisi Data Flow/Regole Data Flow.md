L'uso di una variabile deve sempre essere preceduto in ogni sequenza da una definizione SENZA annullamenti intermedi
La definizione di una variabile deve sempre essere seguita da un uso prima di un suo annullamento o definizione
L'annullamento di una variabile deve essere sempre seguito da una definizione prima di un uso o di altro annullamento

|     | a   | d   | u   |
| --- | --- | --- | --- |
| a   | ERR |     | ERR |
| d   | ERR | ERR |     |
| u    |     |     |     |

La classificazione della violazione di queste regole in warning o error dipende dal linguaggio