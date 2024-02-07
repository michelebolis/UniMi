- Assioma `1`: `monotonicità rispetto alla marcatura iniziale`

`Tutti i tempi di scatto` di una sequenza di scatto devono essere `non minori di uno qualunque dei timestamp dei gettoni della marcatura iniziale`
La marcatura deve essere consistente cioè `non deve contenete gettono prodotti in futuro`

- Assioma `2`: `monotonicità dei tempi di scatto di una sequenza `

`Tutti i tempi di scatto di una sequenza di scatti devono essere ordinati nella sequenza in maniera monotonicamente non decrescente`.
La consistenza si ha dalla proprietà intuitiva che il `tempo non torna indietro`
Due o piu transizioni possono scattare nello stesso istante modellando quindi azioni concorrenti simultanee

- Assioma `3`: `divergenza del tempo / non zenonicità`

Non è possibile avere un `numero infinito di scatti in un intervallo di tempo finito`
La consistenza si ha dalle proprietà intuitive del tempo per cui il tempo non si può fermare e non è suddivisibile in infinitesimi

- Assioma `4`: `marcatura forte iniziale`

`Il massimo tempo di scatto di tutte le abilitazioni nella marcatura iniziale deve essere maggiore o uguale del massimo timestamp associato ad un gettone della marcatura`

La marcatura iniziale DEVE essere consistente con la nuova semantica
`Il gettone con timestamp maggiore del massimo non avrebbe potuto essere creato a un istante successivo a quel timestamp senza che prima fosse scattata la transizione`

- Assioma `5`: `sequenza di scatti forte` 

Una sequenza di scatti MWTS che parte da una marcatura forte iniziale, è una sequenza di scatti forte SE `per ogni scatto il tempo di scatto della transizione non è maggiore del massimo tempo di scatto di un altra transizione abilitata`