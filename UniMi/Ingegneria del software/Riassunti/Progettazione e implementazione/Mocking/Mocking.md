Approccio al testing: 
- metodo restituisce un valore: assert sui risultati di un metodo
- metodo che modifica lo stato: uso il method e poi uso un getter 
- metodo che modifica lo stato MA usando altri metodi di altre classi (dependent component):
	- il mio oggetto chiede dell'input (indirettamente testo anche la correttezza dei componenti che utilizza; se il risultato è sbagliato non sapro da dove provenga l errore)
	- il mio oggetto non attua cambiamento al suo stato, ma a quello di un altro oggetto, quindi devo usare un test che verifichi lo stato del dependent component

Il problema è che magari il componente esterno non è ancora stato implementato, non restituisca risultati deterministici
Può risultare assai difficile testare un SUT che dipende da componenti software non utilizzabili, depended-on component (DOC).

Il mocking è la tecnica di testing che ci permette di sostituire i DOC reali con i vari [[Test Double]]. Effettuare mocking permette di ottenere test più efficienti, affidabili e puliti, consentendo agli sviluppatori di isolare il SUT in un ambiente più controllato.

In generale per ogni test ci deve essere un unica `new` per il SUT e tutti i restanti DOC devono essere mockati

- [[Dummy Object]]
- [[Stub Object]]
- [[Mock Object]]
- [[Spy Object]]
- [[Fake Object]]

[[Mockito]]