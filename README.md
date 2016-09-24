# clojureVSCode

[Clojure](https://clojure.org) support for Visual Studio Code.

I'm trying, believe me!

![Workflow](/images/workflow.gif)

# How to Use?

This extension relies on [Cider nREPL](https://github.com/clojure-emacs/cider-nrepl).
This means you will need to add it to your ``profiles.clj``. Put the following content to your
 `~/.lein/profiles.clj`:

```clojure
{:user {:plugins  [[cider/cider-nrepl "0.12.0-SNAPSHOT"]]
       :dependencies [[org.clojure/tools.nrepl "0.2.12"]]}}
```

When you open a project the extension tries to connect to nREPL automatically.
Otherwise you may run `Connect to nREPL` command through the Visual Studio Code
command pallet.

# Supported Features

Code completion

Code navigation

Interaction with REPL

Showing documentation on hover

# Features That Are Not Supported (But Nice to Have)

Function signatures

Linting

[Debug](https://github.com/indiejames/vscode-clojure-debug)



# Getting Started Walkthrough

1. Create a clojure project you wish to connect to. For this guide we will use leinigen
   ```bash
      lein new hello-vscode
   ```

2. Start a REPL in your terminal, and note the port the REPL is lisening on
   ```bash
$ cd hello-vscode
$ lein repl
nREPL server started on port 45247 on host 127.0.0.1 - nrepl://127.0.0.1:45247
REPL-y 0.3.7, nREPL 0.2.12
Clojure 1.8.0
   ```
   Please note the port that your nREPL is lisening on, in this case **45247** because you will need it later.

3. Open the project folder in VS Code.

4. Connect to the running REPL.

   Open the command pallet and select the command `Clojure: Connect to nREPL`

  You should then be prompted for an nREPL port, enter the port noted in step #2, `45247`.
  
  You should then be prompted for the host of the REPL. In this example we will enter `localhost`.
  
  You should then get a message showing successful connection to the nREPL! 
  
  You should also see a connection indicator on the bottom of the editor window on the left hand side of the status bar that looks like `nrepl://localhost:45247`.
  
  

5. Now Eval a file. The repl needs to have it's namespace initialized and set so it can know about and show things like your docstrings.

   Open the command pallet, and select the command `Clojure: Eval`.
   
   This should evaluate your entire file, and a file successfully compiled notification should be shown.


6. Eval a selected expression
   
   Show the output window by using the View / Output from menu bar if it's not already visible.
   
   Select a block of code you wish to evaluate.
   
   Open the command pallet, and select the command `Clojure: Eval and show the result`. 
   
   Results from the REPL should be printed to the output window named `Evaluation Results`



7. All done, you're to code some clojure :)




# Troubleshooting

## Code completion doesn't work, what I'm doing wrong?

Most likely you forgot to add `cider-nrepl` to the list of dependencies. Please,
consult `How to Use?` section.  

## I don't see completions from the current namespace!

You should eval the file first using the `Eval` command.

## How to understand if I'm connected to nREPL?

If you see a `nrepl://nreplhost:nreplport` status bar item, most likely you
are connected :)

# License

[MIT](https://raw.githubusercontent.com/avli/clojureVSCode/master/LICENSE.txt)
