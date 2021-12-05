title: Clojure-Vim cheatsheet
slug: clojure-vim-cheatsheet
date: 2020-05-05 21:55:00 UTC+02:00
link: 
description: 
type: text
hidetitle: false

# Clojure-Vim cheatsheet

### help
- `:help {topic}<Enter>` or `:help {topic}<ctrl+d>`
- navigate with `ctrl+]` (go), `ctrl+o` (back), `ctrl+i` (forward)
- Vimtutor contents listed [here](/my-projects/vimtutor)

### windows
- windows size: `ctrl+w _` (all vert space), `ctrl+w |` (all hor space), `ctrl+w =` (equal)
- snap window to side: `ctrl+w shift+H/J/K/L`
- move to window: `ctrl+w w` (next), `ctrl+w h/j/k/l` (direction)

### tabs
- next tab: `gt`, previous tab: `gT`, tab in position i: `{i}gt`
- back-and-forth between two tabs: `<Leader>tl` (.vimrc)

### copy-pasting
- `"+` to copy to system clipboard

### auto-complete
- `ctrl+n`: find next match
- `ctrl+p`: find previous match

### macros
- `@{key}`: run macro, so e.g. `@c` to run the macro mapped to `c`


### NerdTree
- open/close with `ctrl+n` (.vimrc)
- `?` while open for keybindings


### GitGutter
- see diff: `<Leader>hp`


### vim-commentary
- `gcc` (un)comment line


### vim-sexp
- `cse(`,`cse)`: surround element in parentheses
- `cse[`, `cse]`: surround element in brackets
- `cse{`, `cse}`: surround element in braces
- `>)`, `<)`, `>(`, and `<(`: slurpage and barfage
- `dsf`: splice (delete surroundings of form)
- `<I`, `>I`: insert at the beginning and ending of a form


### vim-fireplace
- `:Require`: reload current namespace
- `:Require!`: reload all namespaces
- `:Eval`: eval/print the outermost form for the current line
- `:%Eval`: eval/print whole file
- `cpp`: eval/print the innermost form at the cursor
- `cp{motion}`: eval/print motion, e.g. `$` (end of line) or `_` (1st non-blank char on line)
- `K`: show Clojure docs for symbol under cursor
