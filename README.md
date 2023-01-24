# Florida Tech/CMS `baposter` LaTeX template
The original baposter class (Version 1) was created by Brian Amberg (baposter@brian-amberg.de).  Florida Tech and CMS Collaboration-style LaTeX template for a conference poster presentation made by Stephen D. Butalla (stephen.butalla@cern.ch). Version 0, 2021/10/03.

If you want modify and/or distribute the class/template,
please refer to the [CC BY-NC-SA 3.0 license](http://creativecommons.org/licenses/by-nc-sa/3.0/).

# Quick TeX formatting tips

## Creating a section of the poster
 To create a section for the `\headerbox` command, use
 ```
\headerbox{Title of section}{name=section_name, column=X, row=Y, span=Z, below=section_name_below, bottomaligned=section_to_align_with}{

}
```
**Required parameter descriptions:**

* `name`: The identifier of the section. Used to align other boxes.
* `column`: The column number (indexed from zero)
* `row`: The starting row number (indexed from zero)
* `span`: The number of **columns** that the section spans, as measured from the `column` number to the right (left to right)

**Optional parameter descriptions:**
* `below`: the name of the section that the current section is below. One can also use `above` in a similar manner.
* `bottomaligned`: the name of the section to horizontally align the current section with.

## Figures
The normal figure environment does not work with this template (**including figure referencing**). A figure is added with the normal `\includegraphics`
command, *inside* of the `center` environment. One needs to use the `\captionof` command placed *below* the figure, e.g.,

```

\begin{center}
  \includegraphics[width=0.6\linewidth]{your_figure.pdf}
  \captionof{figure}{Caption of the figure.}
\end{center}
```

## Wrapping text around a figure
To wrap text, use the `\wrapfigure` environment:

```
\begin{wrapfigure}{r}{0.5\linewidth}
  \begin{center}
    \includegraphics[width=0.6\linewidth]{your_figure.pdf}
    \captionof{figure}{Caption of the figure.}
  \end{center}
\end{wrapfigure}
```
The first argument of `\wrapfigure` is the location of the figure with respect to the wrapped text [`r` for placing the figure on the right (with text on the left),
and `l`for placing the figure on the left (with text on the left)]. The second argument is the size of the text column.

## Writing text/figures to multiple columns
For multiple columns inside of the poster section, use the `multicols` environment, e.g.,

```
\begin{multicols}{X}{width}

\end{multicols}
```
where `X` is the number of columns and `width` is the width of an individual column (e.g., `0.5\linewidth` for two columns, `0.33\linewidth` for three columns, etc.).
