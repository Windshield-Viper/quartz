## Getting started

Here is what you need to get started:

```latex
\documentclass{article}
\begin{document}
First document. This is a simple example, with no 
extra parameters or packages included.
\end{document}
```

- The first line of code declares the `document` class, which can be a CV, resume, or [more](https://www.ctan.org/topic/class)
- After that, the content of the document is written between the `begin` and `end` tags

## Making a basic preamble

- The preamble of the document is the "setup" section.

A minimal preamble could look like this:
```latex
\documentclass[12pt, letterpaper]{article}
\usepackage{graphicx}
```

- Note how square brackets are used to set additional parameters for the `documentclass` instance (which, in this case, is `article`)
	- In this case, we set the font size and the paper size
	- [Further info about page size and margins](https://www.overleaf.com/learn/latex/Page_size_and_margins)
- The line `usepackage{graphicx}` is loading an external package

## Including title, author, and date info

Like this:
```Latex
\documentclass[12pt, letterpaper]{article}
\title{My first LaTeX document}
\author{Hubert Farnsworth\thanks{Funded by the Overleaf team.}}
\date{August 2022}
```
- `\thanks` is optional and is to thank an institution.
- To typeset the title, use the `\maketitle` command inside the body of the document.

## Example of a simple document


```latex
\documentclass[12pt, letterpaper]{article}
\title{My first LaTeX document}
\author{Hubert Farnsworth\thanks{Funded by the Overleaf team.}}
\date{August 2022}
\begin{document}
\maketitle
We have now added a title, author and date to our first \LaTeX{} document!
\end{document}
```


## Comments, bolds, italics, underlines

- Comments - use a `%` sign before any comment 
	- Example: `% this is a comment`
- **Bold**: bold text in LaTeX is typeset using the `\textbf{…}` command.
- _Italics_: italicised text is produced using the `\textit{…}` command.
- <ins>Underline</ins>: to underline text use the `\underline{…}` command.

Example:
```latex
Some of the \textbf{greatest}
discoveries in \underline{science} 
were made by \textbf{\textit{accident}}.
```

- Another useful one is `\emph`, which italicizes unitalicized things but does the reverse for italicized things.

## Adding images

```latex
\documentclass{article}
\usepackage{graphicx} %LaTeX package to import graphics
\graphicspath{{images/}} %configuring the graphicx package
 
\begin{document}
The universe is immense and it seems to be homogeneous, 
on a large scale, everywhere we look.

% The \includegraphcs command is provided (implemented) by the graphicx package
\includegraphics{universe}  
 
There's a picture of a galaxy above.
\end{document}
```
- Putting graphics into a LaTeX document needs an add-on package. Above, `graphicsx` is used.
- Keep in mind that any image used needs to be uploaded.

## Adding captions, labels, and references to images

- This can be done through the `figure` environment.

```latex
\documentclass{article}
\usepackage{graphicx}
\graphicspath{{images/}}
 
\begin{document}

\begin{figure}[h]
    \centering
    \includegraphics[width=0.75\textwidth]{mesh}
    \caption{A nice plot.}
    \label{fig:mesh1}
\end{figure}
 
As you can see in figure \ref{fig:mesh1}, the function grows near the origin. This example is on page \pageref{fig:mesh1}.

\end{document}
```

- _Noteworthy commands used in this example_
	- `\includegraphics[width=0.75\textwidth]{mesh}`: This form of `\includegraphics` instructs LATEX to set the figure’s width to 75% of the text width—whose value is stored in the `\textwidth` command.
	- **`\caption{A nice plot.}`**: As its name suggests, this command sets the figure caption which can be placed above or below the figure. If you create a list of figures this caption will be used in that list.
	- **`\label{fig:mesh1}`**: To reference this image within your document you give it a label using the `\label` command. The label is used to generate a number for the image and, combined with the next command, will allow you to reference it.
	- **`\ref{fig:mesh1}`**: This code will be substituted by the number corresponding to the referenced figure.

- Images put in a LaTeX document should be put in a `figure` environment so they can be positioned.
- More info found here:
	- [Positioning of figures](https://www.overleaf.com/learn/latex/Positioning_images_and_tables)
	- [Inserting images](https://www.overleaf.com/learn/latex/Inserting_Images)


## Making lists
- Lists can be made using _environments_, which encapsulate the code needed to implement a specific feature.
 
### Unordered lists
- Produced by the `itemize` environment.
- Basically just bullet points
```latex
\documentclass{article}
\begin{document}
\begin{itemize}
  \item The individual entries are indicated with a black dot, a so-called bullet.
  \item The text in the entries may be of any length.
\end{itemize}
\end{document}
```

### Ordered lists
- Same syntax, just using the `enumerate` environment
```latex
\documentclass{article}
\begin{document}
\begin{enumerate}
  \item This is the first entry in our list.
  \item The list numbers increase with each entry we add.
\end{enumerate}
\end{document}
```

## Adding math
- There are two ways to do this - 
	- _Inline math mode – used for writing formulas that are part of a paragraph
	- _Display math mode_ - used for writing expressions that are not part of a text or paragraph and are typeset on separate lines

### Inline math mode
```latex
\documentclass[12pt, letterpaper]{article}
\begin{document}
In physics, the mass-energy equivalence is stated 
by the equation $E=mc^2$, discovered in 1905 by Albert Einstein.
\end{document}
```

- To typeset inline-mode math you can use one of these delimiter pairs: 
	- `\( … \)`
	- `$ … $` 
	- `\begin{math} … \end{math}`
### Display math mode
- Equations in display mode can be numbered or not.
```latex
\documentclass[12pt, letterpaper]{article}
\begin{document}
The mass-energy equivalence is described by the famous equation
\[ E=mc^2 \] discovered in 1905 by Albert Einstein. 

In natural units ($c = 1$), the formula expresses the identity
\begin{equation}
E=m
\end{equation}
\end{document}
```
- To typeset display-mode math use these delimiter pairs:
	- `\[ … \]`
	- `\begin{displaymath} … \end{displaymath}`
	- `\begin{equation} … \end{equation}`



## Online resources for math syntax in LaTeX

Resources:
- [Mathematical expressions](https://www.overleaf.com/learn/latex/Mathematical_expressions "Mathematical expressions")
- [Subscripts and superscripts](https://www.overleaf.com/learn/latex/Subscripts_and_superscripts "Subscripts and superscripts")
- [Brackets and Parentheses](https://www.overleaf.com/learn/latex/Brackets_and_Parentheses "Brackets and Parentheses")
- [Fractions and Binomials](https://www.overleaf.com/learn/latex/Fractions_and_Binomials "Fractions and Binomials")
- [Aligning Equations](https://www.overleaf.com/learn/latex/Aligning_equations_with_amsmath "Aligning equations with amsmath")
- [Operators](https://www.overleaf.com/learn/latex/Operators "Operators")
- [Spacing in math mode](https://www.overleaf.com/learn/latex/Spacing_in_math_mode "Spacing in math mode")
- [Integrals, sums and limits](https://www.overleaf.com/learn/latex/Integrals%2C_sums_and_limits "Integrals, sums and limits")
- [Display style in math mode](https://www.overleaf.com/learn/latex/Display_style_in_math_mode "Display style in math mode")
- [List of Greek letters and math symbols](https://www.overleaf.com/learn/latex/List_of_Greek_letters_and_math_symbols "List of Greek letters and math symbols")
- [Mathematical fonts](https://www.overleaf.com/learn/latex/Mathematical_fonts "Mathematical fonts")

## Document structure (abstracts, paragraphs, chapters)

### Abstracts
- Use `\begin{abstract}` and `\end{abstract}

### Paragraphs and line breaks
- Make a new paragraph by pressing the "enter" key twice. 
- Start a new line without making a new paragraph by inserting a manual line break using the `\\` command
- Or use the `\\newline` command for the same thing.
```latex
\documentclass{article}
\begin{document}

\begin{abstract}
This is a simple paragraph at the beginning of the 
document. A brief introduction about the main subject.
\end{abstract}

After our abstract we can begin the first paragraph, then press ``enter'' twice to start the second one.

This line will start a second paragraph.

I will start the third paragraph and then add \\ a manual line break which causes this text to start on a new line but remains part of the same paragraph. Alternatively, I can use the \verb|\newline|\newline command to start a new line, which is also part of the same paragraph.
\end{document}
```

### Chapters and sections
- Primarily uses the `\chapter` and `\section` commands
- All commands:
	- `\part{part}`
	- `\chapter{chapter}`
	- `\section{section}`
	- `\subsection{subsection}`
	- `\subsubsection{subsubsection}`
	- `\paragraph{paragraph}`
	- `\subparagraph{subparagraph}`
```latex
\documentclass{book}
\begin{document}

\chapter{First Chapter}

\section{Introduction}

This is the first section.

Lorem  ipsum  dolor  sit  amet,  consectetuer  adipiscing  
elit. Etiam  lobortisfacilisis sem.  Nullam nec mi et 
neque pharetra sollicitudin.  Praesent imperdietmi nec ante. 
Donec ullamcorper, felis non sodales...

\section{Second Section}

Lorem ipsum dolor sit amet, consectetuer adipiscing elit.  
Etiam lobortis facilisissem.  Nullam nec mi et neque pharetra 
sollicitudin.  Praesent imperdiet mi necante...

\subsection{First Subsection}
Praesent imperdietmi nec ante. Donec ullamcorper, felis non sodales...

\section*{Unnumbered Section}
Lorem ipsum dolor sit amet, consectetuer adipiscing elit.  
Etiam lobortis facilisissem...
\end{document}
```

## Creating tables

### A basic table
```latex
\begin{center}
\begin{tabular}{c c c}
 cell1 & cell2 & cell3 \\ 
 cell4 & cell5 & cell6 \\  
 cell7 & cell8 & cell9    
\end{tabular}
\end{center}
```
- `tabular` is the default method to create tables
	- a parameter needs to be specified to it (in this case, is was `{c c c}` for 3 centered columns) that tells LaTeX how many columns there will be and how to align them
	- `c` makes centered columns, `r` is for right-aligned, and `l` is for left-aligned
	- To end a table row use the _new line_ command `\\`.
	- Our table is contained within a `center` environment to make it centered within the text width of the page.

### Adding borders
- to add horizontal rules, above and below rows, use the `\hline` command. You can use the command more than once for a double line.
- to add vertical rules, between columns, use the vertical line parameter `|`
```latex
\begin{center}
\begin{tabular}{|c|c|c|} 
 \hline
 cell1 & cell2 & cell3 \\ 
 cell4 & cell5 & cell6 \\ 
 cell7 & cell8 & cell9 \\ 
 \hline
\end{tabular}
\end{center}
```

### Captioning tables
- Tables can be captioned in the same way as images. The only difference is that instead of the **`figure`** environment, you use the **`table`** environment
```latex
Table \ref{table:data} shows how to add a table caption and reference a table.
\begin{table}[h!]
\centering
\begin{tabular}{||c c c c||} 
 \hline
 Col1 & Col2 & Col2 & Col3 \\ [0.5ex] 
 \hline\hline
 1 & 6 & 87837 & 787 \\ 
 2 & 7 & 78 & 5415 \\
 3 & 545 & 778 & 7507 \\
 4 & 545 & 18744 & 7560 \\
 5 & 88 & 788 & 6344 \\ [1ex] 
 \hline
\end{tabular}
\caption{Table to test captions and labels.}
\label{table:data}
\end{table}
```
## Other
### Making a table of contents
- Use the `\tableofcontents` command. 
```latex
\documentclass{article}
\title{Sections and Chapters}
\author{Gubert Farnsworth}
\date{August 2022}
\begin{document}
  
\maketitle
  
\tableofcontents

\section{Introduction}
   
This is the first section.
      
Lorem  ipsum  dolor  sit  amet,  consectetuer  adipiscing  
elit.   Etiam  lobortisfacilisis sem.  Nullam nec mi et 
neque pharetra sollicitudin.  Praesent imperdietmi nec ante. 
Donec ullamcorper, felis non sodales...
       
\section*{Unnumbered Section}
\addcontentsline{toc}{section}{Unnumbered Section}

Lorem ipsum dolor sit amet, consectetuer adipiscing elit.  
Etiam lobortis facilisissem.  Nullam nec mi et neque pharetra 
sollicitudin.  Praesent imperdiet mi necante...

\section{Second Section}
       
Lorem ipsum dolor sit amet, consectetuer adipiscing elit.  
Etiam lobortis facilisissem.  Nullam nec mi et neque pharetra 
sollicitudin.  Praesent imperdiet mi necante...
\end{document}
```

[CTAN - where packages are distributed](https://www.ctan.org/)