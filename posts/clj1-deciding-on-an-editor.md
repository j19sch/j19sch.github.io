<!--
.. title: (clj 1) Deciding on a Clojure editor
.. slug: clj1-deciding-on-an-editor
.. date: 2020-04-29 20:00:15 UTC+02:00
.. tags: clojure
.. category: clojure
.. link: 
.. description:
.. type: text
-->

The second chapter of "[Clojure for the Brave and True](https://www.braveclojure.com/)" is all about Emacs, "an excellent Clojure editor". Now you might wonder: does your choice of editor really matter that much? You're learning the language, so you don't need advanced IDE features. Some syntax highlighting, some code completion, something to help you manage all those parantheses perhaps, done. That would be true if not for the Clojure REPL.

## Clojure REPL
The [REPL](https://clojure.org/guides/repl/introduction) is defintely a Thing(TM) in Clojure. It gives you a prompt where you can type code and it will execute it immediately. You can also load files with code into it, interacting with the functions and data defined in those. So that's a signifcantly faster feedback loop than having to compile and then run - which is how you'd normally run something written in Clojure, since the primaty platform is the JVM. There are [different ways](https://clojure.org/guides/repl/launching_a_basic_repl) of launching a REPL. Most guides I found tell you to use [Leiningen](https://leiningen.org/). Oh, and REPL stands for Read-Evaluate-Print_Loop, because that's what the REPL does.

It definitely feels like this REPL is a bigger thing than I appreciate right now. Probably because I have only just begun learning Clojure. On the other hand, I may have also been spoiled by the quick feedback provided by Python and its [IDLE](https://docs.python.org/3/library/idle.html). On the third hand, it's only because of learning of the Clojure REPL, I looked into importing files into Python's IDLE and found out that's indeed a thing it can do.

In any case, for a Clojure editor you want an editor that's able to connect to and interact with the REPL. It's defintely possible to type commands into the REPL yourself to make it do things like (re)loading files or evaluating a function, but why make things difficult for yourself?


## Emacs
Since the Brave and True book recommended Emacs, I decided I should give it a try. And the book does a great job teaching the Emacs you need for Clojure, including the most useful keybindings for [paredit](https://www.emacswiki.org/emacs/ParEdit), which is a minor mode to help "keep parentheses balanced". Trying out Emacs also confirmed what I mentioned in my [previous post](/blog/clj0-diving-straight-in/): I don't seem to have an Emacs kind of mind. The keybindings feel weird to me.That would probably change if I put in more effort than just going through the chapter once, but Chapter 1 did list some alternative editors, so I decided to take a look at Visual Studio Code and Vim first.


## Visual Studio Code
Although I like VS Code as an editor, I rarely use it since PyCharm and Sublime Text cover my needs. Which gives me the advantage of being able to set up VS Code specifically for Clojure, without having to worry it might mess something else up.

There are two Clojure plugins for VS Code. The first one I tried is simply called [Clojure](https://marketplace.visualstudio.com/items?itemName=avli.clojure). I tried it out and had to do quite some experimenting as I didn't really understand yet what a REPL is and what you would do with it. So after messing about with it, I drew some wrong conclusions, felt it was lacking and looked for an alternative.

The alternative is called [Calva](https://marketplace.visualstudio.com/items?itemName=betterthantomorrow.calva). It's definitely fancier than the other plugin. It adds a lot more commands to VS Code's Command Palette. It opens a REPL prompt with syntax highlighting, code completion and [paredit](https://calva.io/paredit/). This prompt opens as an editor window, so you can have your code and the REPL side-by-side, which I really like. Finally, Calva's documentation is a lot better than that of the other plugin. So Visual Studio Code with Calva looks like an excellent alternative to Emacs, although I also wanted to take a look at Vim as Clojure editor.

## Some lessons learned
Before we go there, I want to come back on those wrong conclusions I mentioned. I only discovered I had drawn these wrong conclusions because I wanted to write these blog posts and thus had to reconstruct what I had done earlier. Sparing all of us some time, I am just going to share what I learned during the reconstruction but had gotten wrong during my initial exploration.

Lesson 1: start your editor, e.g. by doing `code .` in the directory with your `project.clj`. This way the REPL will load your project and it will create its `.nrepl-port` file where you expect it to be.

Lesson 2: The REPL will create a `.nrepl-port` file with the port it is running on. However, when you do `lein repl` in the folder containing that file, it will not figure out that file is there and connect to the existing REPL. It will start a new REPL, overwriting the file.

Lesson 3: If you want to connect to an existing REPL, you can do so with `lein repl :connect <port>` or with `lein repl :connect $(cat .nrepl-port)`. That way you can do the editing in your editor and your REPLing in a separate terminal window. At least that's the way I think I'll be using the REPL, but that probably also something to do with the fact that my [i3wm window manager](https://i3wm.org/) makes it really easy to manage the two separate windows.

Perhaps also good to mention, somewhere along the way I updated Leiningen from 2.8.1 to 2.9.1, because something (I forgot what) was displaying an error because of the older version. Luckily that update just worked by me downloading and installing a .deb of that version without leading me into dependency hell.


## Vim
always liked vim, never got around to learning it beyond rudimentary because no reason to climb the steep initial learning curve

fireplace plugin
works slightly different, but fine, also because i3wm

Keybindings feel like home. (yay for no mouse, trackpoint, i3wm, on the couch) feeling of clarity
not sure if learning Clojure and vim s such a great idea, creating a cheat sheet (needs link!)
So after spending several hours trying out different editors, for now I'm going with Vim with VS Code as a backup.

more on vim setup next time