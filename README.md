20230101081808

# bash notes

* useless use
https://porkmail.org/era/unix/award

## search success in `man bash`

* file attributes
* `^ +Parameter Expansion`
* arithmetics evaluation

## oreilly bash, 3ed

> `.bashrc` is deafult env file in bash

* **Order of precedence** for various sources of commands in shell:

  1. Aliases
  2. Keywords such as `function` and others, like `if` and `for`
  3. Functions
  4. Built-ins like `cd` and `type`
  5. Scripts and executable programs in `PATH`  env var

* prompts
  * `PS1` - main prompt
  * `PS2` - continuation
  * `PS3` - used by `select`
  * `PS4` -

* `$@` vs `$*`

  > when  within double quotes, using `*` expands the reference to one word
  > consisting of all the values in the array separated by the first character
  > of the IFS variable, while `@` expands the values in the array to separate
  > words. When unquoted, both of them expand the values of the array
  > to separate words

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

* `getops`

  > `getopts` takes two arguments. The first is a string that can contain
  > letters and colons. Each letter is a valid option; if a letter is followed
  > by a colon, the option requires an argument. `getopts` picks options off
  > command line and assigns each one (without the leading dash) to a variable
  > whose name is `getopts`’s second argument. As long as there are options
  > left
  > to process, `getopts` will return exit status `0`; when the options are
  > exhausted, it returns exit status 1, causing the while loop to exit.

* `while` vs `until`

  > In while, the loop executes as long as the condition is true; in until,
  > it runs as long as the condition is false.

* use `IFS` - internal field separator
  `TAB`, `LINEFEED` and `space` by default

* process ids are for system, jobs are for bash session

  * `^C` - INT
  * `^Z` - TSTP
  * `^\ ` - stronger version of `^C`

  TERM > QUIT > KILL : `kill <process id>`>`kill - QUIT <process id>`>`kill -KILL <process id>`

* shell inheritance
  * inherits
    * current working directory
    * env vars
    * stdin, stdout, err, any other FDs
    * ingored signals
  * doesn't inherit
    * shell vars, excpt env vars

## cmds

* `type -a <cmdname>` - show all exec of <cmdname>
* `basename` and `dirname`
* `builtin <SHELL-BUILTIN>` - run shell built-in inside another function

* `command` - shell built-in, disables alias and function lookup

* `shift <number>`

  > `shift 1` makes `$2` to become `$1`, etc

* `$ [ \(...\) ]` then ` $(( ... ))` then `(( ... ))` to test arithmetics

* `for (( init ; ending condition ; update ))`

  `for ((;;))` - endless loop
