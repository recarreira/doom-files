# Shortcuts

| shortcut | description           |
|----------|-----------------------|
| alt x    | emacs command list    |
| c 2 t /  | Change unTil second / |
|          |                       |


# DOOM Emacs

## Packages & configs

`init.el`:

``` emacs-lisp
       :editor
       parinfer            ; turn lisp into python, sort of

       :os
       (:if IS-MAC macos)  ; improve compatibility with macOS
       tty                 ; improve the terminal Emacs experience

       :lang
       (clojure +lsp)      ; java with a lisp
       emacs-lisp          ; drown in parentheses
       json                ; At least it ain't XML
       markdown            ; writing docs for people to ignore
       sh                  ; she sells {ba,z,fi}sh shells on the C xor
       yaml                ; JSON, but readable
```

`config.ls`:


```emacs-lisp
;; binding for the ' bug in mac:
(map! :after clojure-mode
      :map clojure-mode-map
      :localleader

      :desc "Cider jack in CLJ"
      "s" #'cider-jack-in-clj)

;; which-key delay time
(setq which-key-idle-delay 0.3
      which-key-idle-secondary-delay 0.05)
```

## Running in the terminal

Enable `tty` in the `init.el` and start emacs using `--no-window-system` option:

```sh
emacs -nw
```

## Running as daemon

Starting the daemon:

```sh
emacs --daemon
```

Connecting to it:

```sh
emacsclient -nw
```

## Terminal helpers

`.zhrc`:

``` sh
alias ec="emacsclient -nw"
alias ekill="emacsclient -e '(kill-emacs)'"
alias edaemon="emacs --daemon"
alias erestart="ekill && edaemon"
```
