# bbr-v3-pkg
Compile bbr-v3 kernel into deb/rpm format.

编译支持 bbr-v3 的 linux 内核为 deb/rpm 格式。

## Installation

从 `https://github.com/Zxilly/bbr-v3-deb/releases/latest` 下载 linux-headers-*.deb 和 linux-image-*.deb 文件。

对于Debian/Ubuntu系统，使用 dpkg -i 或 apt install 进行安装。

对于基于RPM的系统（如Fedora，CentOS，RHEL），请从同一链接下载 kernel-headers-\*.rpm 和 kernel-\*.rpm 文件。

使用 rpm -i 或 dnf install 进行安装。

```bash
# 设置 bbrv3
echo 'net.ipv4.tcp_congestion_control=bbr' | sudo tee -a /etc/sysctl.conf
sudo sysctl -p

# 查看当前的TCP流控算法
sysctl net.ipv4.tcp_congestion_control

# 查看可用的TCP流控算法，以module形式被编译的算法将不会显示
sysctl net.ipv4.tcp_available_congestion_control
```
