Le problematiche inerenti al problema della rappresentazione nel sistema biometrico per la parte di matching `impattano solamente il modulo di matching`, il quale è presente solamente nelle fasi di verification e identification.

Dobbiamo andare a `definire una metrica nello spazio delle feature`, la quale permette di misurare la distanza tra due template per determinare se essi siano simili o meno.

Esempio di matching fra impronte, input e templare :
- Template in ingresso: in ingresso vengono passata le coordinate minuitae e le loro angolazioni
- Vengono eseguite delle rototraslazioni per allineare le 2 mappe attorno ad una minutia.
- Vengono individuate le coppie di minutae corrispondenti nelle 2 mappe
- Calcolo delle distanze e dell'indice di matching

Tutta le impronte di uno stesso individuo potrebbero essere raccolte con deformazioni (troppa pressione sul sensore) le distanze relative alle minutiae cambiano e quindi diventa difficile avere un buon valore di matching. Possiamo dunque adottare delle contro misure :
- Prendere provvedimenti per evitare che l'utente deformi l'impronta durante la scansione
- Inserire nell'algoritmo di matching anche un modello elastico di deformazione, tutta via aumenta la similitudine intraclasse ma tende a diminuire la distanza interclasse.

Domande esame
- Come il problema della rappresentazione della informazione in un sistema biometrico consista nello stabilire quale rappresentazione “machine readable” catturi completamente l’informazione invariante e discriminatoria della misura in ingresso
- Come questo possa essere visto in termini di distanza interclasse ed intraclasse nello spazio delle feature
- Soluzioni al problema della rappresentazione dei sistemi biometrici
	- Del sample
	- Della estrazione delle feature
	- Del template
- Come il modulo di matching implementi una metrica nello spazio delle feature