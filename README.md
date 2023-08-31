# bbr-v3-pkg

[![Build Package](https://github.com/Zxilly/bbr-v3-pkg/actions/workflows/build.yml/badge.svg)](https://github.com/Zxilly/bbr-v3-pkg/actions/workflows/build.yml)

For English, please see [README.EN.md](README.EN.md).

编译支持 bbr-v3 的 linux 内核为 deb/rpm 格式。

## 安装

从 `https://github.com/Zxilly/bbr-v3-deb/releases/latest` 下载。

对于 Debian/Ubuntu 系统，下载 `linux-headers-*.deb` 和 `linux-image-*.deb` 文件，使用 `dpkg -i` 或 `apt install` 进行安装。

对于基于 RPM 的系统（如 Fedora，CentOS，RHEL），请下载 `kernel-headers-*.rpm` 和 `kernel-*.rpm` 文件。

如果需要构建内核模块，还需要下载 `kernel-devel-*.rpm` 文件。

使用 rpm -i 或 dnf install 进行安装。


## 配置

### 启用 bbrv3

```bash
# 设置 bbrv3
echo 'net.ipv4.tcp_congestion_control=bbr' | sudo tee -a /etc/sysctl.conf
sudo sysctl -p

# 查看当前的TCP流控算法
sysctl net.ipv4.tcp_congestion_control

# 查看可用的TCP流控算法，以module形式被编译的算法将不会显示
sysctl net.ipv4.tcp_available_congestion_control
```

如果想启用 bbrv3，流控算法应设置为 `bbr`，如果想使用早期版本的 bbr，流控算法应设置为 `bbr1`。