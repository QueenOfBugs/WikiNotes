
### 将行首TAB(换行符)全部替换成空格(space)

```vim
:%ret!
```

`:help ret`查看具体用法

### 删除行尾空格

```vim
:%s/\s*$//g
```

替换命令的格式`:[range]s[ubstitute]/{pattern}/{string}/[flags] [count]`

- `[range]`: means line range . See: `:help cmdline-ranges` or `:h [range]`
- `s[ubstitute]`: a Ex cmd . See `:help :s`or`:help :su`or`:help :substitute`
- `pattern`: See `:help pattern`
- `String`: Can be a literal string , or something special; See `:help sub-replace-special`
- `[flags]`: See `:help :s_f` or `:help :s_flags`

### 删除行首空格

```vim
:%s/^\s//g
```

