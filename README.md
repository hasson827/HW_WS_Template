# HW_WS_Template

A lightweight LaTeX class for creating math worksheets with an optional answer key. One source file generates both student and instructor versions.

## Features

- **Single source**: One `.tex` file generates both student and answer versions
- **Toggle answers**: Use `[answers]` option to show/hide answers
- **Auto headers**: Automatic page headers with course/institution info
- **Smart spacing**: `\blankspace` shows space in student version, hides in answer version
- **Sub-questions**: `parts` environment for a), b), c) numbering
- **Clean styling**: Blue question labels (Q1, Q2...), red answer labels
- **Page numbers**: Automatic page numbering in footer
- **No paragraph indent**: Clean left-aligned text

## Quick Start

```latex
\documentclass{worksheet}  % Student version
% \documentclass[answers]{worksheet}  % Answer version

\coursename{Linear Algebra}
\coursecode{Math 257}
\institution{Your University}
\professor{Prof. Name}
\semester{Fall 2026}
\wsnumber{1}

\begin{document}
\makeworksheettitle

\begin{question}
    What is $2+2$?
    \blankspace{5em}
\end{question}

\begin{answer}
    The answer is 4.
\end{answer}

\end{document}
```

## Commands

| Command | Description |
|---------|-------------|
| `\coursename{...}` | Set course name |
| `\coursecode{...}` | Set course code |
| `\institution{...}` | Set institution |
| `\professor{...}` | Set professor name |
| `\semester{...}` | Set semester |
| `\wsnumber{...}` | Set worksheet number |
| `\makeworksheettitle` | Generate the title |
| `\blankspace{length}` | Add space (hidden in answer version) |

## Environments

```latex
% Question environment
\begin{question}
    Question text...
\end{question}

% Question with subtitle
\begin{question}[Bonus]
    Question text...
\end{question}

% Parts (sub-questions)
\begin{parts}
    \item Part a
    \item Part b
    \item Part c
\end{parts}

% Answer environment
\begin{answer}
    Answer text...
    % Parts also work inside answers
    \begin{parts}
        \item Answer to part a
        \item Answer to part b
    \end{parts}
\end{answer}
```

## Comparison with System `homework` Class

TeX Live includes a `homework` class with different styling:

| Feature | `worksheet.cls` (This) | System `homework` |
|---------|----------------------|-------------------|
| Question label | Q1, Q2, Q3 (blue) | Problem 1, 2, 3 |
| Answer label | Answer: (red) | Solution (underlined) |
| Title position | Center | Top-right corner |
| QED symbols | None | Square markers |
| Page numbers | Bottom center | Bottom-right corner |
| Toggle answers | `[answers]` option | `[hide-solution]` option |
| Parts in answers | ✅ Supported | ✅ Supported |

See `example_hw.tex` for the system `homework` class format.

## File Structure

```
.
├── worksheet.cls      # Main worksheet class file
├── example_ws.tex     # Worksheet Example usage
├── example_ws.pdf     # Compiled worksheet
├── example_hw.tex     # System homework class
├── example_hw.pdf     # Compiled homework
└── README.md          # This file
```

## Compilation

```bash
pdflatex example_ws.tex
pdflatex example_hw.tex
```

## Requirements

- LaTeX distribution (TeX Live, MiKTeX, etc.)
- Packages: `amsmath`, `amssymb`, `amsthm`, `xcolor`, `geometry`, `fancyhdr`, `enumitem`

## License

[MIT LICENSE](./LICENSE)
