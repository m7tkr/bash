20230101081808

# bash notes

## important links
https://porkmail.org/era/unix/award

## lazy on notes, so search bash

* file attributes
* parameter expansion
* string comparison
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

* `if`
  * `if` operates on *exit status*
  * `[]` vs `[[]]`
    > word splitting and pathname expansion are not performed inside single brackets 

* test arithmetics
  * `$ [ \(...\) ]` then ` $(( ... ))` then `(( ... ))`

* `while` vs `until`

  > In while, the loop executes as long as the condition is true; in until,
  > it runs as long as the condition is false.

* `IFS` - internal field separator
  * `TAB`, `LINEFEED` and `space` by default

* process ids are for system, jobs are for bash session
  * `^C` - INT
  * `^Z` - TSTP
  * `^\ ` - stronger version of `^C`
  * TERM > QUIT > KILL 
    1. `kill <process id>`
    2. `kill - QUIT <process id>`
    3. `kill -KILL <process id>`

* shell inheritance
  * inherits
    * current working directory
    * env vars
    * stdin, stdout, err, any other FDs
    * ingored signals
  * doesn't inherit
    * shell vars, excpt env vars

* redirectors
  * `<` - takes fd from right side
  * `<<` - here-docs
  * `<<<` - here-string
