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

## Must Known Vim Tricks

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

- Insert: `i`, `I`, `a`, `A`, `o` 

- Move: 
  - Basic: `h`, `j`, `k`, `l` 
  - Further: `e`, `0`, `$` 
  - Furthermore: `Ctrl-U`, `Ctrl-D` 
- Jump: `Ctrl-O`, `:<line num>`, `/word`, `gg`, `G` 

