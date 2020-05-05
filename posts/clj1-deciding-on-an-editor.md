<!--
.. title: (clj 1) Deciding on a Clojure editor
.. slug: clj1-deciding-on-an-editor
.. date: 2020-05-01 18:00:15 UTC+02:00
.. tags: clojure, emacs, vscode, vim
.. category: clojure
.. link: 
.. description:
.. type: text
-->

The second chapter of "[Clojure for the Brave and True](https://www.braveclojure.com/)" is all about Emacs, "an excellent Clojure editor". Now you might wonder: does your choice of editor really matter that much? You're learning the language, so you don't need advanced IDE features. Some syntax highlighting, some code completion, something to help you manage all those parantheses perhaps, done. That would be true if not for the Clojure REPL.


## The Clojure REPL
The [REPL](https://clojure.org/guides/repl/introduction) is definitely a Thing™️ in Clojure. It gives you a prompt where you can type code and it will execute it immediately. You can also load files with code into it, interacting with the functions and data defined in those. So that's a signifcantly faster feedback loop than having to compile and then run - which is how you'd normally run something written in Clojure, since its primary platform is the JVM. There are [different ways](https://clojure.org/guides/repl/launching_a_basic_repl) of launching a REPL, but most guides I found tell you to use [Leiningen](https://leiningen.org/). Oh, and REPL stands for Read-Evaluate-Print_Loop, because that's what the REPL does.

It definitely feels like this REPL is a bigger deal than I appreciate right now. Probably because I have only just begun learning Clojure. On the other hand, I may have also been spoiled by the quick feedback provided by Python and its [IDLE](https://docs.python.org/3/library/idle.html). On the third hand, it's only because of learning of the Clojure REPL, I looked into importing files into Python's IDLE and found out that's indeed a thing it can do.

<!-- TEASER_END -->

In any case, for a Clojure editor you want an editor that's able to connect to and interact with the REPL. It's defintely possible to type commands into the REPL yourself to make it do things like (re)loading files or evaluating a function, but that's making things harder for yourself than needed.


## Emacs
As mentioned in my [previous post](/blog/clj0-diving-straight-in/), I don't seem to have the mind for [Emacs](https://www.gnu.org/software/emacs/). However with the Brave-and-True book recommending it, I decided to give it another shot. It had been almost two decades after all. And I must say the book does a great job teaching the Emacs you need for Clojure, including the most useful keybindings for [paredit](https://www.emacswiki.org/emacs/ParEdit), which is a minor mode to help "keep parentheses balanced". Unfortunately it also confirmed my feelings towards Emacs. It doesn't click with me. The keybindings feel weird somehow. Probably that would change if I'd put in more effort than just going through the chapter once, but Chapter 1 did list some alternative editors. So I decided to take a look at Visual Studio Code and Vim, to see if they would work for me.


## Visual Studio Code
Although I like [Visual Studio Code](https://code.visualstudio.com/) as an editor, I rarely use it since PyCharm and Sublime Text cover my needs. Which gives me the advantage of being able to set up VS Code specifically for Clojure, without having to worry that it might mess something up.

There are two Clojure plugins for VS Code. The first one I tried is simply called [Clojure](https://marketplace.visualstudio.com/items?itemName=avli.clojure). I tried it out and had to do quite some experimenting as I didn't really understand yet what a REPL is and what you would do with it. So after messing about with it, I drew some wrong conclusions, felt it was lacking and looked for an alternative.

The alternative is called [Calva](https://marketplace.visualstudio.com/items?itemName=betterthantomorrow.calva). It's definitely fancier than the other plugin. It adds a lot more commands to VS Code's Command Palette. It opens a REPL prompt with syntax highlighting, code completion and [paredit](https://calva.io/paredit/). This REPL prompt opens as an editor window, so you can have your code and the REPL side-by-side, which I really like. Finally, Calva's documentation is a lot better than that of the other plugin.

So Visual Studio Code with Calva looks like an excellent alternative to Emacs, but first I wanted to take a look at Vim as Clojure editor.


## Some lessons learned
Before we move on to Vim, I want to come back to those wrong conclusions I mentioned. I only discovered I had drawn these wrong conclusions because I wanted to write these blog posts and thus had to reconstruct what I had done earlier. Sparing all of us some time, I am just going to share what I learned during the reconstruction, but had gotten wrong during my initial exploration.

Lesson 1: start your editor (e.g. by running `code .` ) in the directory with your `project.clj`. This way the REPL will load your project (instead of not) and it will create its `.nrepl-port` file where you expect it to be.

Lesson 2: The REPL will create a `.nrepl-port` file with the port it is running on. However, when you do `lein repl` in that same folder, it will not figure out that file is there and connect to the existing REPL. It will start a new REPL and overwrite the file with its own port number.

Lesson 3: If you want to connect to an existing REPL, you can do so with `lein repl :connect <port>` or even easier with `lein repl :connect $(cat .nrepl-port)`. This way you can do the editing in your editor and your REPLing in a separate terminal. At least that's the way I think I'll be using the REPL, but that also something to do with the fact that my window manager [i3wm](https://i3wm.org/) makes it really easy to manage the two separate windows.

Perhaps also good to mention, somewhere along the way I updated Leiningen from 2.8.1 to 2.9.1, because something (I forgot what) was displaying an error because of the older version. Luckily that update just worked by downloading and installing a .deb of that version - without leading me into dependency hell.


## Vim
For some reason I've always really liked [Vim](https://www.vim.org/). I've also never really used it for anything more than a quick edit of some file, since it has a steep learning curve. You need consistent practice to get over that initial cliff. Actually, the only reason I'm comfortable using Vim's basic movement keys `h j k l` is because I've played enough roguelikes such as [Dungeon Crawl Stone Soup](https://crawl.develz.org/) that use those keys to move your character around.

The Clojure plugin for Vim is [vim-fireplace](https://github.com/tpope/vim-fireplace). It works slightly differently as it is "not quite a REPL". Apparently - I'm just repeating what I read here - providing a REPL prompt is not something that would play nice with the way Vim's buffers work.

How it does work, is that `cpp` will evaluate what's under your cursor in Vim's command-line window. To be exact, it evalutes the innermost form. I have somewhat of an intuitive graps of what that meams, "innermost form", but don't ask me to explain it just yet. There's also `cqq`, which gives you a blank line in insert mode to type in and evaluate some Clojure. Finally, there's `cpr`. I thought it just reloaded the file into the REPL, but looking [here](https://github.com/tpope/vim-fireplace/blob/master/doc/fireplace.txt) it seems it will also run tests. So perhaps it's better to use `:Require` for the reloading?


## Going forward with Vim
Having tried out these different editors and how they interact with the Leiningen REPL, I have decided to go with Vim. It might not be the best idea to learn both Clojure and Vim at the same time, but I'm still too intrigued with Vim not to try. And I know that I have Visual Studio Code with Calva as a backup.

All in all I think it took me several hours to set up these editors, play around with them and form an opinion. I'm not sure how I feel about that. It does allow me to make an informed choice about which editor to use, but I could have also spent that time actually learning Clojure.

And the best part is that I haven't even set up Vim properly. There are some more recommended plugins in addition to vim-fireplace. And I should clean up my Vim config and the plugins I installed when looking into Vim for Python a few years ago. So more on that next time.
