# NeoVim Script

## Basic

### Variable Types:



#### Numbers:

**1. decimal**

**2. hexadecimal**

Starts with "0x" or "0X"

**3. octal**

Starts with "0", ex: 015 = 13

#### String

Within '' or ""

escap character: '\'

	\t - <Tab>
	\n - <NL>
	\r - <CR>,<Enter>
	\e - <Esc>
	\b - backspace
	\<Esc> - <Esc>
	\<C-W> - CTRL-W
	and more:
	https://neovim.io/doc/user/eval.html#expr-quote


### Operator:

! - not
+, -, *, /, %, +=
. - concantenate strings
=~ - string match with
!~ - string does not match with
a ? b : c - if a then b, else then c  


### Declaration:

:let {variable} = {expression}

* variable name consists of ASCII letters, digits and the underscore, can't start with a digit.

:let s:{variable} = {expression}

* "s:" indicate the variable is only used within this script file.
		
		b:name variable local to a buffer
		w:name variable local to a window
		g:name global vairable (also in a function)
		v:name variable predefined by Vim
	
* $NAME - environment variable
* &name - option
* @r - register

### Conditionals

:if {condition}
	{statements}
:elseif {condition}
	{statements}
:else
	{statements}
:endif

### Iteration:

:while {condition}
:  {statements}
:  break
:endwhile

## Frequently Used Functions:

* echo -- prints its arguments
* range(m, n) -- [m, m+1, ..., n]
* let -- declare variables; see a list of currently defined variables 
* unlet -- delete variables
* exists() -- check if a variable has already been defined

## Subtle:

* automatically convert string to number if looking for, if first character if not digit, it converts to 0.