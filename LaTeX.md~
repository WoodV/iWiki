### LaTex

*Basing on [LaTeX-Tutorial.com](https://www.latex-tutorial.com/tutorials/)*

#### Overview:

.tex file contains two parts: command and actual text.

##### Command:

(We can think it as functions or reseaved words)

	* Starts with `\`
	* Format: `\commandname{option}
	* Environment:
		* Environment is a block of your document with certain typesetting rules.
		* Structure:
		```
		\begin{environment1}
		  \begin{environment2}
		  \end{environment2}
		\end{environment1}
		```
		* {document} is the highest enviroment.

##### Structure:

```
\documentclass{article}

\usepackage{PackageName}

\title{Title}
\author{Author}

\begin{document}
  \maketitle

\section{sectionName}

Text

\subsection{subsectionName}

Text

\subsubsection{subsubsectionName}

Text

\paragraph{paragraphName}

\subparagraph{subparagraphName}

  
\end{document}
```

Actual text starts from `\begin{document}`, everything above that are _preambles_, they can be used by the commands within the `document` environment.

*Section* will be automatically numbered and will be appeared in the table of contents, *Paragraph* won't.

##### Math and Equations:

* $EQUATIONS$ - `$` tells LaTeX to use math feature for text within it.
* \\ - linebreak
* `equation`, `align` - environment
* `int^a_b` for integral symbol
* `frac{u}{v}` for fractions
* `sqrt{x}` for square roots
* `matrix` - environment for matrix
```
\left[
\begin{matrix}
1 & 0\\
0 & 1
\end{matrix}
\right]
```

##### Images & Figures

Use `figure` environment and `graphicx` package.

#### Useful Commands:

* `\maketitle`
* `\newpage`
* `\pagenumbering{gobble\arabic\roman}` - no numbers\arabic numbers\roman numbers
* `\usepackage{PackageName}`
* `equation` - an environment that format math equations. With numbering.
* `equation\*` - same as `equation`, without numbering.
* `align[*]` - similar to `equation`, but make equations align at `&` marked places.
'''
	1 + 2 &= 3 \\
	1 &= 3 - 2
'''


#### Useful Packages:

* `amsmath` - provide `equation\*` environment and others.

