OSS piu è grande l'intervallo scartato all'iterazione $k$, e piu risultano piccoli quelli scartabili all'iterazione $k+1$
`L'iterazione di massima efficacia è quella che consente di scartare metà dell'intervallo di incertezza`, valutando due punti interni distinti vicinissimo tra loro (a distanza $\epsilon$)
Tuttavia all'iterazione successiva il primo e il terzo intervallo sarebbero larghi solo $\epsilon$, quindi si avrebbe un'`iterazione di minima efficacia`

![[Pasted image 20240401103542.png|250]]

`Si vuole quindi compiere l'iterazione di massima efficacia per ultima`, quindi si vuole avere come ultima iterazione due punti $a^{n-1}$ e $b^{n-1}$ distanti $\epsilon$
Si ha perciò
$$I^{n-1}=2I^n-\epsilon$$
Dalle due relazioni
$$I^k = I^{k+1}+I^{k+2},\forall k \geq 0$$
$$I^{n-1}=2I^n-\epsilon$$
Si ricava 
$$I^{n-2} = I^{n-1}+I^n=3I^n-\epsilon$$
$$...$$
$$I^{n-k}=I^{n-k+1}+I^{n-k+2}=F_{k+2}I^n-F_k\epsilon, \forall k \geq 1$$
$$...$$
$$I^0=I^1+I^2=F_{n+2}I^n-F_n\epsilon$$
Perciò
$$I^0=F_{n+2}I^n-F_n\epsilon$$
$$I^n=\frac{I^0}{F_{n+2}}+\frac{F_n}{F_{n+2}}\epsilon$$
Dalla relazione soprastante e dal requisito di incertezza finale 
$$I^n\leq \bigtriangleup$$
Si ricava il `numero di iterazioni necessarie`
$$\overline{n} = \min\{n|\frac{I^0}{F_{n+2}}+\frac{F_n}{F_{n+2}}\epsilon \leq \bigtriangleup\}$$
OSS il secondo addendo è moltiplicato per $\epsilon$ piccolo, quindi in realta bisogna minimizzare il primo addendo
`Formula di Binet`: lega $n$ al numero di Fibonacci di $n$
$$F_n=\frac{1}{\sqrt{5}}((\frac{1+\sqrt{5}}{2})^n-(\frac{1-\sqrt{5}}{2})^n)$$
Una volta trovato $n$, sappiamo quali siano i punti da scegliere
$$I^\overline{n}=\frac{I^0}{F_{\overline{n}+2}}+\frac{F_\overline{n}}{F_{\overline{n}+2}}\epsilon$$
$$I^1 = F_{\overline{n}+1}I^\overline{n}-F_{\overline{n}-1}\epsilon$$
Ricavo $I^1$ in funzione di $I^0$
$$I^1 = F_{\overline{n}+1}(\frac{I^0}{F_{\overline{n}+2}}+\frac{F_\overline{n}}{F_{\overline{n}+2}}\epsilon)-F_{\overline{n}-1}\epsilon =$$
$$= \frac{F_{\overline{n}+1}}{F_{\overline{n}+2}}I^0+\frac{\epsilon}{F_{\overline{n}+2}}(F_{\overline{n}+1}F_\overline{n}-F_{\overline{n}+2}F_{\overline{n}-1}) =$$
$$= \frac{F_{\overline{n}+1}}{F_{\overline{n}+2}}I^0 + \frac{\epsilon}{F_{\overline{n}+2}}(-1)^{\overline{n}-1}$$
