`Standard BIOAPI`: lo standard BIOAPI già dal 2000 contiene tutte le specifiche di interazioni tra i moduli che compongono un sistema biometrico.
`Fornisce un modello di autenticazione ad alto livello per ogni tecnologia biometrica presente sul mercato`.

Include le specifiche delle funzionalità di :
- Verifica
- Identificazione
- Enrollement
- Interfaccia di interazione con il DB, in modo tale da permettere al biometric service provider di gestire i template nel db in modo ottimale

`BSP` è un termine generale che indica il `modulo che gestisce le funzionalità biometriche verso i moduli HW e i layer software necessari alle unità`.

BIOAPI inoltre fornisce le `primitive di gestione dei sistemi biometrici distribuiti`:
Permette alle applicazioni di gestire le acquisizioni dei campioni. Gestire l'acquisizione su un modulo client e l'enrollment, identification e verification su un modulo server.