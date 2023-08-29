# Install-Docker-Engine-on-Ubuntu

# 安装前的准备先更新

  sudo apt-get update
  sudo apt-get upgrade
  
  //出现该选项Y就行，没有则跳过
  
# 解决冲突
  //运行以下命令以卸载所有冲突的软件包
  
  for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
  
  //更新软件包索引并安装软件包以允许使用 基于 HTTPS 的存储库
  
  sudo apt-get update
  sudo apt-get install ca-certificates curl gnupg
  
  //添加 Docker 的官方 GPG 密钥：
  
  sudo install -m 0755 -d /etc/apt/keyrings
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
  
  sudo chmod a+r /etc/apt/keyrings/docker.gpg
  
  //使用以下命令设置存储库：
  
  $echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  //更新包索引
  
  sudo apt-get update


# 安装docker命令

  sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  
  验证：通过运行映像验证 Docker 引擎安装是否成功。hello-world
  
  sudo docker run hello-world

