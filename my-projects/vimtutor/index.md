title: Vimtutor
slug: vimtutor
date: 2020-05-05 21:55:00 UTC+02:00
link: 
description: 
type: text
hidetitle: false

# Vimtutor

The Vimtutor is Vim's interactive tutorial. It's included in most (all?) Vim installations. You can find more information about it [here](https://vimhelp.org/usr_01.txt.html#vimtutor).

### lesson 1
- `h j k l` movement
- `vim <filename` open file
- `ESC` normal mode
- `:q!` exit without saving
- `x` delete char under cursor
- `i` insert text
- `A` to append text at end of line
- `:wq` save and exit

### lesson 2
- `dw` delete rest of word
- `d$` delete until end of line
- motions: `w` start of next word, `e` end of current word, `$` end of line
- count: number before motion to repeat
- `0` to start of line
- `2dw` and `d2w` do the same thing, operator-[number]-motion
- `dd` delete line
- `u` undo change
- `U` undo changes whole line
- `ctrl+r` redo

### lesson 3
- `p` put deleted after cursor
- `r` replace character at cursor
- `c[number]<motion>` change until motion

### lesson 4
- `ctrl+g` file location and status
- `G` move to bottom of file
- `gg` move to start of file
- `<lineno>G` go to line number
- `/` search forward, `?` search backward, `n` match forward, `N` match backward
- `ctrl+o` jump back in jumplist, `ctrl+i` jump forward in jumplist
- `%` matching parentheses `)]}`
- `:s/old/new` single find-and-replace
- `:s/old/new/g` line-global find-and-replace
- `:#,#s/old/new/g` range of lines
- `:%s/old/new/g` whole file
- `:%s/old/new/gc` whole file, prompt

### lesson 5
- `:!<command>` execute external command
- `:w <filename>` save file
- `v` visual mode (selection)
- `:r <thing>` retrieve and insert, e.g. `:r <filename>` or `:r !ls`

### lesson 6
- `o` open line below cursor
- `O` open line above cursor
- `a` append text after cursor
- `R` replace mode
- `y` yank for copy (yank is operator so movements)
- `p` put for paste
- `:set ic` ignore case, `:set noic`
- `:set hls is` hlsearch (highlight matches) and incsearch (show partial matches) options
- `:nohlsearch` disable highlighting of matches
- `\c` ignore case for single search, e.g. `/ignore\c`
- `ic` ignorecase, `is` incsearch, `hls` hlsearch


### lesson 7
- `F1`, `:help`
- `ctrl+w ctrl+w` jump windows
- `:q` close window
- `:help <something>`
- `~/.vimrc` startup script
- `ctrl+d` `tab` command completion
