20230101081808

# This is m7tkr's bash page

## oreilly bash, 3ed

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
* `$@` vs `$*`

  > when  within double quotes, using `*` expands the reference to one word
  > consisting of all the values in the array separated by the first character
  > of the IFS variable, while `@` expands the values in the array to separate
  > words. When unquoted, both of them expand the values of the array
  > to separate words

* `type -a <cmdname>` - show all exec of <cmdname>
* `basename` and `dirname`
* `builtin <SHELL-BUILTIN>` - run shell built-in inside another function
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
  ```
  for name [in list]
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

* `shift <number>`

  `shift 1` makes `$2` to become `$1`, etc

* `getops`

  > `getopts` takes two arguments. The first is a string that can contain
  > letters and colons. Each letter is a valid option; if a letter is followed
  > by a colon, the option requires an argument. `getopts` picks options off
  > command line and assigns each one (without the leading dash) to a variable
  > whose name is `getopts`’s second argument. As long as there are options
  > left
  > to process, `getopts` will return exit status `0`; when the options are
  > exhausted, it returns exit status 1, causing the while loop to exit.

  ```bash
  while getopts ":ab:c" opt; do
      case $opt in
          a ) process option -a ;;
          b ) process option -b
              $OPTARG is the option's argument ;;
          c ) process option -c ;;
         \? ) echo 'usage: alice [-a] [-b barg] [-c] args...'
              exit 1
      esac
  done
  shift $(($OPTIND - 1))
  normal processing of arguments...
  ```
  `:` : if you begin the option letter string with a colon, `getopts` won’t 
  print the err message.

  `\?` : `opt` is set to, in case unlisted option is specified

* `$ [ \(...\) ]` then ` $(( ... ))` then `(( ... ))` to test arithmetics

  `for (( init ; ending condition ; update ))`

  `for ((;;))` - endless loop
