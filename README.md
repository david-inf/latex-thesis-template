# latex-thesis-template
 A LaTeX template for a bachelor thesis

# How to

## Chapters and other levels
```
\chapter{}\label{ch:}
\section{}\label{sc:}
\subsection{}\label{subsc:}
\subsubsection{}
\paragraph{}
```

## Lists
Bullet points
```
\begin{itemize}
\item
\begin{itemize}
\item
\item
\end{itemize}
\item
\item
\end{itemize}
```
Now numbered
```
\begin{enumerate}
\item
\begin{enumerate}
\item
\item
\end{enumerate}
\item
\item
\end{enumerate}
```
Description of some things
```
\begin{description}
\item
\item
\item
\end{description}
```

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

## Bibliography
