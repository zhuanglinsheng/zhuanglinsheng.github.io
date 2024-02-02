## Must Known `Vim` Tricks

### (1) Settings

```
syntex on
set number
set ruler
set colorclumn=120
set list lcs=tab:\ \ 
# Note there is an extra while space after the second backslash
```

### (2) View

- System command: `:!<cmd>`.

- Open multiple files related

  - Display tabs `:ls`.
  - Switch tab `:bn`, `:bp`, `:b1[2,3,4,...]`.
  - Further: Split window `:vsplit`, `:split`.
  - Further: Moving between windows `Ctrl W [hjkl]`.
  - Further: Open a new file `:e file`.

- Screen Scrolling: 
  - With cursor moved `Ctrl-D`, `Ctrl-U`.
  - Without cursor moved `zt`, `zz`, `zb`.

- Move Cursor: 
  - Char level `h`, `j`, `k`, `l`.
  - Word level `W`, `w`, `B`, `b`, `E`, `e`, `ge`.
  - Line level `0`, `$`, `f<Char>`, `T<Char>`.
  - Line level further: Forward to a char within line `f<Char>`.
  - Line level further: Backward to a char within line `T<Char>`.
  - Line level further: Move to column n `<n>|`.

- Jump Cursor: 
  - Sentence level `)`, `(`.
  - Paragraph level `}`, `{`.
  - Block level in C src code `]] `, `[[`, `]m`, `[m`.
  - Screen level `H`, `M`, `L`.
  - Screen level `Ctrl-U`, `Ctrl-D`.
  - File level `:<line num>`, `<line num>G` `gg`, `G`.
  - Search current word `*`
  - Search `/pattern`, `?pattern`.
  - Furward and backward `Ctrl-o`, `Ctrl-i`.

### (3) Edit

- Undo: `u`.

- Same operation as previous: `.`.
  - For example, you want to change all `hello` to `hi` in the file, then
    1. Select all `hello` in the file.
    2. Keep typing `n.`.

- Insert: 
  - Enter insert mode `i`, `I`.
  - Enter insert mode `a`, `A`.
  - Enter insert mode `o`.
  - Enter insert mode `s`, `S`.

- Change:
  - Char level `r`, `s`.
  - Word level `cw`.
  - All between characters `ci<Char>`.
    - For example, to change the contents between quote in "hello world", just type `ci"`.
  - All between characters Including characters `ca<Char>`.
    - For example, to change all contents including quetes in "hi!", just type `ca"`.
  - Line level `cl`, `S`.

- Delete: 
  - Char level `x`.
  - Word level `dw`, `d2w`, ...
  - All between characters `di<Char>`.
    - For example, to delete `int` between `<int>`, just type `di<`.
  - All between characters including characters `da<Char>`.
    - For example, to delete `<int>` includint `<` and `>`, just type `da<`.
  - Line level `dd`, `d2d`, ...
  - Line level further: `d$`.
  - Line level further: `d^`.
  - Delete paragraph: `d}`.

- Yank, Paste 
  - Char level yank `y`.
  - Word level yank `yw`.
  - Between characters `yi<Char>`.
    - For example, to copy `hello` in `"hello"`, just type `yi"`.
  - Between characters including characters `ya<Char>`
    - For example, to copy `"hello"`, just type `ya"`. 
  - Line level yank `yy`, `y2y`,...
  - Line level yank further: `y$`.
  - Line level yank further: `y^`.
  - Paste `p`.

- Search:
  - Current word: `*`.
  - Regular expression based `/foo`.

- Replacement:
  - Regular expression based, within line `:s/foo/bar/gc`.
  - Regular expression based, within file `:%s/foo/bar/gc`.

