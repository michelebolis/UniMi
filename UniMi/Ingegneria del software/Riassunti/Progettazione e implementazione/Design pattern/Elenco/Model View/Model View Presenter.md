| Passaggi                                                                                                                                                               | Rappresentazione                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------ |
| L'utente interagisce con una vista che passa le chiamate ad un Presenter che manipola il Model, che as sua volta chiama gli eventi del Presenter che aggiorna la vista | ![[Pasted image 20231206102650.png]] |

Ci permette di `spezzare la catena circolare` di dipendenze in modo da rendere semplice il testing.
Si introduce un intermediario, il Presenter, e cio ci permette di isolare l'interfaccia logica da quella grafica (design for testing)