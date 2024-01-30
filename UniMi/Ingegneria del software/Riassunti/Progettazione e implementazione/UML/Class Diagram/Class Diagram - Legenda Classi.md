Gli oggetti sono distinguibili in `Classi` e `Interfacce`, identificate rispettivamente dalle lettere `C` e `I`. Vi sono anche le `classi astratte` e gli `enum` (lettere `A` e `E`)
![[Pasted image 20231213101738.png]]
![[Pasted image 20231213102408.png]]
- I metodi delle classi sono rappresentate da un cerchio
- Gli attributi sono rappresentati da un quadrato
Visibilità attributo: 
- pubblico: verde
- protected: giallo
- private: rosso

Font:
- In corsivo vengono rappresentati gli `oggetti non concreti` (ATT classe che implementa un metodo in corsivo, sarà presente nell'UML in quanto ha tale metodo come concreto)
	- Per essere concreto: NON devo avere metodi astratti
	- Per essere astratto: non c è un vincolo in quanto nonostante abbia tutti i metodi concreti potrei decidere di restare astratta
- La sottolineatura indica un `metodo/attributo è statico` (ovvero ha una visibilità a livello di classe e non a livello di istanza)
- \<\<stereotipo>> ovvero un nuovo elemento introdotto che può essere un attributo o un’interfaccia ad esempio, per questo specifico _use-case_ che permette di estendere UML.