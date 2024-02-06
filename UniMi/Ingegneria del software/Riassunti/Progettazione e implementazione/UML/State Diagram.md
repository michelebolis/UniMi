`Gli automi a stati finiti vengono mappati dallo State Diagram` rendendoli compatibili con il dominio applicativo degli UML, le classi.

I rettangoli rappresentano gli `oggetti`.
Le frecce rappresentano relazioni tra classi/oggetti in particolare sono 
- `eventi` SE si considera cosa provoca quella transizione, cioe quale metodo della classe viene chiamato
- `azione`: SE si considera cosa esegue quella transizione, quindi quali operazioni vengono fatte verso l'esterno
Le azioni sono conseguenza degli eventi: l'evento `restituisci()` causa l'azione `book.restituisci(this)`


| Azioni/Eventi                                                                                  | Rappresentazione                     |
| ---------------------------------------------------------------------------------------- | ------------------------------------ |
| Azioni                                                                                    | ![[Pasted image 20231206091845.png]] |
| Azioni interne allo stato: dipendono esclusivamente dallo stato                                                                | ![[Pasted image 20231206091910.png]] |
| Guardie: disambiguare transizioni causate da uno stesso evento e uscenti da stesso stato (gli automi a stati finiti non sono deterministici) | ![[Pasted image 20231206092219.png]] |
| Time event, After (duration): Indica una durata massima di permanenza nello stato                    |                                      |
| Change event, When (condizione): La condizione è espressa in termini di valori degli attributi                                                                                         |                                      |

Il verificarsi di eventi non esplicitamente marcati da un arco deve portare alla terminazione dell’esecuzione e al sollevamento di un errore, questo significa che sono situazioni che **non devono accadere**, differentemente dagli automi a stati finiti, in cui la mancanza di archi indicava una situazione che **non potevano accadere**.

[[Superstate Diagram]]