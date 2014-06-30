minimd
=======

Synopsis
---------
A markdown syntax and filetype plugin for vim which aims to make writing and outlining pleasant.  For this use case, 'pleasant' means that the following requirements must be met.

### Requirements
1. It must be easy to work with headers:
    - Shortcuts for header promotion and demotion;
    - Shortcuts for jumping between headers.
2. Section folding must work properly:
    - Headers must be included in folds.
3. Text must soft wrap at screen boundaries without breaking words.
4. Syntax highlighting mustn't be too garrish,
    - But headers, list items, citations, and code must be signified.
5. Where possible, Vim's defaults are to be preserved.
6. Configuration should only be required for interfacing with external tools
7. Export via Pandoc to HTML or PDF should work by default.

Usage
-----

### Headers
#### Jumping
| Key        | Action           |
| ---------- | -----------------|
| `<Tab>`    | Next header.     |
| `S-<Tab>`  | Previous header. |

#### Promotion and Demotion
| Key |  Action         |
| --- | ----------------|
| `=` | Promote header. |
| `-` | Demote header.  |


### Tasks
| Key      |  Action                        |
| -------- | ------------------------------ |
| `<CR>`   | Toggle task completion status. |

This works with list items written in Github Style Markdown.  Unnumbered list items are converted to tasks as in `- ` to `- [ ] `, and tasks are toggled between `- [ ] ` and `- [X] `.

### Folding (Vim Defaults)
| Key     | Action                          |
| ------- | ------------------------------- |
| `zc`    |       *C*lose fold.             |
| `zo`    |       *O*pen fold.              |
| `zm`    |       Fold one *m*ore level.    |
| `zM`    |       *M*aximum fold-level.     |
| `zr`    |       *R*eveal one fold level.  |
| `zR`    |       *R*eveal all fold levels. |

### Pandoc Integration
#### Keybindings
| Key            | Action                                        |
| -------------- | --------------------------------------------- |
| `<Leader>html` | Export to `out.html` in the parent directory. |
| `<Leader>pdf`  | Export to `out.pdf` in the parent directory.  |

#### Pandoc Options
Options can be passed to Pandoc, either globally or per-filetype by defining `g:pandoc_options`, `g:pandoc_options_html`, and `g:pandoc_options_latex` in your `.vimrc`.  So, for example, if you would like to set a bibliography for use while exporting via Latex, you might write:

    let g:pandoc_options = "-N --bibliography=~/my.bib"

Where `my.bib` is your BibTeX bibliography.
