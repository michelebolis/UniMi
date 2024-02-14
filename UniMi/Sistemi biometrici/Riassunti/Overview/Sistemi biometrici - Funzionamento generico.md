Funzionamento Generico sistema biometrico basato sull'impronta digitale
Possiamo considerare i sistemi biometrici come sistemi di `pattern recognition` ( non è presente la fase di coding).

Si struttura in due fasi principali :
- `Enrollment`: corrisponde alla `fase di inserimento`. Il tratto biometrico viene per la prima volta acquisito dal sistema e registrato oppure viene creato il documento biometrico.
- `Identificazione / verifica`: corrisponde alla `fase di riconoscimento`. Il tratto biometrico viene nuovamente acquisito. Se risulta sufficientemente aderente alle informazioni registrate nel sistema biometrico l'accesso è consentito.

Schema del funzionamento :
![[Pasted image 20231106092049.png]]
- `Acquisition`: l'impronta digitale viene acquisita.
- `Feature extraction`: dall'impronta vengono una serie di tratti distintivi
- `Coding`: vengono "codificati " e salvati nel database.
- Può essere stabilità una certa soglia, se il `matching` è al di sotto della soglia l'utente non è abilitato ad utilizzare il sistema.