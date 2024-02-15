`È possibile sapere a priori i punti dove la curva DET passerà` ( esame)
Se faccio una soglia che è +infinto, nessun impostore passerà come nessun genuino ( la curva passa da +infinito e -infinito 1 0 e 0 1 ).
`La soglia adatta è quindi quella che viene attraversata dalla bisettrice`.  
L'`EER - Equal error rate è l'unico numero singolo che può riassumere il funzionamento del sistema FNMR = FMR`. 

![[Pasted image 20231106100529.png|300]]

Abbiamo diverse zone di funzionamento in base alla realtà che vogliamo modellare :

| FNMR alto  | FMR basissimo quasi zero | Alto livello di sicurezza   |
| ---------- | ------------------------ | --------------------------- |
| FNMR basso | FMR alto                 | Applicazioni forensi        |
| Bisettrice |                          | Applicazioni civili normali |

La `Curva ROC` è l'analogo di DET. $ROC = 1 - DET$
ROC Esprime `quanti genuini sono riusciti correttamente ad entrare`. 
![[Pasted image 20231106100609.png|300]]

La curva ROC e la curva DET mostrano la stessa informazione ma si focalizzano su punti di vista differenti. Riferendosi ad autenticazione positiva :
- La curva DET mostra quanti genuini non passano FNMR
- La curva ROC mette in mostra quanti genuini passano