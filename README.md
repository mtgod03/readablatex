# readablatex

## Usage

### `\ENV` command

The `\ENV` command makes $\LaTeX$ environments brief. Using this command, you can also write

```latex
\begin{envname}[options]
  % Contents comes here.
\end{envname}
```

as

```latex
\ENV<envname>([options]) {
  % Contents comes here.
}
```

#### Examples

```latex
% By usual LaTeX nonation
\begin{equation}
  f(x) = ax^2 + bx + c
\end{equation}

% With \ENV command
\ENV<equation> {
  f(x) = ax^2 + bx + c
}
```

```latex
% By usual LaTeX nonation
\begin{figure}[h]
  \centering
  \includegraphics{sample.png}
  \caption{Sample}
  \label{fig:sample}
\end{figure}

% With \ENV command
\ENV<figure>([h]) {
  \centering
  \includegraphics{sample.png}
  \caption{Sample}
  \label{fig:sample}
}
```

### `\BLOCK` command

The `\BLOCK` command makes chapters, sections, etc. more readable. Using this command, you can also write

```latex
\headingcommand{headingname}
Contents comes here.
```

as

```latex
\BLOCK<headingcommand>(headingname) {
  Contents comes here.
}
```

#### Examples

```latex
% By usual LaTeX nonation
\section{Sample}
This is a sample section.

% With \BLOCK command
\BLOCK<section>(Sample) {
  This is a sample section.
}
```
