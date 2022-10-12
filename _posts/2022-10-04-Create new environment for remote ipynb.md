# VSCode 连接 SSH 的情况下创建可以运行ipynb的环境

## 具体步骤

1. 在server上安装anaconda（一劳永逸）

2. 在anaconda上创建虚拟环境：conda create -n （environment name） python==x.x.x

3. 安装作业要求的package，用conda和pip都行

4. 安装ipykernel：pip install ipykernel (重要！)

5. ctrl shift p，输入jupyter，选择“Specify local or remote Jupyter server for connections”, 选default （在已经连上服务器的情况下，服务器就是本地）

6. 重启vscode，再次打开后，点击ipynb文件的run all，vscode会提示你选择一个环境，之前建立的环境此时应该已经可以被显示出来。

## 2022.10.11 更新：

在完成5后，如果没有效果，可以尝试在5中选择指定某个server，然后会发现现在一个server都找不到了。接下来，再重复一遍5（选择default）和6的操作，之后大概率就可以看到我们需要的环境了。
