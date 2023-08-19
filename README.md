Hydra
======

a C implementation of [Emacs Hydra](https://github.com/abo-abo/hydra) package to be used in terminal.

## What is Hydra

Just list Emacs Hydra. It's a program that groups your terminal commands and bind them to common key on your keyboard. Commands can also be grouped in a tree like structure each node in the tree has a name and key bound to it.

[Spacemacs](https://www.spacemacs.org/) for example is an emacs configuration centered around hydra commands, with all user commands grouped as trees bound in a mnemonic way. for example:

- openenig a file is bound to `space f f`
- deleting current file is bound to `space f D`
- Git status `space g s`

This repo implements a program that can be invoked in your terminal, it reads CSV files of `key,name,command` lines then shows Terminal UI similar to Emacs Hydra.

Binding Hydra to `space` key in your terminal mean pressing `space` will make your terminal similar to spacemacs. this repo has a bash script `hydra-completion.bash` which achieve this binding.

## Build

To build from source:

```
make
```

## Install

build and install
```
make
sudo make install
```

in your `.bashrc` export environment variable `HYDRA` to has a list of hydras files. Hydra example files are installed under `/usr/share/hydra/hydras`.
The following setup Hydra to load `git` commands

```
export HYDRA="/usr/share/hydra/hydras/git"
source /usr/share/hydra/hydra-completion.bash
```

loading `/usr/share/hydra-completion.bash` will bind `hydra` to `Space` key in your keyboard and will invoke `hydra` when the line is empty.

## Hydra file

* Hydra files are simple CSV files that define the commands hydra can load.
* The file has 3 columns without header. an example is under `hydras` directory in this repo.

a simple example can be as follow
```csv
g,Git,
gs,Status,git status
```

* it defines `Git` command that doesn't execute a command under the key `g`
* and defines a command named `Status` under key `s` inside `g` that will execute the command `git status`

## Running

You can run `hydra` binary with a list of hydra files passed to it for example:

```
hydra hydras/git hydras/systemd hydras/github
```

Hydra will load the files in the order passed.

Here is an example running `hydras/git`

[![asciicast](https://asciinema.org/a/603564.svg)](https://asciinema.org/a/603564)


## Project status

The project is still in the prototype phase. I haven't written C in a while (10+
years) so I'm a bit rusty. probably there could be a lot of improvements.
However I would encourage you to try it out.
