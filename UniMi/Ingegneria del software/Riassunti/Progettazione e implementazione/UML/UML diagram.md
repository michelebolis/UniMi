UML diagram
Freccia: relazione tra classi/oggetti
- freccia bianca tratteggiata da classe a interfaccia: la classe implementa l'interfaccia
- freccia nera tratteggiata da classe a classe / da classe a interfaccia: la classe ha una dipendenza rispetto all'altra
- freccia con rombo da classe a classe: legame tra istanze, (se bidirezionale non metto la freccia)
	- associazione, 
	- aggregazione (rombo bianco): legato a qualcosa di esterno che mi definisce
		Metodo implementativo: l'attributo
	- composizione (rombo nero): deve essere un contenimento fisico. Requisiti
		- L'oggetto contenuto deve essere presente nella SOLA classe contenente 
		- La vita dell oggetto contenuto sia legata al contenente 
		Metodo implementativo: classe statica inner
	minimo..massimo di istanze

corsivo: oggetto non concreto (ATT classe che implementa un metodo in corsivo, sarà presente nell UML in quanto ha tale metodo come concreto)
Per essere concreto: NON devo avere metodi astratti
Per essere astratto: non c è un vincolo in quanto nonostante abbia tutti i metodi concreti potrei decidere di restare astratta

\<\<stereotipo>>
sottolineatura: quando un metodo/attributo è statico 

Attributo: 
- pubblico: verde
- protected: giallo
- private: rosso
