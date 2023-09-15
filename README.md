# ReadabLaTeX

ReadabLaTeX is an extension of $\LaTeX$'s notation.

In my opinion, LaTeX's notation is redundunt and not readable. Using ReadabLaTeX enables you to write LaTeX documents briefly and readably.

- **Readable**: Surrounding environments by `{}` instead of `\begin` and `\end` makes your documents more brief and readable.
- **Flexible**: You can use ReadabLaTeX partially as well as fully.
- **Compatible**: As ReadabLaTeX is just a LaTeX package, every LaTeX command can of course be used together with ReadabLaTeX.

## Basic Usage

With ReadabLaTeX, the following two documents

```latex
\documentclass{article}
\usepackage{readablatex}

\title{ReadabLaTeX Example}
\author{someone}
\date{\today}

\ENV<document> {
  \maketitle

  \BLOCK<section>(Sample Section) {
    First, I write usual text.
    Second, I write a nested list.
    \ENV<itemize> {
      \item First Item
      \item Second Item
      \ENV<itemize> {
        \item 2-1
        \item 2-2
      }
    }
    Finally, I write an equation.
    \ENV<equation> {
      S_n = \sum_{k=1}^n a_k
    }
  }
}
```

and

```latex
\documentclass{article}
\usepackage{readablatex}

\title{ReadabLaTeX Example}
\author{someone}
\date{\today}

\+<document> {
  \maketitle

  \+<section>(Sample Section) {
    First, I write usual text.
    Second, I write a nested list.
    \+<itemize> {
      \item First Item
      \item Second Item
      \+<itemize> {
        \item 2-1
        \item 2-2
      }
    }
    Finally, I write an equation.
    \+<equation> {
      S_n = \sum_{k=1}^n a_k
    }
  }
}
```

are the same as

```latex
\documentclass{article}

\title{ReadabLaTeX Example}
\author{someone}
\date{\today}

\begin{document}

\maketitle

\section{Sample Section}

First, I write usual text.
Second, I write a nested list.
\begin{itemize}
  \item First Item
  \item Second Item
  \begin{itemize}
    \item 2-1
    \item 2-2
  \end{itemize}
\end{itemize}
Finally, I write an equation.
\begin{equation}
  S_n = \sum_{k=1}^n a_k
\end{equation}

\end{document}
```

## Commands

### `\ENV` command

The `\ENV` command makes $\LaTeX$ environments brief.

Using this command, you can write

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

The `\BLOCK` command makes chapters, sections, etc. more readable.

Using this command, you can write

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

### `\+` command

The `\+` command is the integrated shorthand of `\ENV` and `\BLOCK`.

For example, this command enables you to write

```latex
\section{Quadratic Function}
The following is an example of quadratic function.
\begin{equation*}
  f(x) = ax^2 + bx + c
\end{equation*}
```

as

```latex
\+<section>(Quadratic Function) {
  The following is an example of quadratic function.
  \+<equation*> {
    f(x) = ax^2 + bx + c
  }
}
```
