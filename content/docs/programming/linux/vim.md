---
title: "Vim"
weight: 2
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 安装事项

### Termux中vim

要按顺序装，不然会出错：
```bash
pkg install vim
pkg install vim-python
```

## 基础操作

### vim帮助

自带入门教程
```bash
vimtutor
```

vim中打开帮助
```vim
:help
```

### 一般模式
### 编辑模式
### 底线模式

搜索替换：
```vim
# 用法
:n1,n2s/word1/word2/g
# 示例
:1,$s/word1/word2/g
:1,$s/word1/word2/gc
:50,100s/word1/word2/gc
```

## 进阶

### 快捷键绑定

`map`用于绑定快捷键，同样的还有：
 - nmap
 - vmap
 - imap

分别对应不同模式下的绑定，用法：
```vim
nmap <c-d> dd
vmap / yy
```
实现了正常模式下ctrl+d删除行，视图模式下复制行。

> imap比较特殊，它的命令无法直接执行，需要回到正常模式，再切换回插入模式。

```vim
:imap <c-d> <esc>dd
```
上面代码，实现了在插入模式下，按下ctrl+d回到正常模式，然后正常模式下执行删除行，但是留在了正常模式，要想再换回插入模式，可改为：
```vim
:imap <c-d> <esc>ddi
```

## 插件

### vim8插件管理器

创建两个文件夹：
```bash
mkdir .vim/pack/[name]/start -p
mkdir .vim/pack/[name]/opt -p
```

start是自动加载，opt是手动加载，手动加载命令：
```vim
:packadd [plugin]
```

安装插件帮助文档，每个插件都有个doc文件夹用来存放帮助文档，进入vim：
```vim
:helptags .vim/pack/[name]/start/[plugin]/doc
```

### ycm

```bash
apt install vim-gtk3 vim-addon-manager vim-youcompleteme vim-python-jedi
vam install youcompleteme python-jedi
```

### emmet-vim

写前端必备的emmet插件

```bash
git clone https://github.com/mattn/emmet-vim.git
cd emmet-vim
mkdir .vim
mkdir .vim/plugin
mkdir .vim/autoload
cp plugin/emmet.vim ~/.vim/plugin/
cp autoload/emmet.vim ~/.vim/autoload/
cp -a autoload/emmet ~/.vim/autoload/
```

### vim-airline

```bash
cd .vim/pack/[name]/start/
git clone https://github.com/vim-airline/vim-airline
```

### NERDTree

```bash
cd .vim/pack/[name]/start/
git clone https://github.com/preservim/nerdtree
```

快捷键绑定：
```vim
nnoremap <leader>n :NERDTreeFocus<CR>
nnoremap <C-n> :NERDTree<CR>
nnoremap <C-t> :NERDTreeToggle<CR>
nnoremap <C-f> :NERDTreeFind<CR>
```

### python自动对齐/代码格式化

需先从pip安装：
```bash
pip install autopep8
```

```bash
cd .vim/pack/[name]/start/
git clone https://github.com/tell-k/vim-autopep8
```

使用方法：
```vim
:Autopep8
```
可用u撤销格式化的结果

### 缩进对齐线

```bash
cd .vim/pack/[name]/start/
git clone https://github.com/Yggdroot/indentLine
```
使用方法：
```vim
:IndentLinesToggle
```

### 快捷注释

```bash
cd .vim/pack/[name]/start/
git clone https://github.com/preservim/nerdcommenter
```
暂时不会用

### 自动补充括号

```bash
cd .vim/pack/[name]/start/
git clone https://github.com/jiangmiao/auto-pairs
```


### 中文帮助文档

```vim
cd .vim/pack/[name]/start/
git clone https://github.com/yianwillis/vimcdoc
```

## 配置

### 更换主题

```vim
:colorscheme [scheme]
```

### 关闭preview
```vim
set completeopt-=preview
```

### 一键运行
```vim
map <F5> :call CompileRunGcc()<CR>
func! CompileRunGcc()
        exec "w"
if &filetype == 'c'
            exec "!g++ % -o %<"
            exec "!time ./%<"
elseif &filetype == 'cpp'
            exec "!g++ % -o %<"
            exec "!time ./%<"
elseif &filetype == 'java'
            exec "!javac %"
            exec "!time java %<"
elseif &filetype == 'sh'
            :!time bash %
elseif &filetype == 'python'
            exec "!time python %"
elseif &filetype == 'html'
            exec "!firefox % &"
elseif &filetype == 'go'
    "        exec "!go build %<"
            exec "!time go run %"
elseif &filetype == 'mkd'
            exec "!~/.vim/markdown.pl % > %.html &"
            exec "!firefox %.html &"
endif
    endfunc
```
