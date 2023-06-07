# latex-thesis-template
 A LaTeX template for a bachelor thesis

# How to

## Floating objects
### Figures
Just one graphic
```
\begin{figure}
\centering
\includegraphics[]{}
\caption{caption}
\label{fig:}
\end{figure}
```
Multiple (four here) graphics
```
\begin{figure}
\centering
\subfloat[]{\emph{}]
 {\includegraphics[]{}} \quad
\subfloat[]{\emph{}]
 {\includegraphics[]{}} \\
\subfloat[]{\emph{}]
 {\includegraphics[]{}} \quad
\subfloat[]{\emph{}]
 {\includegraphics[]{}}
\caption{}
\label{fig:}
\end{figure}
```

### Tables
Simple two column table
```
\begin{table}
\caption{}
\label{tab:}
\begin{tabular}{ll}
\toprule
& \\
\midrule
& \\
\bottomrule
\end{tabular}
\end{table}
```
