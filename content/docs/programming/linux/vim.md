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

## 基础操作

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

