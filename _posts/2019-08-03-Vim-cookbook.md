---
title: 'Vim cookbook'
date: 2019-08-03
modified: 2019-08-03
permalink: /posts/2019/08/Vim-cookbook/
tags:
 - cookbook
excerpt_separator: <!--more-->
---

This is a cheatsheet for vim commands and operations.
<!--more-->

## Configuration

### Display line numbers

- in the current file

```
:set number # to enable line numbers
:set nonumber # to disable line numbers
```

- to change config

 add `set number` in `~/.vimrc`

## Navigating

### Basic movement

- `h` move to the left by one position

- `l` move to the right by one position

- `j` move to the downward direction by one line

- `k` move to the upward direction by one line

### Inline movement

- `b` move to the start of the current word

- `e` move to the end of the current word

- `w` move to the start of the next word

**Info:** combine movement with a number, e.g. `3w`, `9k` is the same as pressing `w` three times, pressing `k` nine times, respectively.
{: .notice--info}

- `^` move to the first non-blank character

- `g_` move to the last non-blank character

- `n + Space` move to the nth character of the current line

- `0` move to the **start column** of the current line

- `$` move to the **end column** of the current line

### Text movement

- `+` move to the first non-blank character of the next line

- `-` move to the first non-blank character of the previous line

- `:n` jump to the nth line

- `:+n` or `n + Enter` jump down n lines

- `:-n` jump up n lines

- `gg` or `:0` move to the **first line** of the file 

- `G` or `:$` move to the **end line** of the file

**Info:** combine movement with a number, e.g. `3G` move to the third line of the file
{: .notice--info}

### screen movement

- `ctrl + e` scroll down a line

- `ctrl + y` scroll up a line

- `ctrl + d` scroll down the half of page

- `ctrl + u` scroll up the half page

- `ctrl + f` or `Page down` scroll down the entire page

- `ctrl + b` or `Page up` scroll up the entire page

- `ctrl + o` jump to the previous position

- `ctrl + i` jump to the next position


## Editing

### Insert

- `i` insert the text before the cursor

- `I` insert the text at the beginning of the line

### Open a new line

- `o` open new line below the cursor

- `O` open new line above the cursor

### Append

- `a` append the text after the cursor

- `A` append the text at the end of line

### Delete

- `x` delete the character on the cursor

- `X` delete the character before the cursor

- `dw` delete a word beginning at the cursor

- `d0` delete from the beginning of current line to the cursor position (including current character)

- `d$` delete from current position to the end of the line (including current character)

- `D` delete entire line beginning at the cursor

- `dd` delete entire line，

- `d1G` delete from the first line to the current line (including current line)

- `dG` delete from the current line to the end (including current line)

**Info:** combine movement with a number, e.g. `3dw` delete 3 words at a time, `4D` delete 4 lines at a time
{: .notice--info}

**Mention:** all of these commands is will 'cut' the text to the clipboard, so the following `p` will works!
{: .notice--warning}

### Delete and insert

- `s` delete the character under the cursor and switch to insert mode

- `S` delete the whole line and switch to insert mode

- `C` delete the following text after the cursor and switch to insert mode

### Replace

- `r` replace the character on the cursor but not switch to insert mode

- `R` replace the following text

### Copy & Paste

- `y` copy a single character on the cursor

- `yy` copy entire line

- `p` paste text after the cursor

- `P` paste text before the cursor

**Info:** combine movement with a number, e.g. `3yy` copy the following three lines including the current line
{: .notice--info}

### Join lines

- `J` remove the `line breaks` to `whitespace`

**Info:** combine inserting with a number, e.g. `5igo` + `Esc` wil insert 'go' five times
{: .notice--info}

### Undo & Redo

- `u` undo single action

**Info:** combine inserting with a number, e.g. `3u` will undo action five times
{: .notice--info}

- `ctrl + r` redo single action

## Searching

### Inline searching

- `f<char>` jump to the next occurrence of `<char>`

- `t<char>` jump before the next occurrence of `<char>`

**e.g. delete until specified char:** `dt"` delete text until `"`
{: .notice--success}

### Global searching

- `*` search the next occurrence of the word cursor on

- `#` search the previous occurrence of the word cursor on

- `/<expression>` search the expression in forward direction

- `?<expression>` search the expression in backward direction

- `n` find the next/previous occurence in `/<expression>`/`?<expression>`

- `N` find the previous/next occurence in `/<expression>`/`?<expression>`

- `//` repeat the previous searching

## Advance

### Replace

- `:<line1>,<line2>s/<word1>/<word2>/g` replace `word1` with `word2` between `line1` and `line2`, flag `g` refers to global

- `:%s/<word1>/<word2>/gc` replace `word1` with `word2` to the whole text, `%` means for every line, flag `gc` refers to global and need confirmation

- `ddp` swap the current line to the next one

### Visual mode

- `v` switch to visual mode

**e.g. delete the whole word:** `v` for visual mode, `e` jump to the end of the current word, `d` to delete
{: .notice--success}

### Visual block mode

- `ctrl + v` switch to visual block mode

**e.g. Comment quickly:** `ctrl + v` for block mode, select some lines, `I` to insect at the beginning of each line, input the annotation symbol, `Esc` twice finally comment several lines quickly
{: .notice--success}

- `:10,20s#^#//#g` comment `//` from line 10 to line 20

- `:10,20s#^//##g` uncomment `//` from line 10 to line 20

- `:10,20s/^/#/g` comment `#` from line 10 to line 20

- `:10,20s/^#//g` uncomment `#` from line 10 to line 20

- `:%s/$/\r/g` add a newline to each line

### Others

- `:! <command>` run the command and show the output outside of vim environment
