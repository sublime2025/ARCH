#### 安装常用包

```sh
pacman -S neofetch
pacman -S curl
pacman -S yay
pacman -S rpm
pacman -S git
pacman -S firefox
```



#### 安装Yay

```sh
sudo pacman -S base-devel
sudo pacman -S git
sudo git clone https://aur.archlinux.org/yay.git
sudo chown -R username:users ./yay
id username
cd yay
makepkg -si
```



#### 开启SSH远程

```sh
sudo pacman -S openssh

# 启动服务
sudo systemctl start sshd

# 设置开机自启
sudo systemctl enable sshd

# 查看服务状态
sudo systemctl status sshd

# 编辑配置文件
vim /etc/ssh/sshd_config  
#PasswordAuthentication yes

# 设置防火墙
sudo ufw allow ssh
sudo ufw allow 22/tcp
sudo systemctl restart sshd

# 网络管理工具
sudo pacman -S networkmanager
sudo systemctl start NetworkManager
sudo systemctl enable NetworkManager

```



#### 安装中文字体包

```sh
# 安装常用中文字体
sudo pacman -S adobe-source-han-sans-cn-fonts

# 编辑 locale.gen 文件
sudo vim /etc/locale.gen
zh_CN.UTF-8 UTF-8
zh_CN.GBK GBK
zh_CN GB2312

# 生成 locale
sudo locale-gen

# 设置中文
echo LANG=zh_CN.UTF-8 > /etc/locale.conf

# 安装中文
sudo pacman -S cinnamon-translations
```



#### 安装中文输入法

```sh
# 安装fictx5
sudo pacman -S fcitx5 fcitx5-chinese-addons fcitx5-gtk fcitx5-qt fcitx5-configtool

# 编辑配置文件
vim /etc/environment
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx

# 检查输入法状态
fcitx5-diagnose
```



#### 安装docker

```sh
# 安装服务
pacman -S docker 

# 开机自启
systemctl enable docker

# 设置用户
groupadd docker
usermod -aG docker UserName

# 仓库地址
vim /etc/docker/daemon.json

{
"registry-mirrors" :
["https://docker.m.daocloud.io",
"https://docker.cmliussss.net",
"https://docker.1ms.run",
"https://huecker.io",
"https://dockerhub.timeweb.cloud",
"https://docker.rainbond.cc"]
}

# 加载配置
systemctl daemon-reload

# 重新启动
systemctl restart docker

# 安装镜像
docker pull dpanel/dpanel

# 创建容器
docker run -d --name dpanel --restart=always \
 -p 80:80 -p 443:443 -p 8807:8080 -e APP_NAME=dpanel \
 -v /var/run/docker.sock:/var/run/docker.sock -v dpanel:/dpanel \
 dpanel/dpanel:latest 

# 访问地址
localhost:8807

```
