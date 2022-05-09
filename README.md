# Shortcuts

## General navigation and edition 

| shortcuts               | description                                                                           |
|-------------------------|---------------------------------------------------------------------------------------|
| `alt` + `x`             | emacs command list                                                                    |
| `c (2) t /`             | Change unTil (second) `/`                                                             |
| `d w`                   | Delete Word                                                                           |
| `c i "`                 | Change Inside `"`                                                                     |
| `u`                     | Undo                                                                                  |
| `ctrl` + `r`            | Redo                                                                                  |
| `shift` + `v` `(j) (k)` | Select on Visual mode (down) (up)                                                     |
| `shift` + `k`           | go to documentation                                                                   |
| `(shift) o`             | new line (above)                                                                      |
| `33 G`                  | Go to line `33`                                                                       |
| `/bla` `(n) (N)`        | search word `bla` on file. Press enter, then n (next) or N (previous)                 |
| `0`                     | beginning of line                                                                     |
| `$`                     | end of line                                                                           |
| `:e <tab>`              | Edit of create file                                                                   |
| `:! ls`                 | run the `ls` command on terminal                                                      |
| `:w`                    | Write (aka save) file                                                                 |
| `:q`                    | Quit the buffer                                                                       |
| `:%s/bla/ble/gI`        | Substitute (aka replace) word `bla` for `ble` on file (%), case sensitively (I)       |
| `space q s`             | Save current session                                                                  |
| `space c d`             | go to Definition                                                                      |
| `space c D`             | go to references                                                                      |
| `space /`               | search on project (Note: use up and down keys to navigate, not j and k)               |
| `space b k`             | Kill (close) the current Buffer                                                       |
| `space space`           | open files on current project                                                         |
| `space b i`             | see and navigate through open files on the current Buffer (ibuffer)                   |
| `space o P`             | open project tree, showing the current file location                                  |
| `space w h`             | move to the window on the left (h). You can also go to right (l), down (j) and up (k) |

## Clojure

| shortcuts | description                    |
|-----------|--------------------------------|
| `, e b`   | Eval current file (aka Buffer) |
| `, t n`   | Run Test on current Namespace  |
| `, t t`   | Run current test               |
| `, t a`   | Rerun last test                |

TODO: sort shortcuts 

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
