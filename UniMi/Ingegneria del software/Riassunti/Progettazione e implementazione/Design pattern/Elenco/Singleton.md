si vuole avere un oggetto e non una classe
Approccio lazy: ritardare la creazione dell oggetto
...
Brutta soluzione: NON è thread safe
Soluzione: usare syncronized nel metodo getInstance, che implica un controllo se qualcuno ha gia il lock sul metodo della classe
Problema: non è ottimale dal punto di vista delle prestazioni
Soluzione: usare syncronized SOLO dentro all if del null facendo poi nuovamente il controllo: double check

ATTTTTT In Java non facciamo cosi

Idioma Java con cui si fa Singleton:
...

usando un enumerabile, quando lo utilizzo la prima volta la creazione è thread safe grazie alla VM e otteniamo quello che volevamo: un unico oggetto accessibile, condiviso e immutabile
