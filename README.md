以下是在 Ubuntu 22.04 上安装 Docker 的步骤：

准备工作：
卸载操作系统默认安装的 Docker（如果有的话）：
sudo apt-get remove docker docker-engine docker.io containerd runc

安装必要的支持：
sudo apt install apt-transport-https ca-certificates curl software-properties-common gnupg lsb-release

添加 Docker 官方 GPG key：
使用以下命令添加 Docker 官方 GPG key（也可以使用阿里源的 GPG KEY）：
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

添加 Docker APT 源：
Docker 官方源：
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

阿里源（推荐使用阿里的 GPG KEY）：
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://mirrors.aliyun.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

更新源并安装 Docker：
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io

启动 Docker：
sudo systemctl enable docker

允许非 Root 用户执行 Docker 命令：
添加 docker 用户组：
sudo groupadd docker

将当前用户添加到 docker 用户组：
sudo usermod -aG docker $USER

使权限生效：
newgrp docker

更新 .bashrc 文件：
编辑 ~/.bashrc 文件，在文件末尾增加以下一行（如果没有此行命令，每次打开新终端都需要执行 newgrp docker 命令）：
groupadd -f docker

现在已经成功安装了 Docker！
可以运行 docker run --rm hello-world 来测试 Docker 是否安装正确。

如果您在使用过程中发现拉取 Docker 镜像速度较慢，可以配置 Docker 国内镜像加速。祝您使用愉快！🐳
