Procedure of virtual env and vscode remote and jupyter notebook 20220421

# Conda in remote

下载一个anaconda/miniconda的bash脚本，传到remote， 执行`bash xxx.sh`一路yes, 注意在.bashrc检查环境变量是否配置成功

记得重新启动terminal，否则可能没有刷新设置

# Conda with jupyter

在CS224n的做法里，直接利用提供的env.yml，执行`conda env create -f env.yml`，接着`python -m ipykernel install --user --name cs224n` 使得cs224n的虚拟环境可以运行notebook
 
不过这样是直接创建全新的环境，我已经创建了同名的虚拟环境的话就会报错了。这时候我们可以`conda env update -n=cs224n -f=env.yml`导入配置文件。另外，我使用`conda install jupyter notebook`安装的notebook套件

如何在jupyter中切换虚拟环境？配置setting中的conda path之后重启vscode，刷新设置后理应可以直接select interpreter: (cs224n)conda env

# Kill notebook?

在dcgan的demo运行完之后发现nvidia-smi仍然占用了2GB的显存，发现jupyter在后台进程没有被kill。占用资源肯定是不好的，解决方案有：

- 在nvidia-smi中有pid，找到后`kill 9 pid`，这种方法适用于处理占用显存的进程
- 选中正确的conda env后jupyter notebook stop，是否适用不清楚，但是会直接把kernel关掉并且不知道怎么正确打开
- 在conda env中`jupyter notebook` 发现竟然可以提供了可以在本地浏览器打开的url！在图形界面当然是有关闭Notebook的地方的，但是没有配置过conda env上的notebook的theme

# Jupyter notebook theme & extension

themes

```
pip install jupyterthemes

jt -t grade3 -f fira -fs 14 -cellw 90% -ofs 15 -dfs 15 -T -T
```

extensions

```
pip install jupyter_contrib_nbextensions

jupyter contrib nbextension install --user
```