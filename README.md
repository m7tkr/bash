Sun  1 Jan 2023 08:18:08 UTC

anything regarding bash will be posted here

# This is m7tkr's bash page

## oreilly bash, 3ed

> The GNU project was started by Richard Stallman of the Free Software
> Foundation (FSF) for the purpose of creating a UNIX-compatible operating
> system and replacing all of the commercial UNIX utilities with freely
> distributable ones. GNU embodies not only new software utilities, but a new
> distribution concept: the copyleft. Copylefted software may be freely
> distributed so long as no restrictions are placed on further distribution
> (for example, the source code must be made freely available).

> bash’s command-line editing interface is **readline**. It is actually a
> library of
> software developed for the GNU project that can be used by applications
> requiring a textbased interface. It provides editing and text-manipulation
> features to make it easier for the user to enter and edit text. Just as
> as importantly, it allows standardization, in terms of both key strokes and
> customization methods, across all applications that use it.

> `.bashrc` is deafult env file in bash

**Order of precedence** for various sources of commands in shell:

1. Aliases
2. Keywords such as `function` and others, like `if` and `for`
3. Functions
4. Built-ins like `cd` and `type`
5. Scripts and executable programs in `PATH`  env var

### cmds

* `fc` - load last run cmd
* `!!` - repeat last cmd
* `history`
  * `history -c` - delete history
* `stty`
* `bind` - check binded keystrokes
  * `^I` - `<TAB>`
  * `^H` - backspace
  * `^J` - linefeed
  * `^{` - escape
* prompts
  * PS1/2/3/4
* `hash`
  * `hash -r` - remove everything
  * `hash -d` *name* - remove specific entry
  * `hash -p` *name* - insert specific entry
* `cdable_vars` - variable for changing dirs
* `export [-p]` - show env vars
* `type -a <cmdname>` - show all exec of <cmdname>
* `basename` and `dirname`
* `builtin SHELL-BUILTIN` - run shell built-in inside another function
