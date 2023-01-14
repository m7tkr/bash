20230101081808

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
  * `PS1` - main prompt
  * `PS2` - continuation
  * `PS3` - used by `select`
  * `PS4`
* `hash`
* `cdable_vars` - variable for changing dirs
* `export [-p]` - show env vars
* `type -a <cmdname>` - show all exec of <cmdname>
* `basename` and `dirname`
* `builtin SHELL-BUILTIN` - run shell built-in inside another function
* `if`
  * `[]` vs `[[]]`
    > The second version is identical to the first except that word splitting
    > and pathname expansion are not performed on the words within brackets
  * *string comparison operators*
  * *arithmetic **test** operators*
  * *file attribute checking*
  * `if` operates on exit status
  * `&&` and `||` - logical operators
    > Same as above. However, unlike those operators, `-a` and `-o` are only
    > available inside a `test` conditional expression
  * `!` - placed before brackets for negation
* `for`
  ```for name [in list]
     do
         statements that can use $name...
     done
   ```
  in case `[in list]` is not specified `$@` is default
* use `IFS` - internal field separator

  `TAB`, `LINEFEED` and `space` by default
* `command` - shell built-in, disables alias and function lookup
* `case`
  ```
  case expression in
      pattern1 )
          statements ;;
      pattern2 )
          statements ;;
  ...
  esac
  ```
  > Any of the patterns can actually be several patterns separated by pipe
  > characters (|).
* `select`
  ```
  select name [in list]
  do
       statements that can use $name...
  done
  ```
* `while` vs `until`

  > In while, the loop executes as long as the condition is true; in until,
  > it runs as long as the condition is false.
