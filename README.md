skywalker-vim
=============
1.基本配置文件
请参看~/.vimrc文件

2.实用brew install ctags安装ctags

3.安装taglist

4.安装pydiction
pydiction用来实现代码补全和语法提示功能。pydiction不能通过apt安装，需要自行下载安装。
在vim官网下载zip包，然后自行解压。下载地址为：http://www.vim.org/scripts/script.php?script_id=850
python_pydiction.vim: vim插件文件。complete-dict: 一个字典文件，包含了Python的关键字和模块。插件引用的内容即来自于此。pydiction.py: 一个py脚本，运行此文件可以增加新的模块到complete-dict字典中。
进入解压后的pydiction目录$ cp after/ftplugin/python_pydiction.vim ~/.vim/after/ftplugin
$ cp complete-dict ~/.vim
$ cp pydiction.py ~/.vim

5.编辑配置文件
let Tlist_Auto_Highlight_Tag=1  
let Tlist_Auto_Open=1  
let Tlist_Auto_Update=1  
let Tlist_Display_Tag_Scope=1  
let Tlist_Exit_OnlyWindow=1  
let Tlist_Enable_Dold_Column=1  
let Tlist_File_Fold_Auto_Close=1  let Tlist_Show_One_File=1  let Tlist_Use_Right_Window=1  let Tlist_Use_SingleClick=1  nnoremap <silent> <F8> :TlistToggle<CR>   filetype plugin on  autocmd FileType python set omnifunc=pythoncomplete#Complete  autocmd FileType javascrīpt set omnifunc=javascriptcomplete#CompleteJS  autocmd FileType html set omnifunc=htmlcomplete#CompleteTags  autocmd FileType css set omnifunc=csscomplete#CompleteCSS  autocmd FileType xml set omnifunc=xmlcomplete#CompleteTags  autocmd FileType php set omnifunc=phpcomplete#CompletePHP  autocmd FileType c set omnifunc=ccomplete#Complete        let g:pydiction_location='~/.vim/tools/pydiction/complete-dict'  set autoindentset tabstop=4  set shiftwidth=4  set expandtab  set number
6.安装Pathogen.vim

　　　　简介：pathogen.vim是一个方便操作"runtimepath", "path", "tags"等的插件，安装了pathogen.vim后，可以非常方便地下载安装其他vim插件。
　　　　下载：http://www.vim.org/scripts/script.php?script_id=2332 或 https://github.com/tpope/vim-pathogen
　　　　安装：
　　　　　　首先，在vim runtime目录下创建两新目录 ~/.vim/autoload 和 ~/.vim/bundle。
$ mkdir -p ~/.vim/autoload ~/.vim/bundle
　　　　　　其次，拷贝源包中 autoload/pathogen.vim 到 ~/.vim/autoload 目录下。
$ cp autoload/pathogen.vim ~/.vim/autoload/pathogen.vim
　　　　　　然后，在.vimrc文件中写入以下代码：
execute pathogen#infect()
　　　　　　至此，pathogen.vim便安装完成了。此后所有vim插件目录可以解压到 ~/.vim/bundle 中， 它会被自动追加到"runtimepath"中。
7.安装代码高亮显示

简介：对代码进行高亮显示。
　　　　下载：http://www.vim.org/scripts/script.php?script_id=1599
　　　　安装：
　　　　　　将下载的highlight.vim拷贝到 ~/.vim/plugin 目录下。
$ cp highlight.vim ~/.vim/plugin
　　　　　　高亮搜索结果命令 :set hlsearch，使用命令 :hi Search查看高亮背景色，默认棕黄色，更改高亮背景色命令 :hi Search guibg=LightBlue。
　　　　　　临时关闭高亮命令 :nohlsearch，该命令可简写为 :noh。
　　　　　　可以配置.vimrc，使用空格键临时关闭搜索结果高亮，在.vimrc写入：
:nnoremap <silent> <Space> :nohlsearch<Bar>:echo<CR>
　　　　　　要关闭搜索结果高亮，使用命令 :set nohlsearch。同样可以配置.vimrc来使用快捷键（F4）快速关闭和开启搜索结果高亮，在.vimrc写入：
:noremap <F4> :set hlsearch! hlsearch?<CR>
　　　　　　要默认关闭搜索结果高亮，在.vimrc写入：
set viminfo^=h
　　　　　　（更多参考 http://vim.wikia.com/wiki/Highlight_all_search_pattern_matches）
　　　　　　  (如何高亮单行 http://vim.wikia.com/wiki/Highlight_current_line）
8.NERDTree目录树
简介：打开文件目录树，相当于文件浏览器。
　　下载：http://www.vim.org/scripts/script.php?script_id=1658
　　安装：

　　　　将整个解压后的源包拷贝到 ~/.vim 目录下，需要确保 NERD_tree.vim 位于 ~/.vim/plugin 目录下， NERD_tree.txt 位于 ~/.vim/doc 目录下。
　　　　使用<F7>作为快捷键开关目录树，在.vimrc写入： 
map <F7> :NERDTreeToggle<CR>

9.自动补全

简介：可以对常用词进行提示补全。
　　下载：http://www.vim.org/scripts/script.php?script_id=1879 或 https://bitbucket.org/ns9tks/vim-autocomplpop/get/tip.zip
　　安装：
　　　　拷贝acp.vim 到 ~/.vim/plugin 目录下，拷贝acp.txt到~/.vim/doc 目录下。
　　【注意】 该插件有一个依赖对象l9.vim，所以还需要安装l9.vim插件。
10.l9.vim

简介：自动补全AutoComplPop的依赖库。
　　下载：http://www.vim.org/scripts/script.php?script_id=3252
　　安装：
　　　　将源包目录置于vim运行时目录下，确保 l9.vim 处于 ~/.vim/plugin 目录下， l9.txt 处于 ~/.vim/doc 目录下。
11.安装后的问题
Taglist : Failed to Generate tags for xxxxx 
ctags : illegl option -- ^- 
,原来taglist只支持exuberant ctags tool,不支持GNU　ctags或UNIX ctags,mac下自带的不是exuberant　ctags,所以就会有问题了,解决办法也很简单,下载exuberant ctags tool,然后装在一个与系统自带的ctags不冲突的路径下,然后在.vimrc里加一行let Tlist_Ctags_Cmd = '/path/to/ctags'就可以了.

解决方案：
编辑~/.bash_profile文件, 添加一行MAC环境下的环境变量设置在.bash_profile中。 
export PATH=/usr/local/bin:$PATH 
let Tlist_Ctags_Cmd = '/usr/local/bin/ctags’

