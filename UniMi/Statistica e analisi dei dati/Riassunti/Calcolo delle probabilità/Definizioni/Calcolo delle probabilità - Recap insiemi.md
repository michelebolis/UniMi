Diagrammi di Venn: rettangolo è l'insieme universo, $\Omega$, mentre un generico elemento sarà un esito e contenuto in un cerchio rappresentante l'evento $E$

Operazioni:
- Unione: $\forall E, F, e \in (E \cup F) \iff e \in E \vee e \in F$
	- L'evento $E \cup F$ contiene gli esiti dell'evento $E$ e gli esiti dell'evento $F$
		$E \cup F$ si verifica quando si verifica $E$ oppure si verifica $F$
- Intersezione: $\forall E, F, e \in (E \cap F) \iff e \in E \wedge e \in F$
	- L'evento $E \cap F$ si verifica solo se entrambi gli eventi $E$ e $F$ si verificano
- Sottrazione: $\forall E, F e \in  (E - F) \iff e \in E \wedge e \notin F$
	- L'evento $E - F$ si verifica solo se $E$ si verifica ed $F$ non si verifica
	- $\Omega-E$ si verifica quando non si verifica $E: \overline E$ complemento di $E$
 
OSS minuscole per gli esiti, maiuscole per eventi

L'evento vuoto, $\emptyset$, per definizione non si verifica mai, evento impossibile
$\Omega \subseteq \Omega --> \Omega$ è un evento con la particolarità che si verifica sempre, evento certo

Concetto di sottoinsieme
$E \subseteq F$ quando $\forall e \in E \implies e \in F$
$E \subseteq F$ quando si verifica l'evento $E \implies$ si verifica F ($E \implies F$)

$E = F \iff E \subseteq F \wedge F \subseteq E$

È possibile estendere unione e intersezione a piu di due eventi, considerando quindi l'unione degli Ei questo si verifica se almeno uno degli eventi Ei si verifica mentre l'intersezione degli Ei si verifica SOLO SE tutti gli eventi Ei si verificano

Proprieta dell'unione e dell'intersezione
- Commutatività
	- $A \cup B = B \cup A$
	- $A \cap B = B \cap A$
- Associatività
	- $A \cup (B \cup C) = (A \cup B) \cup C$ //non vi è priorita nell'ordine delle operazioni
	- $A \cap (B \cap C) = (A \cap B) \cap C$
- Distributività
	- $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$
	- $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$

Leggi de Morgan
- $\overline{(A \cup B)} = \overline A \cap \overline B$, l'evento che si verifica quando non si verifica A o B è lo stesso evento che si verifica quando non si verifica A e non si verifica B

DIM
$\forall e \in \overline{(A \cup B)} \iff e \in \overline A \cap B$
$e \notin (A \cup B) \implies e \notin (A \cup B) \implies e \notin A \wedge e \notin B \implies e \in \overline A \wedge \overline B \implies e \in \overline A \cap \overline B$
Abbiamo dimostrato che $\overline{(A \cup B)} \subseteq \overline A \cap \overline B$
Si puo rifare lo stesso ragionamento al contrario per dimostrare l'altra implicazione per dimostrare $\overline A \cap \overline B$ sottoinsieme $\overline{(A \cup B)}$

- !(A ∩ B) = !A U !B
