## Useful Linux Operations

Move file in batch

```shell
mkdir folder
mv * folder
```

Remove suffix in batch

```shell
for file in suffix_*; do 
	mv $file ${file$suffix_} 
done
```

<br>

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

### (2) Operations

- Open multiple files related

  - Display `:ls` 
  - Switch `:bn`, `:bp`, `:b1[2,3,4,...]` 

  - Split window `:vsplit`, `:split` 
  - Moving between windows `Ctrl W [hjkl]` 
  - Open a new file `:e file` 

- System command: `:!<cmd>` 

- Insert: 
  - Enter insert mode `i`, `I` 
  - Enter insert mode `a`, `A` 
  - Enter insert mode `o` 
  - Enter insert mode `s`, `S` 

- Change:
  - Char level `r`, `s` 
  - Word level `cw` 
  - Line level `cl`, `S` 

- Delete: 
  - Char level `x` 
  - Word level `dw`, `d2w`, ...
  - Line level `dd`, `d2d`, ...
  - Line level further: `d$` 
  - Line level further: `d^` 

- Yank, Paste and Undo
  - Char level yank `y` 
  - Word level yank `yw` 
  - Line level yank `yy`, `y2y`,...
  - Line level yank further: `y$` 
  - Line level yank further: `y^` 
  - Paste `p` 
  - Undo `u` 

- Move: 
  - Char level `h`, `j`, `k`, `l` 
  - Word level `w`, `b`, `e`, `ge` 
  - Line level `0`, `$`, `f<char>`, `T<char>` 
  - Line level further: Forward to a char within line `f<char>` 
  - Line level further: Backward to a char within line `T<char>` 
  - Line level further: Move to line n `<n>|`

- Jump: 
  - Paragraph level `}`, `{` 
  - Block level `]] `, `[[`, `]m`, `[m` 
  - Screen level `Ctrl-U`, `Ctrl-D` 
  - File level `:<line num>`, `gg`, `G` 
  - Search `/pattern`, `?pattern` 
  - Furward and backward `Ctrl-o`, `Ctrl-i` 

- Replacement:
  - Line level `:s/foo/bar/gc` 
  - File level `:%s/foo/bar/gc` 
  - File level `:%s/foo/bar/gc` 


