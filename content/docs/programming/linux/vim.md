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

## 插件

### vim8插件管理

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

