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

### NerdTree
- open/close with `ctrl+n` (.vimrc)
- `?` while open for keybindings

### GitGutter
- see diff: `<Leader>hp`

### vim-fireplace
- `:Require`: reload current namespace
- `:Eval`: eval/print the outermost form for the current line
- `cpp`: eval/print the innermost form at the cursor
