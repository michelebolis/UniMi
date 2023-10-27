pattern con cui pensiamo i pattern, identifica due elementi base
- HookMethod: metodo astratto che determina il comportamento specifico nelle sottoclassi
	- Punto caldo in cui si puo intervenire per personalizzare, adattare lo schema 
- TemplateMethod: metodo che coordina generalmente piu hook method
	- Punto freddo di invaribilità del pattern

Come si relazionano hook e template
- Unification: template e hook sono nella stessa classe del framework
- Connection: template e hook sono in classi separate tra di loro collegate da una associazione
- Recursive connection: template e hook sono in classi tra di loro collegate anche tramite relazione di generalizzazione
