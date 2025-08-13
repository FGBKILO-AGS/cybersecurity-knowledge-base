# Linux基础教程

## 1. Linux简介

### 1.1 什么是Linux

Linux是一个开源的类Unix操作系统，由芬兰学生Linus Torvalds在1991年首次发布。Linux是基于UNIX设计思想的自由和开放源代码的类UNIX操作系统，它的内核由Linus Torvalds开发，而其他部分则由全球各地的程序员共同开发和维护。

### 1.2 Linux的特点

- **开源免费**：任何人都可以自由获取、使用、修改和分发Linux
- **多用户多任务**：支持多个用户同时登录系统并执行多个任务
- **良好的稳定性**：系统可以长时间运行而不需要重启
- **强大的网络功能**：天生为网络而设计
- **丰富的软件资源**：拥有大量免费的应用软件
- **优良的可移植性**：可运行在多种硬件平台上
- **安全性高**：相比其他操作系统，Linux的安全性更高

### 1.3 常见Linux发行版

- **Ubuntu**：最流行的桌面Linux发行版之一，适合Linux新手
- **CentOS/RHEL**：企业级服务器的首选，稳定可靠
- **Debian**：以其稳定性和安全性著称
- **Fedora**：Red Hat的社区版本，包含最新的技术和软件
- **Arch Linux**：追求简洁和最新软件的发行版
- **Kali Linux**：专注于安全和渗透测试

## 2. Linux安装

### 2.1 安装前准备

- 确定安装方式：物理机安装、虚拟机安装或双系统
- 备份重要数据
- 下载所需Linux发行版ISO镜像
- 准备安装介质（U盘或光盘）

### 2.2 虚拟机安装（以VMware为例）

1. 安装VMware Workstation/Player
2. 创建新的虚拟机
3. 选择"稍后安装操作系统"
4. 选择Linux，并指定版本
5. 设置虚拟机名称和存储位置
6. 设置磁盘大小（建议至少20GB）
7. 自定义硬件配置（内存建议2GB以上）
8. 设置CD/DVD使用ISO镜像文件
9. 启动虚拟机，开始安装

### 2.3 物理机安装步骤

1. 制作启动U盘（使用Rufus、Etcher等工具）
2. 设置BIOS从U盘启动
3. 按照安装向导进行操作
4. 设置分区（建议/分区15-20GB，/home分区根据需要，swap分区为内存的1-2倍）
5. 设置用户名和密码
6. 等待安装完成并重启

## 3. Linux基本操作

### 3.1 登录和注销

```bash
# 登录系统
username: your_username
password: your_password

# 注销当前用户
logout
# 或
exit
```

### 3.2 关机和重启

```bash
# 立即关机
shutdown -h now
# 或
poweroff

# 立即重启
shutdown -r now
# 或
reboot

# 计划关机（10分钟后）
shutdown -h +10
```

### 3.3 基本命令行操作

```bash
# 显示当前目录
pwd

# 列出文件和目录
ls
ls -l  # 详细信息
ls -a  # 显示隐藏文件
ls -lh # 以人类可读方式显示文件大小

# 切换目录
cd /path/to/directory  # 绝对路径
cd directory_name      # 相对路径
cd ..                  # 上一级目录
cd ~                   # 用户主目录
cd -                   # 上一个工作目录

# 创建目录
mkdir directory_name
mkdir -p parent/child/grandchild  # 创建多级目录

# 删除目录
rmdir directory_name              # 只能删除空目录
rm -r directory_name              # 递归删除目录及其内容

# 创建文件
touch filename

# 复制文件或目录
cp source destination
cp -r source_dir destination_dir  # 递归复制目录

# 移动/重命名文件或目录
mv source destination

# 删除文件
rm filename
rm -f filename                    # 强制删除，不提示
```

### 3.4 文件查看和编辑

```bash
# 查看文件内容
cat filename       # 显示整个文件
more filename      # 分页显示，空格翻页，q退出
less filename      # 更强大的分页器，可上下滚动
head filename      # 显示文件开头10行
head -n 20 filename # 显示文件开头20行
tail filename      # 显示文件末尾10行
tail -n 20 filename # 显示文件末尾20行
tail -f filename   # 实时查看文件更新

# 文本编辑器
nano filename      # 简单易用的编辑器
vim filename       # 高级文本编辑器
```

### 3.5 文件权限管理

```bash
# 查看文件权限
ls -l

# 权限表示：rwxrwxrwx（所有者、组、其他人的读、写、执行权限）

# 修改文件权限（数字方式）
chmod 755 filename  # rwxr-xr-x
chmod 644 filename  # rw-r--r--
chmod 777 filename  # rwxrwxrwx（不推荐）

# 修改文件权限（符号方式）
chmod u+x filename  # 给所有者添加执行权限
chmod g-w filename  # 移除组的写权限
chmod o=r filename  # 设置其他人只有读权限
chmod a+x filename  # 给所有人添加执行权限

# 修改文件所有者
chown user filename
chown user:group filename  # 同时修改所有者和组

# 修改文件所属组
chgrp group filename
```

## 4. 文件系统

### 4.1 Linux文件系统层次结构

- **/bin**：基本命令二进制文件
- **/boot**：启动文件，包括内核和引导加载程序
- **/dev**：设备文件
- **/etc**：系统配置文件
- **/home**：用户主目录
- **/lib**：系统库文件
- **/media**：可移动媒体挂载点
- **/mnt**：临时挂载点
- **/opt**：可选应用软件包
- **/proc**：进程和内核信息的虚拟文件系统
- **/root**：root用户的主目录
- **/run**：运行时变量数据
- **/sbin**：系统二进制文件
- **/srv**：服务数据
- **/sys**：系统相关信息
- **/tmp**：临时文件
- **/usr**：用户程序和数据
- **/var**：可变数据文件

### 4.2 文件系统操作

```bash
# 查看磁盘空间使用情况
df -h

# 查看目录大小
du -sh directory_name

# 查看文件系统类型
file -s /dev/sda1

# 挂载文件系统
mount /dev/sdb1 /mnt/usb

# 卸载文件系统
umount /mnt/usb

# 查看已挂载的文件系统
mount

# 创建文件系统
mkfs.ext4 /dev/sdb1  # 创建ext4文件系统
```

## 5. 用户和组管理

### 5.1 用户管理

```bash
# 添加用户
useradd username
useradd -m -s /bin/bash username  # 创建主目录并设置shell

# 设置用户密码
passwd username

# 修改用户信息
usermod -c "Full Name" username  # 修改注释信息
usermod -s /bin/zsh username     # 修改默认shell
usermod -g groupname username    # 修改主组
usermod -G group1,group2 username # 修改附加组

# 删除用户
userdel username
userdel -r username              # 同时删除用户主目录

# 查看用户信息
id username
whoami                           # 显示当前用户
who                              # 显示当前登录的用户
w                                # 显示当前登录的用户及其活动
```

### 5.2 组管理

```bash
# 创建组
groupadd groupname

# 修改组
groupmod -n new_name old_name    # 重命名组

# 删除组
groupdel groupname

# 将用户添加到组
usermod -aG groupname username
# 或
gpasswd -a username groupname

# 从组中删除用户
gpasswd -d username groupname

# 查看组信息
groups                           # 显示当前用户所属的组
groups username                  # 显示指定用户所属的组
cat /etc/group                   # 查看所有组
```

### 5.3 用户和组配置文件

- **/etc/passwd**：用户账户信息
- **/etc/shadow**：用户密码信息（加密）
- **/etc/group**：组信息
- **/etc/gshadow**：组密码信息
- **/etc/sudoers**：sudo配置文件

## 6. 进程管理

### 6.1 查看进程

```bash
# 查看当前运行的进程
ps
ps aux                           # 显示所有进程详细信息
ps -ef                           # 显示所有进程（全格式）

# 实时监控进程
top
htop                             # 更友好的top替代品（可能需要安装）

# 查看特定进程
pgrep process_name               # 查找进程ID
ps aux | grep process_name       # 过滤特定进程
```

### 6.2 进程控制

```bash
# 终止进程
kill PID                         # 发送TERM信号
kill -9 PID                      # 发送KILL信号（强制终止）
killall process_name             # 终止所有指定名称的进程

# 前台/后台进程控制
command &                        # 在后台运行命令
Ctrl+Z                           # 暂停当前前台进程
bg                               # 将暂停的进程放到后台运行
fg                               # 将后台进程调到前台
jobs                             # 列出后台作业

# 进程优先级
nice -n 10 command              # 以较低优先级启动进程
renice +10 PID                   # 调整运行中进程的优先级
```

### 6.3 系统监控

```bash
# 系统负载
uptime

# 内存使用情况
free -h

# CPU信息
cat /proc/cpuinfo
lscpu

# 系统信息
uname -a
hostnamectl

# 查看系统启动时间
who -b
uptime
```

## 7. 网络配置和管理

### 7.1 网络配置

```bash
# 查看网络接口
ifconfig                         # 传统命令，可能需要安装net-tools
ip addr                          # 现代命令

# 配置IP地址（临时）
ifconfig eth0 192.168.1.100 netmask 255.255.255.0
# 或
ip addr add 192.168.1.100/24 dev eth0

# 启用/禁用网络接口
ifconfig eth0 up
ifconfig eth0 down
# 或
ip link set eth0 up
ip link set eth0 down

# 配置默认网关（临时）
route add default gw 192.168.1.1
# 或
ip route add default via 192.168.1.1
```

### 7.2 网络工具

```bash
# 测试连通性
ping hostname_or_ip

# 跟踪路由
traceroute hostname_or_ip
tracepath hostname_or_ip

# DNS查询
nslookup domain_name
dig domain_name

# 端口扫描
nmap hostname_or_ip

# 查看开放端口
netstat -tuln
ss -tuln

# 下载文件
wget url
curl -O url

# SSH连接
ssh username@hostname_or_ip
ssh -p port_number username@hostname_or_ip
```

### 7.3 网络配置文件

- **/etc/hostname**：主机名
- **/etc/hosts**：主机名到IP地址的映射
- **/etc/resolv.conf**：DNS配置
- **/etc/network/interfaces**（Debian/Ubuntu）或 **/etc/sysconfig/network-scripts/**（RHEL/CentOS）：网络接口配置

## 8. 软件包管理

### 8.1 Debian/Ubuntu（APT）

```bash
# 更新软件包列表
apt update

# 升级已安装的软件包
apt upgrade
apt full-upgrade                 # 也会移除不需要的包

# 安装软件包
apt install package_name

# 删除软件包
apt remove package_name
apt purge package_name           # 同时删除配置文件

# 搜索软件包
apt search keyword

# 查看软件包信息
apt show package_name

# 清理不需要的包
apt autoremove
apt clean                        # 清理本地缓存
```

### 8.2 RHEL/CentOS/Fedora（YUM/DNF）

```bash
# 更新软件包列表和升级
yum update
# 或（Fedora和新版CentOS）
dnf update

# 安装软件包
yum install package_name
dnf install package_name

# 删除软件包
yum remove package_name
dnf remove package_name

# 搜索软件包
yum search keyword
dnf search keyword

# 查看软件包信息
yum info package_name
dnf info package_name

# 列出已安装的软件包
yum list installed
dnf list installed
```

### 8.3 Arch Linux（Pacman）

```bash
# 更新软件包列表和升级
pacman -Syu

# 安装软件包
pacman -S package_name

# 删除软件包
pacman -R package_name
pacman -Rs package_name          # 同时删除依赖

# 搜索软件包
pacman -Ss keyword

# 查看软件包信息
pacman -Si package_name

# 列出已安装的软件包
pacman -Q
```

### 8.4 从源代码安装

```bash
# 基本步骤
# 1. 下载源代码（通常是tar.gz或tar.bz2文件）
wget http://example.com/software-1.0.tar.gz

# 2. 解压缩
tar -xzvf software-1.0.tar.gz    # 对于.tar.gz
tar -xjvf software-1.0.tar.bz2   # 对于.tar.bz2

# 3. 进入源代码目录
cd software-1.0

# 4. 配置
./configure --prefix=/usr/local

# 5. 编译
make

# 6. 安装
sudo make install
```

## 9. Shell脚本编程

### 9.1 基础语法

```bash
#!/bin/bash
# 这是一个注释

# 变量定义和使用
NAME="Linux"
echo "Hello, $NAME!"

# 命令替换
DATE=$(date)
echo "Current date and time: $DATE"

# 条件语句
if [ "$NAME" = "Linux" ]; then
    echo "Name is Linux"
elif [ "$NAME" = "Unix" ]; then
    echo "Name is Unix"
else
    echo "Name is neither Linux nor Unix"
fi

# 循环
# For循环
for i in 1 2 3 4 5; do
    echo "Number: $i"
done

# While循环
count=1
while [ $count -le 5 ]; do
    echo "Count: $count"
    count=$((count + 1))
done

# Until循环
count=1
until [ $count -gt 5 ]; do
    echo "Count: $count"
    count=$((count + 1))
done

# 函数
greet() {
    echo "Hello, $1!"
}

greet "World"
```

### 9.2 常用脚本示例

#### 备份脚本

```bash
#!/bin/bash

# 简单的备份脚本
BACKUP_DIR="/backup"
SOURCE_DIR="/home/user/documents"
DATESTAMP=$(date +%Y%m%d)
ARCHIVE_NAME="backup_${DATESTAMP}.tar.gz"

# 创建备份目录（如果不存在）
mkdir -p "$BACKUP_DIR"

# 创建归档
tar -czf "${BACKUP_DIR}/${ARCHIVE_NAME}" "$SOURCE_DIR"

# 检查是否成功
if [ $? -eq 0 ]; then
    echo "Backup completed successfully: ${BACKUP_DIR}/${ARCHIVE_NAME}"
else
    echo "Backup failed!"
fi
```

#### 系统监控脚本

```bash
#!/bin/bash

# 简单的系统监控脚本
echo "=== System Information ==="
echo "Hostname: $(hostname)"
echo "Kernel: $(uname -r)"
echo "Uptime: $(uptime -p)"
echo

echo "=== CPU Usage ==="
top -bn1 | grep "Cpu(s)" | awk '{print $2 + $4}' | awk '{print "CPU Usage: " $1 "%"}'
echo

echo "=== Memory Usage ==="
free -h | grep Mem | awk '{print "Total: " $2 "\tUsed: " $3 "\tFree: " $4}'
echo

echo "=== Disk Usage ==="
df -h | grep -v "tmpfs" | grep -v "udev"
echo

echo "=== Network Interfaces ==="
ip -brief addr show
echo
```

## 10. 系统服务和守护进程

### 10.1 Systemd服务管理

```bash
# 查看服务状态
systemctl status service_name

# 启动服务
systemctl start service_name

# 停止服务
systemctl stop service_name

# 重启服务
systemctl restart service_name

# 重新加载配置
systemctl reload service_name

# 启用服务（开机自启）
systemctl enable service_name

# 禁用服务（禁止开机自启）
systemctl disable service_name

# 查看所有服务
systemctl list-units --type=service

# 查看启动失败的服务
systemctl --failed
```

### 10.2 日志管理

```bash
# 查看系统日志
journalctl

# 查看特定服务的日志
journalctl -u service_name

# 查看最近的日志
journalctl -n 50

# 实时查看日志
journalctl -f

# 查看特定时间段的日志
journalctl --since "2023-01-01" --until "2023-01-02 03:00"

# 传统日志文件
cat /var/log/syslog              # Debian/Ubuntu
cat /var/log/messages            # RHEL/CentOS
```

### 10.3 创建自定义服务

```bash
# 创建服务文件
sudo nano /etc/systemd/system/myservice.service

# 服务文件内容示例
[Unit]
Description=My Custom Service
After=network.target

[Service]
Type=simple
User=username
ExecStart=/path/to/your/program
Restart=on-failure

[Install]
WantedBy=multi-user.target

# 重新加载systemd配置
systemctl daemon-reload

# 启用并启动服务
systemctl enable myservice
systemctl start myservice
```

## 11. 安全加固

### 11.1 基本安全措施

```bash
# 更新系统
apt update && apt upgrade         # Debian/Ubuntu
yum update                        # RHEL/CentOS

# 检查开放端口
ss -tuln

# 配置防火墙（UFW - Ubuntu）
ufw enable
ufw allow ssh
ufw allow 80/tcp
ufw status

# 配置防火墙（firewalld - RHEL/CentOS）
systemctl start firewalld
systemctl enable firewalld
firewall-cmd --permanent --add-service=ssh
firewall-cmd --permanent --add-service=http
firewall-cmd --reload
firewall-cmd --list-all
```

### 11.2 SSH安全配置

```bash
# 编辑SSH配置文件
sudo nano /etc/ssh/sshd_config

# 推荐的安全设置
# 禁用root登录
PermitRootLogin no

# 使用密钥认证，禁用密码认证
PasswordAuthentication no

# 限制SSH访问用户
AllowUsers user1 user2

# 更改默认端口（可选）
Port 2222

# 重启SSH服务
systemctl restart sshd
```

### 11.3 账户安全

```bash
# 设置强密码策略
sudo nano /etc/pam.d/common-password
# 添加：password requisite pam_pwquality.so retry=3 minlen=12 difok=3 ucredit=-1 lcredit=-1 dcredit=-1 ocredit=-1

# 设置密码过期策略
sudo chage -M 90 username         # 设置密码90天过期
sudo chage -l username            # 查看密码策略

# 锁定账户
sudo passwd -l username

# 解锁账户
sudo passwd -u username
```

## 12. 高级主题

### 12.1 LVM（逻辑卷管理）

```bash
# 查看物理卷、卷组和逻辑卷
pvs                              # 物理卷
vgs                              # 卷组
lvs                              # 逻辑卷

# 创建物理卷
pvcreate /dev/sdb

# 创建卷组
vgcreate vg_name /dev/sdb

# 创建逻辑卷
lvcreate -L 10G -n lv_name vg_name

# 扩展逻辑卷
lvextend -L +5G /dev/vg_name/lv_name
resize2fs /dev/vg_name/lv_name    # 调整文件系统大小
```

### 12.2 容器和虚拟化

```bash
# Docker基本命令
docker ps                         # 列出运行中的容器
docker images                     # 列出镜像
docker pull image_name            # 拉取镜像
docker run -d -p 80:80 image_name # 运行容器
docker stop container_id          # 停止容器
docker rm container_id            # 删除容器

# 虚拟机管理（KVM/QEMU）
virsh list                        # 列出运行中的虚拟机
virsh start vm_name              # 启动虚拟机
virsh shutdown vm_name           # 关闭虚拟机
virsh destroy vm_name            # 强制关闭虚拟机
```

### 12.3 性能调优

```bash
# 查看系统性能
top
htop
iostat
vmstat

# 调整进程优先级
nice -n 10 command               # 以较低优先级启动进程
renice +10 PID                    # 调整运行中进程的优先级

# 限制进程资源使用
ulimit -n 4096                    # 设置最大打开文件数

# 系统参数调整
sudo sysctl -w vm.swappiness=10   # 减少交换使用
sudo sysctl -p                    # 应用更改
```

## 13. 故障排除

### 13.1 常见问题诊断

```bash
# 磁盘空间问题
df -h                             # 查看磁盘使用情况
du -sh /*                         # 查看根目录下各目录大小
find / -type f -size +100M        # 查找大文件

# 内存问题
free -h                           # 查看内存使用情况
top                               # 查看内存消耗最多的进程

# CPU问题
top                               # 查看CPU使用情况
mpstat                            # 查看CPU统计信息

# 网络问题
ping gateway_ip                   # 测试网络连通性
traceroute hostname               # 跟踪路由
ss -tuln                          # 查看开放端口
```

### 13.2 系统恢复

```bash
# 进入救援模式（通过启动介质）
# 挂载根分区
mount /dev/sda1 /mnt

# 挂载其他必要的文件系统
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys

# chroot到挂载的系统
chroot /mnt

# 修复引导加载程序（GRUB）
grub-install /dev/sda
update-grub
```

### 13.3 系统备份和恢复

```bash
# 使用rsync备份
rsync -avz --delete /source/directory/ /backup/directory/

# 使用tar创建完整备份
tar -czvf backup.tar.gz /home/user

# 使用dd创建磁盘镜像
dd if=/dev/sda of=/path/to/disk.img bs=4M status=progress

# 从tar恢复
tar -xzvf backup.tar.gz -C /restore/directory/

# 从dd镜像恢复
dd if=/path/to/disk.img of=/dev/sda bs=4M status=progress
```

## 14. 实用技巧

### 14.1 命令行技巧

```bash
# 命令历史
history                           # 显示命令历史
!n                               # 执行历史中的第n条命令
!!                               # 执行上一条命令
!string                          # 执行最近的以string开头的命令

# 命令别名
alias ll='ls -la'                 # 创建临时别名
# 永久别名（添加到~/.bashrc）
echo 'alias ll="ls -la"' >> ~/.bashrc
source ~/.bashrc                  # 重新加载配置

# 命令替换
echo "Today is $(date +%A)"

# 管道和重定向
ls -la | grep "file"              # 管道
ls -la > output.txt               # 输出重定向（覆盖）
ls -la >> output.txt              # 输出重定向（追加）
command 2> error.log              # 错误重定向
command > output.txt 2>&1         # 标准输出和错误重定向到同一文件
```

### 14.2 文本处理工具

```bash
# grep - 文本搜索
grep "pattern" file
grep -i "pattern" file            # 忽略大小写
grep -r "pattern" directory       # 递归搜索
grep -v "pattern" file            # 反向匹配（不包含pattern的行）

# sed - 流编辑器
sed 's/old/new/' file             # 替换第一次出现
sed 's/old/new/g' file            # 全局替换
sed -i 's/old/new/g' file         # 直接修改文件
sed '1,5d' file                   # 删除1-5行

# awk - 文本处理语言
awk '{print $1}' file             # 打印第一列
awk -F: '{print $1}' /etc/passwd  # 使用:作为分隔符
awk '{sum+=$1} END {print sum}' file # 计算第一列的总和
```

### 14.3 压缩和解压缩

```bash
# tar
tar -czvf archive.tar.gz directory # 创建gzip压缩的tar归档
tar -cjvf archive.tar.bz2 directory # 创建bzip2压缩的tar归档
tar -xzvf archive.tar.gz          # 解压gzip压缩的tar归档
tar -xjvf archive.tar.bz2         # 解压bzip2压缩的tar归档

# zip/unzip
zip -r archive.zip directory      # 创建zip归档
unzip archive.zip                 # 解压zip归档

# 其他格式
gzip file                         # 压缩文件（创建.gz文件）
gunzip file.gz                    # 解压.gz文件
bzip2 file                        # 压缩文件（创建.bz2文件）
bunzip2 file.bz2                  # 解压.bz2文件
```

## 15. 参考资源

### 15.1 官方文档

- [Linux Documentation Project](https://tldp.org/)
- [Ubuntu Documentation](https://help.ubuntu.com/)
- [CentOS Documentation](https://docs.centos.org/)
- [Arch Linux Wiki](https://wiki.archlinux.org/)

### 15.2 命令手册

```bash
# 查看命令手册
man command_name
info command_name
command_name --help
```

### 15.3 在线学习资源

- [Linux Journey](https://linuxjourney.com/)
- [Linux Command Library](https://linuxcommandlibrary.com/)
- [ExplainShell](https://explainshell.com/)
- [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/) - 通过游戏学习Linux命令

## 结语

本教程涵盖了Linux的基础知识和常用操作，但Linux的世界非常广阔，还有许多高级主题和专业领域值得探索。持续学习和实践是掌握Linux的关键。希望这份教程能够帮助你开始Linux之旅，并为进一步学习打下坚实基础。