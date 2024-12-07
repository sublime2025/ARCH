#### 

```basic
pacman -S neofetch
pacman -S curl
pacman -S yay
pacman -S rpm
pacman -S git
pacman -S wget
pacman -S firefox
sudo pacman -S base-devel
sudo pacman -S git
sudo git clone https://aur.archlinux.org/yay.git
sudo chown -R username:users ./yay
id username
cd yay
makepkg -si
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
# 安装常用中文字体
sudo pacman -S wqy-zenhei

# 编辑 locale.gen 文件
sudo vim /etc/locale.gen
zh_CN.UTF-8 UTF-8
zh_CN.GBK GBK
zh_CN GB2312

# 生成 locale
sudo locale-gen

# 设置中文
echo LANG=zh_CN.UTF-8 > /etc/locale.conf
# 安装fictx5
sudo pacman -S fcitx5 fcitx5-chinese-addons fcitx5-gtk fcitx5-qt fcitx5-configtool

# 编辑配置文件
 vim /etc/environment
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx

# 字体配置
vim  ~/.config/fontconfig/fonts.conf
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <alias>
    <family>sans-serif</family>
    <prefer>
      <family>Noto Sans CJK SC</family>
      <family>WenQuanYi Micro Hei</family>
    </prefer>
  </alias>
  <alias>
    <family>serif</family>
    <prefer>
      <family>Noto Serif CJK SC</family>
      <family>WenQuanYi Zen Hei</family>
    </prefer>
  </alias>
  <alias>
    <family>monospace</family>
    <prefer>
      <family>Noto Sans Mono CJK SC</family>
      <family>WenQuanYi Micro Hei Mono</family>
    </prefer>
  </alias>
</fontconfig>
pacman -S docker 

# 修改仓库地址
vim /etc/docker/daemon.json

# 重启
systemctl restart docker

# 开机自启
systemctl enable docker

# 测试安装
docker run hello-world
```
