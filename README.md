# latex-thesis-template
A LaTeX template for a bachelor thesis

## How to
Il file principale è `MyThesis.tex`, all'interno di questo si devono convogliare tutti gli altri `.tex` che si troveranno nella cartella Chapters ed eventualmente FrontBackMatter tramite il comando `\input{path}`, il cui argomento è il percorso per arrivare al file interessato. `\input{./Chapters/chap1.tex` inserisce quanto presente nel file `chap1.tex` della cartella Chapters. All'interno del file principale si ha la struttura del documento riportata di seguito.

### Struttura del documento
FRONTMATTER
- [ ] Frontespizio
- [x] Dedica
- [x] Sommario
- [x] Indice generale
- [x] Ringraziamenti
MAINMATTER
- [x] Introduzione numerata
- [x] Capitoli centrali
- [x] Conclusioni
BACKMATTER
- [ ] Appendici
- [x] Bibliografia
- [ ] Indice analitico

Per inserire soltanto l'elenco delle figure usare il seguente codice presente nel file `ToC.tex`
```
\cleardoublepage
\begingroup
\renewcommand*{\addvspace}[1]{} % looks better
% ---------- List of Figures ------------
\pdfbookmark{\listfigurename}{listoffigures} % place the bookmark
\listoffigures % print the LoF
% ---------- List of Tables -------------
%\cleardoublepage % if there's LoF behind
%\pdfbookmark{\listtablename}{listoftables} % place the bookmark
%\listoftables % print the LoT
% ---------------------------------------
\endgroup
```
Analogamente per inserire soltanto l'elenco delle tabelle; rimuovere tutti i commenti per averli entrambi.

### Scrittura
Nel testo, ogni capoverso è automaticamente indentato. Usare i comandi `\smallskip \medskip \bigskip` per dare eventuale spazio tra un capoverso e l'altro. Utilizzare il comando `\noindent` per annullare l'indentatura. Di seguito si dà uno spazio nel secondo capoverso:
```
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.

Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.\par\medskip

Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
```
Altre soluzioni per dare spazio verticare sono `\\[lenght]` la cui lunghezza è opzionale e `\vspace{length}`. Le unità di misura che si consiglia di utilizzare sono il centimetro `cm` e il millimetro `mm`, il punto `pt`, il pollice `in`, la larghezza di una x `ex` e la larghezza di una M `em`.

Le virgolette si inseriscono con le seguenti ` ''testo`` `.

Utilizzare solo in caso di necessità il grassetto `\textbf{text}`, quando si vuole evidenziare un parola si ricorre al corsivo tramite `\emph{text}`. Parole non nella lingua del documento (Italiano) devono essere scritte in corsivo, usare `\engemph{text}` per parole in lingua Inglese. Il comando `\omissis` stampa il simbolo di omissione di una parte del testo quando si cita.

Per generare del testo fittizio usare `\lipsum`, per averne meno `\lipsum[1]` oppure `\lipsum[1-3]` ecc.

### Capitoli e livelli inferiori
```
\chapter{Chapter name}\label{ch:}
\section{Section name}\label{sc:}
\subsection{Subsection name}\label{subsc:}
\subsubsection{Subsubsection name}
\paragraph{Paragraph name}
```

### Riferimenti incrociati
Il comando `\ref{label}` stampa il numero del label, da usare così `si veda il paragrafo~\ref{sc:par1} per maggiori informazioni`. Il comando `\vref{label}` ha lo stesso funzionamento del precedente ma oltre al numero del riferimento stampa il numero di pagina al quale si trova.

### Elenchi
Elenco puntato
```
\begin{itemize}
\item text;
\begin{itemize}
\item text;
\item text.
\end{itemize}
\item text;
\item text.
\end{itemize}
```
Elenco numerato
```
\begin{enumerate}
\item text;
\begin{enumerate}
\item text;
\item text.
\end{enumerate}
\item text;
\item text.
\end{enumerate}
```
Descrizione
```
\begin{description}
\item[First item] \lipsum[1][1-2].
\item[Second item] \lipsum[1][3-4].
\item[Third item] \lipsum[1][5-6].
\end{description}
```

Qualora si volesse ridurre localmente lo spazio verticale tra gli item di un elenco, agire sul parametro `itemsep` e qualora si volesse ridurre ulteriormente dare una valore negativo oppure agire sull'altro parametro `parsep`; per modificare lo spazio che separa gli elementi dell'elenco dal margine sinistro della gabbia di testo usare il parametro `leftmargin`. Con il parametro `label` si modifica il label di ogni elemento
```
\begin{itemize}[itemsep=val,parsep=val,leftmargin=val,label=]
\item text.
\end{itemize}
```
È possibile azzerare lo spazio verticale oltre che tra gli elementi, prima e dopo l'elenco passando il parametro `nosep`. Si possono modificare gli elenchi globalmente ad esempio tramite `\setlist[itemize]{key=val}` nel preamble, per comodità al di sotto del pacchetto `enumitem` usato.

### Oggetti flottanti
#### Figure
Una sola figura
```
\begin{figure}
\centering
\includegraphics[key=val]{path}
\caption{caption}
\label{fig:}
\end{figure}
```
Quattro figure, nel caso se ne volesse 2 o 3 commentare dove non si vogliono avere altre immagini
```
\begin{figure}
\centering
\subfloat[][\emph{subcaption}\label{subfig:}]
 {\includegraphics[key=val]{path}} \quad
\subfloat[][\emph{subcaption}\label{subfig:}]
 {\includegraphics[key=val]{path}} \\
\subfloat[][\emph{subcaption}\label{subfig:}]
 {\includegraphics[key=val]{path}} \quad
\subfloat[][\emph{subcaption}\label{subfig:}]
 {\includegraphics[key=val]{path}}
\caption{maincaption}
\label{fig:}
\end{figure}
```
L'argomento obbligatorio di `\includegraphics{path}` deve contenere il percorso della figura che si vuole inserire, si consiglia di utilizzare la cartella Figures per contenerle. Lo spazio orizzontale può essere variato sostituendo `\,` a `\quad` per uno spazio minore, oppure `\qquad` per uno spazio maggiore. Per quanto riguarda lo spazio verticale, può essere variato tramite l'argomento opzionale di `\\[length]`.

Per modificare le dimensioni di una figura si agisce su tre parametri chiave-valore nell'argomento opzionale del comando `\includegraphics[width=val,height=val,scale=val]{path}`, si consiglia di scegliere tra uno dei possibili:
- larghezza: per comodità si definisce relativamente alla larghezza del testo `width=0.7\textwidth` in questo caso il 70%
- altezza: per comodità si può definire relativamente alla larghezza del testo `height=0.3\textwidth`
- fattore di scala: si aumentano o si riducono le dimensioni attraverso un fattore `scale=0.5` riduce le dimensioni del 50%

#### Tabelle
Nelle tabelle la didascalia e il rispettivo label si trovano sopra. I tipi di colonna `l c r` riguardano l'allineamento interno della colonna. Un altro tipo possibile è `p{length}` il cui argomento è la larghezza della colonna espressa in una certa unità di misura oppure relativamente alla larghezza del testo `\textwidth`, il testo in questa colonna viene giustificato e sillabato automaticamente.

Tabella con due colonne
```
\begin{table}
\caption{caption}
\label{tab:}
\begin{tabular}{ll}
\toprule
intestazione & intestazione \\
\midrule
testo & testo \\
\bottomrule
\end{tabular}
\end{table}
```
Tabella con due colonne a larghezza prefissata, il tipo di colonna `X` calcola automaticamente la larghezza della stessa e si usa quando nella colonna le celle contengono testo che non sia un'unica parola. Per comodità la larghezza della tabella si definisce relativamente alla larghezza del testo della pagina. `0.5\textwidth` significa che la larghezza della tabella è metà di quella della gabbia del testo.
```
\begin{table}
\caption{caption}
\label{tab:}
\begin{tabularx}{\textwidth}{lX}
\toprule
testo & \lipsum[1-4] \\
\midrule
testo & \lipsum[1-4] \\
\bottomrule
\end{tabularx}
\end{table}
```

### Bibliografia
Il file `MyThesis.bib` è il database bibliografico nel quale inserire le citazioni, ognuna con il relativo id univoco. Lo stile di citazione impostato è IEEE, schema di citazione e bibliografica numerici. Un altro stile possibile è autore-anno secondo lo stile Chicago, andare nel preamble del file principale per saperne di più.

Comandi utili per le citazioni all'interno del testo, `bibid` è identifica ciascuna citazione
```
\cite{bibid}
\textcite{bibid}
\citeauthor{bibid}
\citeyear{bibid}
```
Esempio `come dimostrato da~\textcite{bibid} ecc`.
