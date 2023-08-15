# bbr-v3-deb

Compile bbr-v3 kernel into deb format.
编译 bbr-v3 内核为 deb 格式

## Installation

从 `https://github.com/Zxilly/bbr-v3-deb/releases/latest` 下载 `linux-headers` 和 `linux-image`.

`dpkg -i` 或 `apt install` 安装。

```bash
# 设置 bbrv3
echo 'net.ipv4.tcp_congestion_control=bbr1' | sudo tee -a /etc/sysctl.conf
sudo sysctl -p

# 查看当前的TCP流控算法
sysctl net.ipv4.tcp_congestion_control

# 查看可用的TCP流控算法，以module形式被编译的算法将不会显示
sysctl net.ipv4.tcp_available_congestion_control
```
