Nei linguaggi OO, gli oggetti hanno dei metodi ad essi collegati MA anche uno stato il quale causa l impossibilità di testare i metodi in modo isolato

Problematiche
- Nelle sottoclassi è necessario testare nuovamente tutti i metodi ereditati, rieseguendo i casi di test anche nelle sottoclassi
- Testare le classi astratte è come testare una classe non completa: si potrebbero prevedere delle implementazioni dei metodi astratti dummy
- Il collegamento dinamico complica poi la determinazione dei criteri di copertura (es non si possono piu stabilire staticamente tutti i cammini)  

Le tecniche devono quindi spostarsi dalle procedure alle classi

[[Tecniche per OO - Class Testing]]
[[Tecniche per OO - Criteri di copertura]]