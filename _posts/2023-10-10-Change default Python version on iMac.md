# 更改iMac中默认python版本

事情起因：数据处理需要使用antspy做N4 bias correction. 于是打开指定的环境pip install antspyx，然后运行python程序。结果显示不存在ants这个库。

经过检查，发现这不仅仅是ants没装上的问题：实际上，在实验室iMac上的vscode，即使激活了某个anaconda环境，实际使用的python版本也不会更改。（之前一直没发现是因为只用了内置库。。。）

例如：conda activate py39 （python版本为3.9），然后键入“python”，被告知python版本是3.8（？？？）

上国内外网站上各种查询解决方案，无外乎是配置环境变量，但均无效果。

临时解决方案：更改默认python 版本。

我的流程：（参考：https://blog.csdn.net/u012033124/article/details/88894834 ）

1. vim ~/.zshrc (打开环境变量)；

2. 加入：export PATH=${PATH}:~/opt/anaconda3/envs/xxx/bin

3. 加入：alias python="~/opt/anaconda3/envs/xxx/bin/python" (重点，相当于说，conda activate的环境还是没有起作用，使用的还是默认路径。但是我们把默认路径修改为了我们要activate的路径= =。也就是说以后每次换环境都要改一下这句 = =。)

再次在terminal中输入“python”，显示版本正确。运行程序，可以运行。



-------------------------------------------------------------------------

### 突发奇想

那也就是说，我可以直接把每个环境名都alias一下？例如：

alias env1="~/opt/anaconda3/envs/env1/bin/python"

alias env2="~/opt/anaconda3/envs/env2/bin/python"

...

然后我就可以把"python xx.py" 改为直接用 "env1 xx.py"，甚至不用conda activate？

有空试试。。。



### 关于上一节设想如果实现，怎么在已有的环境中安装新package的问题：

实际上lab mac经常出现打开某环境后，pip install package没有装在这个环境的情况。

解决方案：

conda activate env1, 修改"pip install xxx" 为 "python -m pip install xxx" (当然，如果采用了上一节的方案，就应写为env1 -m pip install xxx...)



