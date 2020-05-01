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

The second chapter of "[Clojure for the Brave and True](https://www.braveclojure.com/)" is all about Emacs, "an excellent Clojure editor". Now you might wonder: does your choice of editor really matter that much? You're learning the language, so you don't need advanced IDE features. Some syntax highlighting, some code completion, something to help you manage the parantheses perhaps, done. That would be true if not for the Clojure REPL.

## Clojure REPL
The [REPL](https://clojure.org/guides/repl/introduction) is defintely a Thing(TM) in Clojure. It gives you a prompt where you can type code and it will execute it immediately. You can also load files with code into it, interacting with the functions and data defined in those. So that's a signifcantly faster feedback loop than having to compile and then run - which is how you'd normally run something written in Clojure, since the primaty platform is the JVM. Oh, and REPL stands for Read-Evaluate-Print_Loop, because that's what the REPL does.

It definitely feels like this REPL is a bigger thing than I appreciate right now. Probably because I have only just begun learning Clojure. On the other hand, I may have also been spoiled by the quick feedback provided by Python and its [IDLE](https://docs.python.org/3/library/idle.html). On the third hand, it's only because of learning of the Clojure REPL, I looked into importing files into Python's IDLE and found out that's indeed a thing it can do.

In any case, for a Clojure editor you want an editor that's able to connect to and interact with the REPL. It's defintely possible to type commands into the REPL yourself to make it do things like (re)loading files or evaluating a function, but why make things difficult for yourself?


## Emacs
Since the Brave and True book recommends Emacs, I decided I should give Emacs a try - even though as mentioned in my [previous post](/blog/clj0-diving-straight-in/) I don't seem to have an Emacs mind. The book does a great job teaching the Emacs you need for Clojure, but all those keybindings, I don't have the mind for it. Of course, that would probably change if I put in some more effort than going throught the chapter once, but Chapter 1 did list some alternative editors, so I decided to take a look at Visual Studio Code and Vim first.


## Visual Studio Code
like it as an editor, don't use it because PyCharm and Sublime, so good to set up specifically for Clojure

plugin 1 "Clojure" https://marketplace.visualstudio.com/items?itemName=avli.clojure
- do `code .` in the dir with `project.clj` so that it loads the project and creates `.nrepl-port` where you expect it
- `lein repl` does not read to `nrepl-port` but does (over)write to it, so need to `lein repl :connect <port>`, I prefer running this way, having a terminal / repl client to interact with over VS code panels, i3wm helps with it virtual workspaces and speed and keyboard shortcuts

plugin 2, "Calva" https://marketplace.visualstudio.com/items?itemName=betterthantomorrow.calva
- fancier, separate repl pane, allowing working side-by-side code-repl
- lot more commands
- includes [paredit](https://calva.io/paredit/)
- same issue with the repl, need `:connect`

somewhere along the way updated Leiningen from Ubuntu 18.04 repo to later Ubuntu repo
did another round of testing to be able to write this blog post, turns out I mis-interpreted/mis-remembered some stuff



## Vim
always liked vim, never got around to learning it beyond rudimentary because no reason to climb the steep initial learning curve

fireplace plugin
works slightly different, but fine, also because i3wm

Keybindings feel like home. (yay for no mouse, trackpoint, i3wm, on the couch) feeling of clarity
not sure if learning Clojure and vim s such a great idea, creating a cheat sheet (needs link!)
So after spending several hours trying out different editors, for now I'm going with Vim with VS Code as a backup.

more on vim setup next time