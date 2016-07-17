<!-- vim -->
\pagebreak

General ex command line <!-- {{{1 -->
=======================
- `set {option1} {option2}` : issue two set commands (same for setlocal)
    - `set cursorline! hlsearch!`
- `{command1} | {command2}` : issue two ex commands in one line
    - `echo 'hello' | set ruler!`
- `exe {string}` : run the string as an ex command line
    - `exe 'set colorcolumn='.(40+20)`
- `redraw!` : sometimes the vim rendering is corrupted, run this will force vim to redraw
- `q:` : opens command history window
- `put =expression` : evaluate the expression, paste the result and enter normal mode
    - `put =1+2`

\pagebreak

Editing in ex command line <!-- {{{1 -->
==========================
- `<c-r><c-a>` : Pull <CWORD> onto search/command line
- `<c-r><c-w>` : Pull <cword> onto search/command line
- `<c-r>{register}` : Pull the content of {register} onto search/command line
    - `<c-r>/` : last search
    - `<c-r>:` : last ex command
    - `<c-r>@` : last yanked
    - `<c-r>%` : file name

\pagebreak

Vim-shell interactions <!-- {{{1 -->
======================
- `sh` : open a temporary shell, return to vim upon its exit

\pagebreak

Buffer management <!-- {{{1 -->
=================
- `badd {file_name}` : add {file-name} to the buffer list without opening it
    - `badd resources/a`

\pagebreak

File operation <!-- {{{1 -->
==============
- `:edit!` / `:e!` : reload current buffer from disk
- `:E` / `:e.` / `:e .` : open the current directory in netrw
- `X` : crypt the current file
    - `e resouces/encryptme`
    - write something
    - `X`
- `:find {pattern}` : open the file that matches pattern, if multiple files are present it fails
  with message **E77: Too many file names**
    - `find **/*foundm*`
- `enew` : open a new unnamed buffer
- `vnew` : open a new unnamed buffer in the vertical split
- `w {file}` / `write {file}` : save the current buffer to file and remind in the current file
    - `write! resources/write`
        - we are still at vim.md
- `w {file}` / `write {file}` : also works with visual selection
    - visually select a chunk
    - `write! resources/xwrite`
        - we are still at vim.md, with the visually selected piped to the content of xwrite
- `sav {file}` / `saveas {file}` : save the current buffer to file and switch to that file, doesn't
  work with visual selection
    - `sav resources/saveas`
        - we are now at resources/saveas
- `r {file}` / `read {file}` : paste the content of {file} here
    - `read resources/xwrite`
- `r! {command}` : run shell command {command}, paste the output here
    - `r!ls -al`
- `TOhtml` : print the current file (or visual selection) to an html file named **%.html**
    - `TOhtml`
    - `w resources/vim.md.html`
    - `!open resources/vim.md.html`

\pagebreak

Visual selection mode <!-- {{{1 -->
=====================
- `g?` : turn selected text into gibberish

\pagebreak

Mark <!-- {{{1 -->
====
    :marks : print the active marks list

    ma : place a mark a
    'a : move to the ^ of the line of mark a
    `a : move to the exact location of mark [a-z]

    mA : place a mark A that can be accessed from anywhere
    'A : move to the ^ of the line of mark A in any file
    `A : move to the exact location of mark A in any file

    `. : move to the last edit
    '. : move to the ^ of the last edit

    `` : position before the last jump within current file
    '` : the ^ of position before the last jump within current file

    `^ : location of last insertion
    '^ : the ^ of last insertion

    `[ : start of last change or yank
    '[ : the ^ of start of last change or yank

    `] : end of last change or yank
    '] : the ^ of end of last change or yank

    `< : start of last visual selction
    '< : the ^ of start of last visual selction

    `> : end of last visual selection
    '> : the ^ of end of last visual selection
