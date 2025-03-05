# Vim Cheat Sheet

## Global
- `:h[elp] keyword` - open help for keyword
- `:sav[eas] file` - save file as
- `:clo[se]` - close current pane
- `:ter[minal]` - open a terminal window
- `K` - open man page for word under the cursor
- **Tip:** Run `vimtutor` in a terminal to learn the first Vim commands.

---

## Cursor Movement
- `h` - move cursor left
- `j` - move cursor down
- `k` - move cursor up
- `l` - move cursor right
- `gj` - move cursor down (multi-line text)
- `gk` - move cursor up (multi-line text)
- `H` - move to top of screen
- `M` - move to middle of screen
- `L` - move to bottom of screen
- `w` - jump forwards to the start of a word
- `W` - jump forwards to the start of a word (words can contain punctuation)
- `e` - jump forwards to the end of a word
- `E` - jump forwards to the end of a word (words can contain punctuation)
- `b` - jump backwards to the start of a word
- `B` - jump backwards to the start of a word (words can contain punctuation)
- `ge` - jump backwards to the end of a word
- `gE` - jump backwards to the end of a word (words can contain punctuation)
- `%` - move cursor to matching character (pairs like '()', '{}', '[]')
- `0` - jump to the start of the line
- `^` - jump to the first non-blank character of the line
- `$` - jump to the end of the line
- `g_` - jump to the last non-blank character of the line
- `gg` - go to the first line of the document
- `G` - go to the last line of the document
- `5gg` or `5G` - go to line 5
- `gd` - move to local declaration
- `gD` - move to global declaration
- `fx` - jump to next occurrence of character `x`
- `tx` - jump to before next occurrence of character `x`
- `Fx` - jump to previous occurrence of character `x`
- `Tx` - jump to after previous occurrence of character `x`
- `;` - repeat previous `f`, `t`, `F` or `T` movement
- `,` - repeat previous `f`, `t`, `F` or `T` movement, backwards
- `}` - jump to next paragraph (or function/block, when editing code)
- `{` - jump to previous paragraph (or function/block, when editing code)
- `zz` - center cursor on screen
- `zt` - position cursor on top of the screen
- `zb` - position cursor on bottom of the screen
- `Ctrl + e` - move screen down one line (without moving cursor)
- `Ctrl + y` - move screen up one line (without moving cursor)
- `Ctrl + b` - move screen up one page (cursor to last line)
- `Ctrl + f` - move screen down one page (cursor to first line)
- `Ctrl + d` - move cursor and screen down 1/2 page
- `Ctrl + u` - move cursor and screen up 1/2 page
- **Tip:** Prefix a cursor movement command with a number to repeat it (e.g., `4j` moves down 4 lines).

---

## Insert Mode - Inserting/Appending Text
- `i` - insert before the cursor
- `I` - insert at the beginning of the line
- `a` - insert (append) after the cursor
- `A` - insert (append) at the end of the line
- `o` - append (open) a new line below the current line
- `O` - append (open) a new line above the current line
- `ea` - insert (append) at the end of the word
- `Ctrl + h` - delete the character before the cursor during insert mode
- `Ctrl + w` - delete word before the cursor during insert mode
- `Ctrl + j` - add a line break at the cursor position during insert mode
- `Ctrl + t` - indent (move right) line one shiftwidth during insert mode
- `Ctrl + d` - de-indent (move left) line one shiftwidth during insert mode
- `Ctrl + n` - insert (auto-complete) next match before the cursor
- `Ctrl + p` - insert (auto-complete) previous match before the cursor
- `Ctrl + rx` - insert the contents of register `x`
- `Ctrl + ox` - temporarily enter normal mode to issue one normal-mode command `x`
- `Esc` or `Ctrl + c` - exit insert mode

---

## Editing
- `r` - replace a single character
- `R` - replace more than one character until `ESC` is pressed
- `J` - join line below to the current one with one space in between
- `gJ` - join line below to the current one without space in between
- `gwip` - reflow paragraph
- `g~` - switch case up to motion
- `gu` - change to lowercase up to motion
- `gU` - change to uppercase up to motion
- `cc` - change (replace) entire line
- `c$` or `C` - change (replace) to the end of the line
- `ciw` - change (replace) entire word
- `cw` or `ce` - change (replace) to the end of the word
- `s` - delete character and substitute text (same as `cl`)
- `S` - delete line and substitute text (same as `cc`)
- `xp` - transpose two letters (delete and paste)
- `u` - undo
- `U` - restore (undo) last changed line
- `Ctrl + r` - redo
- `.` - repeat last command

---

## Marking Text (Visual Mode)
- `v` - start visual mode, mark lines, then do a command (like `y` to yank)
- `V` - start linewise visual mode
- `Ctrl + v` - start visual block mode
- `o` - move to other end of marked area
- `O` - move to other corner of block
- `aw` - mark a word
- `ab` - a block with `()`
- `aB` - a block with `{}` 
- `at` - a block with `<` tags
- `ib` - inner block with `()`
- `iB` - inner block with `{}` 
- `it` - inner block with `<` tags
- `Esc` or `Ctrl + c` - exit visual mode
- **Tip:** Instead of `b` or `B`, use `(` or `{}` respectively.

---

## Visual Commands
- `>` - shift text right
- `<` - shift text left
- `y` - yank (copy) marked text
- `d` - delete marked text
- `~` - switch case
- `u` - change marked text to lowercase
- `U` - change marked text to uppercase

---

## Exiting
- `:w` - write (save) the file, but don’t exit
- `:wq` or `:x` or `ZZ` - write (save) and quit
- `:q` - quit (fails if there are unsaved changes)
- `:q!` or `ZQ` - quit and throw away unsaved changes

____
Tags : #programming #text-editor