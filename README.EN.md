# bbr-v3-pkg

[![Build Package](https://github.com/Zxilly/bbr-v3-pkg/actions/workflows/build.yml/badge.svg)](https://github.com/Zxilly/bbr-v3-pkg/actions/workflows/build.yml)

Compile Linux kernel with BBRv3 support into deb/rpm package formats.

## Installation

Download from `https://github.com/Zxilly/bbr-v3-deb/releases/latest`.

For Debian/Ubuntu systems, download the `linux-headers-*.deb` and `linux-image-*.deb` files and install using `dpkg -i` or `apt install`.

For RPM-based systems (like Fedora, CentOS, RHEL), download the `kernel-headers-*.rpm` and `kernel-*.rpm` files.

If kernel modules need to be built, also download the `kernel-devel-*.rpm` file.

Install using rpm -i or dnf install.

## Configuration

### Enabling BBRv3

```bash
# Set up BBRv3
echo 'net.ipv4.tcp_congestion_control=bbr' | sudo tee -a /etc/sysctl.conf
sudo sysctl -p

# Check the current TCP congestion control algorithm
sysctl net.ipv4.tcp_congestion_control

# Check available TCP congestion control algorithms; algorithms compiled as modules will not be displayed
sysctl net.ipv4.tcp_available_congestion_control
```

To enable BBRv3, set the congestion control algorithm to `bbr`. If you want to use an earlier version of BBR, set the congestion control algorithm to `bbr1`.