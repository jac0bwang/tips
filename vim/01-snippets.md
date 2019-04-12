# Vim snippet 小技巧

要使用 vim snippet 要经过下面几个步骤：

## 1. 为自己的 vim 添加 snippet 插件

使用 vim snippet 的话首先要在自己的 `~/.vimrc` 添加如下的2个插件内容：

```vim
Plugin 'SirVer/ultisnips'
Plugin 'honza/vim-snippets'


" 下面是相关的配置信息
let g:UltiSnipsExpandTrigger = "<tab>"
let g:UltiSnipsListSnippets = "<c-tab>"
let g:UltiSnipsJumpForwardTrigger = "<tab>"
let g:UltiSnipsJumpBackwardTrigger = "<s-tab>"

" If you want :UltiSnipsEdit to split your window.
let g:UltiSnipsEditSplit="vertical"
let g:UltiSnipsSnippetDirectories=[$HOME.'/.vim/UltiSnips']
```

然后就可以到自己的目录下查看都是有什么缩写的代码片段了，在下面的目录中存放了很
多已经写好的关于相关语言的配置，可以直接使用的

```bash
ls ~/.vim/bundle/vim-snippets/snippets/*.snippets
```

也可以在 `~/.vim/` 下创建一个文件夹为 `UltiSnips` 用来存放我们自定义的补全，创
建一个文件名为 `xxxx.snippets` 的文件，这个 `xxxx`即会在某个具体的语言生效。
比如，需要创建一个用来补全 C 语言的文件，那文件名就是 `c.snippets`，创建一个用来
补全 Cpp 的文件，那文件名就是 `cpp.snippets`


## 2. 如何写属于自己的代码片段呢？

首先要符合 snippet 的语法规则，那它的规则是什么样的呢？

```bash
snippet trigger_word [ "description" [ options ] ]

snippet 缩写 [ “描述” [选项] ]
code
endsnippet
```

在使用中很少去设置 options 字段，如果有需求可以查看帮助文档 
`:help UltiSnips-snippet-options`

## 3. snippet 使用

有了前面的设置就可以在自己的代码用使用相应的缩写字段进行补全，可以加速编写代码的速度

```snippets
snippet main                              
    int main(int argc, const char *argv[])
    {                                     
        ${0}                              
        return 0;                         
    }                                     
```

对于上面的代码片段来说，在使用时只需要在 输入 `main` 之后按下 `tab` 键就可以补全
其中管标会自动定位到 `${0}` 的位置，进行后续的代码输入，非常方便

对于如下有多个变量的代码片段来说，可以在输入完第一个区域后使用 `tab` 键跳转到
下一个位置的区域接着输入， 这个 `tab` 键是可以设置的，在第一步的时候是要进行相应的设置的

```
# for                                                 
snippet for                                           
    for (int ${2:i} = 0; $2 < ${1:count}; $2${3:++}) {
        ${4}                                          
    }                                                 
```
