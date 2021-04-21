vim教程
======

## vim键盘映射

> vim能定制的原因之一就是vim的键盘映射特性

### 基本映射:map

- normal 模式的键盘映射

	将<kbd>-</kbd>按键映射为<kbd>x</kbd>

```vim
:map - x
```





vim插件配置
======

## vim-plug - 插件管理工具

- Installation

  将[plug.vim](https://raw.githubusercontent.com/junegunn/vimplug/master/plug.vim)放到.vim/autoload/目录下就可以了

- Commands

  | Command| Description|
  |:---:|:---:|
  |PlugInstall|install plugins|
  |PlugUpdate|install or update plugins|
  |PlugClean|Remove unlisted plugins|
  |PlugUpgrade|Upgrade vim-plug itself|
  |PlugStatus|check the status of plugins|
  |PlugDiff|Examine changes from the previous update and the pending changes|
  |PlugSnapshot|Generate script for restoring the current snapshot of the plugins|

## airline

![airline](./airline.png)

```vim
" airline
let g:airline_theme="onedark"
let g:airline_powerline_fonts = 1
let g:airline#extensions#tabline#enabled = 1
if !exists('g:airline_symbols')
    let g:airline_symbols = {}
endif
let g:airline_left_sep = ''
let g:airline_left_alt_sep = ''
let g:airline_right_sep = ''
let g:airline_right_alt_sep = ''

```

vim 光标设置
=====

### 高亮光标

```vim
" 高亮光标所在行
set cursorline
" 高亮光标所在列
"set cursorcolumn

" 高亮设置
highlight CursorLine ctermbg=darkblue
```
