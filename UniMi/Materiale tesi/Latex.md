Preambolo:
`\title{...}`,  `\author{...}` e `\date{...}` servono per il maketitle

Tra `\begin{document}` e `\end{document}` c'è il documento vero e proprio
`\maketitle` usa le info del preambolo
Per formule matematiche `$$` o `$$$$`
`\begin{enumerate/itemize} .. \end{enumerate/itemize}` permette di avere una lista con gli elementi identificati con `\item`
Stessa cosa in generale con le sezioni del documento numerate denotate da `\section{nameSection}`
Per aggiungere immagini: 
- `\usepackage{graphicsx}`, carico l immagini nella cartella, e la aggiungo con `\includegraphics[scale=0.5]{nameImage}`
- Stessa cosa ma uso `\begin{figure} ... \end{figure}`
Opzioni posizioni immagini
- `\begin{figure}[h]` h=here permette di renderizzare l immagine dove l ho scritta
- `\begin{figure}[ht]` ht=here and top if possible
- `\begin{figure}[b]` b=bottom

Formattazione
- Grassetto: `\textbf{textToBold}`
- Italic `\textit{text}`

Si puo far riferimento a un contenuto con una `label{text}` e poi utilizzare il riferimento con `\ref{text}`
Per centrare un contenuto `\begin{center} ... end{center}`

Tabular `\begin{tabular} ... \end{tabular}` è una tabella senza contorni solo linee verticali tra colonne
Table `\begin{table} ... \end{table}`
Per la descrizione delle tabelle `\caption{Description}` dentro la table

Per aggiungere un nota che deve apparira a fondo pagina, nel testo dove deve apparire la ref, `\footnote{text}`
SE la stessa nota appare piu volte, uso `\footnotemark` e poi `\footnotetext{text}`

Per aggiungere un indice dei contenuti `\tableofcontents`
Per aggiungere un indice anche delle figure `\listoffigures`

Per la bibliografia creo un file `ref.bib` e poi nel mio file .tex uso `\bibliography{ref}`
MA per farle apparire devo prima citarle nel testo usando `\cite{...}`