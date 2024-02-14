Fra i filtraggi iniziali usati di solito in genere troviamo:
- `Contrast stretching`:
Le immagini delle impronte digitali hanno di solito dei toni di grigio molto limitati. L'operazione di contrst stretching `allarga la dinamica dell'immagine`.
![[Pasted image 20231106103853.png]]
Ogni pixel viene rimappato, ottenendo un `maggiore contrasto`. Andiamo di conseguenza ad `distribuire la distribuzione dei grigi nell'immagine`.

- `Histogram manipulation`:
L'istogramma di una immagine può essere mappato in un altro istogramma mediante diverse funzioni. Ad esempio il logaritmo permette di evidenziare delle variazioni sottili di toni di grigio in una immagine che aveva già una dinamica elevata.

`Un istogramma è prendere un pixel alla volta ed aumentare i bin che contiene tutti i pixel con un certo valore`, da 0 a 255 se usiamo la codifica a 8 bit.

`Filtraggio più ottimizzato` rispetto a prima, non andiamo ad aumentare solo il minimo e il massimo.

- `Wiener filtering `:
`Quando si conoscono le caratteristiche spettrali dell'immagine e del rumore` si usa il filtro di wiener.
Permette di andare ad `attenuare il rumore ed ad amplificare il segnale` che ci serve, agendo su ogni pixel.

- `Normalization`:
L'obiettivo della normalizzazione è quello di `standardizzare le variazioni di grigio dei ridge` in tutta l'immagine, per agevolare gli algoritmi successivi.

Andiamo in questo modo a gestire la variabilità tra le immagini  (con diverso contrasto) che un sensore può catturare, in questo modo gli algoritmi successivi possono lavorare con meno casi possibili.

`L'algoritmo prende un pixel alla volta e lo porta ad un valore fissato di media e varianza nell'immagine finale`.

Non equivale ad una equalizzazione dell'istogramma, in quanto il filtraggio può essere programmato per lavorare anche localmente.

Una volta che abbiamo un immagine standardizzata, possiamo andare ad eseguire la `segmentazione`, estraendo dall'immagine solamente i ridge che mi servono :
Un algoritmo di segmentazione divide ciò che non ci interessa (background) da quello che ci interessa (foregorund). I `ridge vengono identificati in quanto in un intorno locale presentano una varianza di toni di grigio molto alta`.

L'immagine viene divisa in blocchi (ad esempio $16*16$), viene calcolata la varianza locale  tra i toni del grigio del blocco e vengono scartati i blocchi sotto ad una soglia prefissata.
- Blocco troppo piccolo: troppe poche informazioni, non riesco a calcolare la varianza
- Blocco troppo grande: non riesco  a definire bene il contorno dei componenti dell'immagine che mi servono.

Inoltre un impronta/immagine generica, presenta delle regioni con diversa qualità :
Diversa qualità dovuta a :
- Diversa pressione
- Tagli, abrasioni
- Uso non corretto

DI solito si distinguono le regioni che compongono l'immagine in 3 categorie
- Well-defined
- Recoverable
- Unrecoverable ( un AI non può inventarsi delle caratteristiche non esistenti)