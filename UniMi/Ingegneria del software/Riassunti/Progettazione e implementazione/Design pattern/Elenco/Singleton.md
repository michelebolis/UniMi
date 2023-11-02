Si vuole avere un oggetto con una sola istanza
Approccio lazy: ritardare la creazione dell oggetto

Prevediamo un costruttore privato e un metodo statico getInstance che permetta di restituire l'unica istanza
Tuttavia tale soluzione non è sicura dal punto di vista della concorrenza

La soluzione è di usare @Synchronized nel metodo getInstance, che implica un controllo se qualcuno ha gia il lock sul metodo della classe

La soluzione migliore dal punto di vista delle prestazione è di usare @Synchronized SOLO dentro all if del null facendo poi nuovamente il controllo, double check

![[Pasted image 20231101110239.png]]

Idioma Java:
Si usa un enumerativo con un unico valore. Quando lo utilizzo per la prima volta, la creazione è thread safe grazie alla VM e otteniamo un unico oggetto accessibile, condiviso e immutabile

```java
public enum MySingleton {
    INSTANCE;

    public void metodoIstanza() { ... }
}

MySingleton.INSTANCE.sampleOp();
```