<!--
.. title: (clj 2) Setting up Vim for Clojure
.. slug: clj2-setting-up-vim
.. date: 2020-05-05 21:55:15 UTC+02:00
.. tags: clojure, programming, vim
.. category: clojure
.. link: 
.. description:
.. type: text
-->

As mentioned in my [previous post](/blog/clj1-deciding-on-an-editor) I've decided to use [Vim](https://www.vim.org/) as my Clojure editor. That leaves me with three things to do: getting reacquainted with Vim, updating my Vim config in the .`vimrc` file, and installing both general and Clojure-specific Vim plugins.


## Getting reacquainted with Vim

Ever since I learned Vim basics a long time ago I have been using it once in a while to make small edits to a config file or a commit message, but not for anything more complicated than that. So that's the first thing I wanted to address: refresh my basics and make sure I know where to find more information when I need it.

### Vimtutor
I figured that a good way to get back into Vim was the [Vimtutor](https://vimhelp.org/usr_01.txt.html#vimtutor). It's a 30-minute interactive tutorial where you edit a file with instructions with vim. I kept notes of what it covers, which you can find [here](/my-projects/vimtutor). Vim's help also includes a [quickref](https://vimhelp.org/quickref.txt.html), an "Overview of the most common commands you will use", which is intimidatingly long considering that description. As a reference to look things up in, it should be useful, though.

<!-- TEASER_END -->

Going through the Vimtutor to refresh my Vim felt good. Something about Vim keybindings just feels right to me. However, me liking Vim dies not mean that I automatically remember all the keybindings and commands and capabilities of Vim. So I decided that if I wanted this project of both learning Vim and Clojure to work, I should make a [Clojure-Vim cheatsheet](/my-projects/clojure-vim-cheatsheet) to help me. The plan is to keep updating this sheet as I do more with Vim and Clojure.

### Using Vim's `:help` command
Another great resource are Vim's help files, which can be found [online](https://vimhelp.org/) and by typing `:help<Enter>` or `<F1>` in Vim itself. You can also see help on specific topics by doing `:help {topic}<Enter>`, or do `:help {topic}<ctrl+d>` to see entries matching what you have typed so far.

When you do that, you'll notice that Vim will open the relevant help file in a separate [window,](https://vimhelp.org/windows.txt.html), i.e. the vim screen is now split in half. (Vim also has [tabs](https://vimhelp.org/tabpage.txt.html), with tabs containing one or multiple windows.) So that makes right now the right time to learn some basic Vim window management:

- close the active window with `:q` (closes Vim if that leaves you with 0 active windows)
- make the active window take up all vertical space with `ctrl+w _` or all horizontal space with `ctrl+w |`
- split equally again with `ctrl+w =`
- move to the next window with `ctrl+w w`
- move to the window in a specific direction with `ctrl+w {direction}`, with direction being one of `h j k l`
- snap the window to a side with `ctrl+w shift+{direction}`, with direction again being one of `h j k l`

With basic window management out of the way, there are also a few keybindings to learn to help with text navigation:

- to look up whatever word is under the cursor hit `ctrl+]` (works for topics and with section titles)
- to jump back to where you were use `ctrl+o`
- to jump forward again use `ctrl+i`

That should be enough to make Vim's help files a useful resource. Or at least I hope it is, because the above is the result of me looking up the things I expect to need to be able to use Vim's help files.


## Updating my Vim configuration
First of all a warning: you can spend hours upon hours looking into Vim's configuration settings, plugins, and color schemes - without using Vim to write a single line of... let's say Clojure. If you want to know how deep that rabbit hole goes, I recommend reading this [blog post](http://karolis.koncevicius.lt/posts/porn_zen_and_vimrc/) by Karolis Koncevičius, where he shares "Lessons learned during my 5 year adventure in fiddling with Vim configuration files".

So after spending a few hours exploring Vim settings and plugins, I decided to keep my configuration and especially my plugins as limited and simple as possible - despite all the promises of shiny new toys I could add. That way I might actually get around again to playing with Clojure and writing a blog post about that sometime soon.

### The `.vimrc` file
Vim configuration happens via a file in the user's home directory, `.vimrc`. You can find mine [here](https://github.com/j19sch/dotfiles/blob/b1b62a2169058edd8a0f5069e694b8717890a1fb/vimrc). I might have updated it since writing this though, so if you want to see the current version, go [here](https://github.com/j19sch/dotfiles/blob/master/vimrc).

There are plenty of good resources on what to put in your `.vimrc`-file. Here are three I took inspiration from:

- [A Good Vimrc](https://dougblack.io/words/a-good-vimrc.html) by Doug Black
- [Basic vimrc](https://github.com/amix/vimrc/blob/master/vimrcs/basic.vim) by Amir Salihefendic
- [Top 50 Vim Configuration Options](https://www.shortcutfoo.com/blog/top-50-vim-configuration-options/) from shortcutFoo

That should be more than enough to get you going. As part of this blog post, I do want to highlight a few settings that you might not think of changing while using Vim. First, there's `set wildmenu`, which will display the tab completion of Vim's command line as a menu instead of as one completion at a time. Secondly, `set scrolloff=5` means Vim will always try to display 5 lines above and below the cursor and `set display+=lastline` will try to show as much as possible of the last line in the window instead of a column of "@". Finally, I disabled backup and swap files with `set nobackup`, `set nowritebackup`, and `set noswapfile` for multiple reasons. It saves writes to my SSD, for version control I use GitHub, and it allows me to set `updatetime=300` so that the GitGutter plugin feels more responsive.

### Vim plugins
The main question for Vim plugins is: which Vim plugin do you use to manage your Vim plugins? A few years ago when looking into Vim as Python editor, I decided to go with [vim-plug](https://github.com/junegunn/vim-plug). I can't remember why, but it could be because it says it's a "minimalist Vim plugin manager". Two popular alternatives are [Vundle](https://github.com/VundleVim/Vundle.vim) and [Pathogen](https://github.com/tpope/vim-pathogen). Since Vim 8 there's also native support for [packages](https://vimhelp.org/repeat.txt.html#packages).

#### General plugins
I ended up installing the following general plugins:

- [GitGutter](https://github.com/airblade/vim-gitgutter) to show git diff markers in the sign column and see the diff
- [indentLine](https://github.com/Yggdroot/indentLine) to display indentation levels
- [Lightline](https://github.com/itchyny/lightline.vim) to configure the statusline
- [NerdTree](https://github.com/preservim/nerdtree) to have a tree explorer
- [vim-commentary](https://github.com/tpope/vim-commentary) to easily (un)comment lines
- [vim-fugitive](https://github.com/tpope/vim-fugitive) to show the current branch in the statusline (it can do lots more than that)
- [vim-plug](https://github.com/junegunn/vim-plug) to manage installing and removing plugins as mentioned above

Of course all of these come with their own commands. The ones I expect to use are in my [Clojure-Vim cheatsheet](/my-projects/clojure-vim-cheatsheet/).

#### Clojure plugins
For Clojure-specific plugins I mostly followed Keith Smiley's [advice](https://thoughtbot.com/blog/writing-clojure-in-vim) and went with these:

- [vim-clojure-highlight](https://github.com/guns/vim-clojure-highlight) for syntax highlighting to referred and aliased vars in Clojure buffers
- [vim-fireplace](https://github.com/tpope/vim-fireplace) as REPL plugin
- [vim-sexp](https://github.com/guns/vim-sexp) for precision editing to S-expressions
- [vim-sexp-mappings-for-regular-people](https://github.com/tpope/vim-sexp-mappings-for-regular-people) for supposedly better vim-sexp key mappings

I have barely used these plugins - if at all, actually, in the case if vim-sexp -, so my cheatsheet won't have much on these yet.

As far as I know there are two alternatives to vim-fireplace: [vim-iced](https://github.com/liquidz/vim-iced) and [conjure](https://github.com/Olical/conjure), with the latter only actively supporting [Neovim](https://neovim.io/). I am curious about those, but am going to postpone exploring them until I have some experience with vim-fireplace - and with Clojure itself.

#### Color schemes
The color scheme I enabled last time I was looking into Vim is [Diki Ananta](https://dikiaap.id/)'s [minimalist](https://github.com/dikiaap/minimalist). I still like it, so that saved me the time of looking for a good color scheme. I would like to have a good light color scheme as well, though...

<div style='margin-bottom: 1.8rem' markdown="1"></div>
And with all of that done, I think I'm ready to return to the third chapter of [Clojure for the Brave and True](https://www.braveclojure.com/).