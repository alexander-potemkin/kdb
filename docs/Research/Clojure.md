# Basic information

- Paul Graham infamous essay: http://www.paulgraham.com/icad.html
- Clojure cool free online book: https://www.braveclojure.com/clojure-for-the-brave-and-true/
- Learning in browser by example - very cool and easy to try: https://www.maria.cloud
- Clojure docs - https://clojuredocs.org
- Begginer materials, including animated introduction to Clojure: [https://gist.github.com/yogthos/be323be0361c589570a6da4ccc85f58f](https://gist.github.com/yogthos/be323be0361c589570a6da4ccc85f58f)
- community - Clojurians Slack


## No/Low-code implementation
- vlojure - https://github.com/Ella-Hoeppner/Vlojure
- Try on Blockly https://github.com/kloimhardt/werkbank
- in-browser Clojure and not only https://github.com/viebel/klipse
- another try on Blockly https://github.com/ParkerICI/blockoid

Tooling:
- Learn it in the code editor: [https://github.com/PEZ/rich4clojure](https://github.com/PEZ/rich4clojure)
- Calva - a VSCode/VSCodium/Theia extension and web interface to try it online now: [https://calva.io/get-started-with-clojure/](https://calva.io/get-started-with-clojure/)
- Bash like sripts replacement in Clojure: [https://book.babashka.org/#differences-with-clojure](https://book.babashka.org/#differences-with-clojure)
	- Babashka integration with editors: https://github.com/exercism/babashka/blob/main/docs/editors.md
	- Babashka book: https://book.babashka.org
- data navigator: https://github.com/djblue/portal
- web server (Ring) nice exceptions handling: https://github.com/magnars/prone
- another approach to debugger: https://github.com/jpmonettas/flow-storm-debugger
- library for logging and tracing in case of the failures: https://github.com/athos/Postmortem
- 

Features:
- fantastic REPL!
- programming by contract seems to be there: https://stackoverflow.com/questions/1865298/how-might-you-implement-design-by-contract-in-clojure-specifically-or-functional
- Tests that lies next to the code - [https://github.com/hyperfiddle/rcf](https://github.com/hyperfiddle/rcf)


# MacOS installation
```
brew tap homebrew/cask-versions
brew install --cask temurin17
java --version # expected to be Temurin 17
brew install clojure/tools/clojure
brew install --cask vscodium
```


# babashka 

REPL connect as [covered here](https://book.babashka.org/#repl):
`bb repl` for local repl

for Cursive socket-repl `bb socket-repl 1666` for networked repl, or `bb socket-repl '{:address "0.0.0.0" :accept clojure.core.server/repl :port 1666}'` for more options

prepl `bb socket-repl '{:address "0.0.0.0" :accept clojure.core.server/io-prepl :port 1666}'` 

for Canva - nrepl `bb nrepl-server 1667` 

Or from [babashka's guide](https://github.com/exercism/babashka/blob/main/docs/editors.md):

```
clj -A:new lib myorg/bbtest
cd bbtest
bb --nrepl-server 1667
open /Applications/VSCodium.app .
```


- Cmd + Shift + P -> `Connect to a running REPL` or Ctrl + Option + C twice
- Choose `Generic` project when prompted, and enter `localhost:1667`.

REPL commands:
-  Load Current File and Dependencies `Ctrl + Option + c enter`
-  Evaluate Current Form Inline `ctrl+alt+c e`
-  Evaluate Current Top Level Form (defun) `ctrl+alt+c space`

Go and play with [babashka's book](https://book.babashka.org/#introduction).
