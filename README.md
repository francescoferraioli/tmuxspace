# tmuxspace

Start a new tmux workspace (session) based on a configuration file. It is a lightweight version of other tools like [tmuxinator](https://github.com/tmuxinator/tmuxinator) and [teamocil](https://github.com/remi/teamocil). Lightweight in dependencies which means that you can run it without having to set up binaries like ruby. However, its also lightweight in features as compared to those other tools.

## Installation

### Dependencies

It only has one dependency, which itself has no dependency:

- [tmux-up](https://github.com/jamesottaway/tmux-up)
  - Please follow the installation instructions

### Getting the binary

Currently the only way to download and use tmuxspace is to clone this repo and copy it to somewhere in your `$PATH`.

- `git clone https://github.com/francescoferraioli/tmuxspace.git`
- `cd tmuxspace`
- `chmod u+x tmuxspace`
- `cp tmuxspace /usr/local/bin/tmuxspace`

## Usage

Define the desired initial state of your tmux session in a file. 

The file must:
- End with `.tmuxspace`
- Contain lines with the following format
```
path(name)[setup]
```
> path: The path to the directory

> name: The name of the window

> setup: The way you want that window to be setup. It must be 3
characters long.

    [   ]: One pane
    [ | ]: Two panes split vertically
    [---]: Two panes split horizontally
    [-| ]: Three panes - two on the left and one on the right
    [ |-]: Three panes - one on the left and two on the right
    [-'-]: Three panes - two on the top and one on the bottom
    [-,-]: Three panes - one on the top and two on the bottom
    [-|-]: Four tiled panes

### Example

```
~/code/frontend(frontend)[ |-]
~/code/backend(backend)[ | ]
```

This would start a session with two windows:
- frontend with 3 panes at ~/code/frontend
- backend with 2 panes at ~/code/backend