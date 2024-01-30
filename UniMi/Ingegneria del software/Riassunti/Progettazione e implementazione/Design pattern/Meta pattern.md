I `meta pattern` sono pattern con cui pensiamo i pattern: identificano due elementi base
- `HookMethod`: metodo astratto che `determina il comportamento specifico nelle sottoclassi`
	- Punto caldo in cui si puo intervenire per personalizzare, adattare lo schema 
- `TemplateMethod`: metodo che `coordina generalmente piu hook method`
	- Punto freddo di invariabilità del pattern

Come si relazionano hook e template

| Metodo | Spiegazione | es |
| --- | --- | --- |
| `Unification` | template e hook sono nella stessa classe astratta| |
|`Connection` | template e hook sono in classi separate (rispettivamente concreta e astratta) tra di loro collegate da una associazione|![[Pasted image 20231101090817.png]] |
| `Recursive connection` | template e hook sono in classi tra di loro collegate anche tramite relazione di generalizzazione: la classe template dipende  | ![[Pasted image 20231101090915.png]]|
