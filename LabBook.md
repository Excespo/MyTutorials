# Handbook by Excespo

# Unsolved

Tikz plotting problem

Jupyter2latex

# SSH: Lab
`ssh -p 51601 yijie@202.120.55.134`

123456

# VPN
expressVPN

password with a _ end

activation with ED2KAKG9KOGG9XV5CW6A9F5
(or goto website to copy)

# Vscode sftp with lab (__DANGER__)
vscode 使用sftp上传文件夹：

ctrl+shift+p sftp:config

local -> remote

uploadOnSave务必设置为false否则保存时会遇到文件丢失

最好只用在第一次上传文件，其余时候使用git实现同步，这个插件年久失修，非常不经考验

最好不用

# Git
## local configure
git本机设置:
 - `$ git config --global user.name "Your Name"`
 - `$ git config --global user.email "email@example.com"`

## procedure for new project
git new repo设置:(win ver)

先在github上create a new repository with readme.md, license, .gitignore

然后选定本地文件夹 `git bash it`
```git
git init
git add README.md
git commit -m'first commit'
git branch -M main
git remote add git@github:xxx
git push -u origin main
```

## git for new machine
git ssh设置(linux ver.)

 - `cd ~/.ssh`
 - `ssh-keygen` (无需其他参数)
 - .ssh下的id_rsa.pub放入github
 - touch config 写入Host github.com HostName github.com user git IdentifyFile ~/.ssh/id_rsa
 - `ssh -T git@github.com` 验证ssh是否设置成功
 - ssh有时效，可能需要再次设置

## conclusion
git最好是先在github上建好repo然后用git@github clone下来 然后add commit push

在vscode中add操作是自动的 然后先放入staged changes,然后按那个勾commit with comment，最后push

在本机上， clone下之后把文件复制黏贴进去，然后
```git
git add .
git commit -m git push origin main
```
注意：git add remote origin xxx添加分支

origin应该是云端主机的名称, main是分支


# Linux terminal command
linux指令
 - 查看主机名称
`$ hostname`
 - 查看主机内存情况（以Mb或Gb为单位）
`$ free -m/-g`
 - 查看CPU主频信息
`$ lscpu`
 - 查看ip地址
`$ ifconfig`
 - 查看GPU信息
`$ lspci | grep -i vga`
 - 生成文件目录 
`tree -a >tree.txt` ,win10下`cmd tree /f >tree.txt`
 - 在文件夹中
	- `rm- rf filename` 强制删除文件
	- `cd .?`或`cd ../` 回退路径
	- `cd /` 跳转至根目录 
	- `cd`或`cd ~` 跳转至家目录
	- `mkdir dirname` 生成文件夹
	- `mkdir -p dir1/dir2/dir3` 依次生成层级文件夹
	- `chmod -R 777 dirname` (7=4execute+2write+1read,三位7从高开始依次为文件所有者，群组，其他人访问权限)


# Latex

看来看去，Markdown相比较Latex更适合写一些简单的演示文稿，不能写复杂的笔记。要写笔记还是Latex比较合适，功能也齐全。

## 1. Texlive
Tex live是一个封装好的发行版，反正下载就完事了 [Source](https://tug.org/texlive/)

找到 [ISO image](https://tug.org/texlive/acquire-iso.html) 然后下载一个`.iso`出来， 或者就正常点下载本地installer也行

然后开始安装，我选择装在D盘是因为平衡两边的用量。然后慢慢等着（这次安装没有注意可选项，是一路next过来的，下次可以注意一下）

用`tex -version`验证是否安装成功， `latex -version`查看pdfTex的版本信息

注意添加系统变量，但是windows应该是自己添加好了`.../bin/win32`

## 2.VScode & Latex
安装插件`Latex Workshop`，开始忙碌的`settings.json`
要重新写settings的话，可以参考官方文档，写的比较清楚。还有

recipe和tools竟然有default的一些用法，和博客里写的不完全一致。
这次想自己配置，就没照抄博客。特别是tools和recipe的板块，是按插件的默认配置写进去的。

删除编译文件要配置进去，不然一大堆东西不美观就是。应该是要留下synctex不然不能双向搜索

## 3.语法
第一次写犯病了，documentclass和author,date,title都没加上就狂点编译，果真是没有markdown那么简单，但是也确实犯病了。

开在brower里的pdf竟然也不是edge的pdf浏览器。。tab里的vscode自带的pdf浏览器支持了双向搜索很爽。`Ctrl+Alt+J`正向，反向就`Ctrl+Click`很爽啊。

## 4.使用模板

# Anaconda
 - 0. 历史错误问题一览
	- 2021/4/20 各种plot函数一运行就内核崩溃，日志仅有'no such comm'，网络无解决方案，尝试批量更新所有包失败，大概是把包搞坏了，于是重装

 - 1. 卸载anaconda
直接everything找到卸载程序
 - 2. 重新安装anaconda
,官网
 - 3. 安装过程记得更改目录和勾选配置环境变量
 - 4. 配置环境变量
	- win+R sysdm.cpl
	- D:\anaconda3
	- D:\anaconda3\Library\mingw-w64\bin
	- D:\anaconda3\Library\bin
	- D:\anaconda3\Scripts
 - 5. jupyter extension
	- `pip install jupyter_contrib_nbextensions`
	- `jupyter contrib nbextension install --user`
 - 6. 默认目录路径
		jupyter notebook --generate-config
		找到c.NotebookApp.notebook_dir = 
		取消注释，写入新目录
开始>jupyternotebook>更多>属性>快捷方式>目标>删除"%USERPROFILE%/"
 - 7. 设置D:/anaconda3文件夹权限
属性>权限>完全控制（听说装在C盘就不会有这个问题）
 - 8. done

# cuda&cudnn&torch 全部重装
 - 0. C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v???\ 目录下没有找到cudnn.h
 - 1. 打开Nvidia control panel确认驱动版本465.89
 - 2. 确认要安装的模块(torch/tensorflow)与cuda,cudnn的版本对应关系
 - 3. 下载cuda11.0 toolkit(历史版本在 archive of precious CUDA Releases)，安装时尽量全部用默认设置，但是注意是否默认安装旧版本的工具模块
 - 4.  安装完毕后在cmd中运行nvcc --version
 - 5. https://developer.nvidia.com/rdp/cudnn-download 需要账号，找到对应版本下载
 - 6. 解压缩，将文件对应放入cuda的目录中
 - 7. 配置环境变量
CUDA的系统变量在安装过程中自动写入，CUDNN要手动写入系统变量path
	 - C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.1\lib\x64
 
	 - C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.1\include
 
	 - C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.1\bin
 
	 - C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.1\extras\CUPTI\libx64
 
	 - C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.1\bin\win64
 
	 - C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.1\common\lib\x64

 - 8. torch安装
pytorch官网找到`conda install`

		`conda install pytorch torchvision torchaudio cudatoolkit=11.1 -c pytorch -c conda-forge`

		开着vpn等，因为-c pytorch是从官网上面下载的，去掉以后会换成清华的镜像源，但是好像没有完整的toolkit包

 - 9. 好了

# Jetbrains

## Pycharm
没啥好说的，UI一装直接开用，字体什么一边用一遍调一下慢慢就好了。记得每个文件都有自己的configuration，这个比较逆天，有的时候会忘

## Pycharm & SSH
`tools->deployment->configuration`+`python intepreter`
映射一般不会出问题，记得设置就好。有问题就删了重来，不玩花的。

## Pycharm & Jupyter Notebook
没ipynb用真的挺煎熬的，有以下步骤

- 设置`jupyter notebook`密码并获取token
  ```bash
  $ ipython
  In[1]: from notebook.auth import passwd
  In[2]: p = passwd()
  Out[2]: Entry password:
			Verify password:
  In[3]: print(p)
  ```
  此处的p是生成的token,形如
  ```
  argon2:$argon2id$v=19$m=10240,t=10,p=8$Fq5mTA5JzdbKo4Zbk//BEQ$NQvTDsivgU4zCwI+BXt+uQ
  ```

- 生成并修改配置文件
	```bash
	jupyter notebook --generate-config
	```
	配置文件的位置一般在`/.jupyter/jupyter_notebook_config.py`，找到并修改如下项：
	```py
	c.NotebookApp.token = u'sha:token'
  	c.NotebookApp.ip = '*' 
  	c.NotebookApp.port = '8888'
	c.NotebookApp.open_brower = False
	c.NotebookApp.allow_remote_access = True
	```
	其中token为之前生成的字符串

- 打开jupyter
	```bash
	jupyter notebook
	```
	在其中找到
	```bash
	Jupyter Notebook 6.4.4 is running at:
	[I 16:12:08.013 NotebookApp] http://speit01:8889/?token=...
	[I 16:12:08.013 NotebookApp]  or http://127.0.0.1:8889/?token=...
	```
	以上就是服务器的jupyter内核运行的url，你可以复制下来，拼接上token在本机的浏览器上打开，但是目录文件的地址是`/.jupyter/`,这显然是不可接受的。应该也可以通过`config.py`文件中的某一项修改。但是由于我们要用pycharm打开Jupyter，就不纠结了

	__关于Jupyter后台运行的问题__`nohup jupyter notebook&`还没试过效果

- 从Pycharm打开
	.ipynb中找到大大的`configure jupyter server->configured server` 第一次要输入password，但是可以remember很好

到这里基本上就结束了 遇到了问题是好像没有选用合适的python内核

- 第二次打开
	第二次打开在ssh session里发现url变了，接上token后显示`error: jupyter server malformed`



## CLion
先是熟悉的`settings->tools->ssh configuration`,然后是不熟悉的`build,execution,deployment->toolchains->+ remote host` 然后移上去当default
于是他说我cmake版本太低了，寄 然后有点不敢删cmake
鉴于不是很吃资源 其实用local的MingGW也可以吼



-------------------------------------------------

# CACHE FRANCAISE
