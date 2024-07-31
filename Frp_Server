# Docker_Frp_Server
# 创建存放目录
sudo mkdir /etc/frp
# 创建frps.ini文件
vim /etc/frp/frps.ini


# frps.ini文件内容
[common]
# 监听端口
bind_port = 7000
# 面板端口
dashboard_port = 7500
# 登录面板账号设置
dashboard_user = admin
dashboard_pwd = hw1234
# 设置http及https协议下代理端口（非重要）
vhost_http_port = 7080
vhost_https_port = 7081
# 身份验证
token = 12345678
# frps.ini end

# 部署
docker pull snowdreamtech/frpc
docker run --restart=always --network host -d -v /etc/frp/frps.ini:/etc/frp/frps.ini --name frps snowdreamtech/frps

# frpc.ini文件内容
[common]
# server_addr为FRPS服务器IP地址
server_addr = 192.168.0.1
# server_port为服务端监听端口，bind_port
server_port = 7000
# 身份验证
token = 12345678
[web]
type = tcp
local_ip = 127.0.0.1
local_port = 5000
remote_port = 2250
# [ssh] 为服务名称，下方此处设置为，访问frp服务段的2288端口时，等同于通过中转服务器访问127.0.0.1的22端口。
# type 为连接的类型，此处为tcp
# local_ip 为中转客户端实际访问的IP 
# local_port 为目标端口
# remote_port 为远程端口
# frpc.ini end
