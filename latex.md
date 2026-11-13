# LaTeX for Technical Writing

## 1. Introduction
LaTeX is a document preparation system used for academic and technical writing. I write content and formatting instructions in a `.tex` source file, compile it, and obtain a formatted document, usually a PDF. It is useful for assignments, reports, research papers, equations, tables, figures and references.

**Source note:** The supplied Doxygen lecture says that LaTeX fundamentals were covered earlier, but the separate LaTeX lecture slides were not included. This page is an introductory summary of common LaTeX concepts.

## 2. Basic document structure
A LaTeX document has a preamble and a document body. The preamble defines the document class and packages. The body contains the actual content.

```latex
\\documentclass[12pt,a4paper]{article}
\\usepackage{graphicx}
\\usepackage{amsmath}

\\title{My Technical Report}
\\author{Student Name}
\\date{\\today}

\\begin{document}
\\maketitle

\\section{Introduction}
This is the introduction.

\\section{Conclusion}
This is the conclusion.
\\end{document}
```

The `\\documentclass` command selects the document type. Packages add features. `\\maketitle` displays the title information.

## 3. Common document classes
| Class | Common use |
|---|---|
| `article` | Assignments, short reports and papers |
| `report` | Longer reports with chapters |
| `book` | Books and long documents |
| `letter` | Formal letters |
| `beamer` | Slide presentations |

## 4. Sections and text formatting
Use `\\section`, `\\subsection` and `\\subsubsection` to create a heading hierarchy.

```latex
\\textbf{Bold text}
\\textit{Italic text}
\\underline{Underlined text}
\\emph{Emphasized text}
```

## 5. Lists
```latex
\\begin{itemize}
  \\item First point
  \\item Second point
\\end{itemize}

\\begin{enumerate}
  \\item First step
  \\item Second step
\\end{enumerate}
```
`itemize` creates bullet points, while `enumerate` creates numbered points.

## 6. Mathematical equations
Inline mathematics is placed between `$` symbols. Displayed equations can use the `equation` environment.

```latex
The area of a circle is $A = \\pi r^2$.

\\begin{equation}
E = mc^2
\\end{equation}
```

The `amsmath` package provides useful environments such as `align`.

```latex
\\begin{align}
a^2 + b^2 &= c^2 \\\\
x &= \\frac{-b \\pm \\sqrt{b^2-4ac}}{2a}
\\end{align}
```

## 7. Tables and images
A simple table can be created with `tabular`.

```latex
\\begin{tabular}{|c|c|}
\\hline
Subject & Marks \\\\
\\hline
TW & 90 \\\\
\\hline
\\end{tabular}
```

To insert an image, load `graphicx`.

```latex
\\begin{figure}[h]
  \\centering
  \\includegraphics[width=0.6\\textwidth]{diagram.png}
  \\caption{System diagram}
  \\label{fig:system}
\\end{figure}
```

## 8. Labels and references
Labels let LaTeX refer to numbered sections, figures and tables without manually typing their numbers.

```latex
\\section{Methodology}
\\label{sec:method}
As explained in Section~\\ref{sec:method}, ...
```

A bibliography can be managed using a `.bib` file and a bibliography tool. The exact workflow depends on the template and compiler. Sources must be cited consistently.

## 9. Compilation workflow
1. Create a `.tex` file.
2. Add the document structure and content.
3. Compile it using a LaTeX distribution or online editor.
4. Check the generated PDF.
5. Correct errors and compile again.

TeX Live and MiKTeX are common local distributions. Overleaf is a browser-based editor.

## 10. Good practices
- Use meaningful headings and a clear document hierarchy.
- Keep the preamble organized and include only required packages.
- Use labels and references instead of manually typing numbers.
- Give figures and tables captions.
- Compile regularly and proofread the final PDF.

## 11. What I learned
LaTeX separates content from much of the formatting. It is useful for long technical documents because equations, figures and references can be kept consistent. Learning the syntax takes practice, but the structure is valuable for academic writing.
