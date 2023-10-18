> Xray-TLS+Web搭建/管理脚本

- 支持 (VLESS/VMess)-(TCP/gRPC/WebSocket)-(XTLS/TLS) + Web 的搭建/管理，支持多种协议并存

- 集成 多版本bbr/锐速 安装选项

- 支持多种系统 (Ubuntu CentOS Debian deepin fedora ...) 

- 支持多种指令集 (x86 x86_64 arm64 ...)

- 支持ipv6only服务器 (需自行设置dns64)

- 集成删除阿里云盾和腾讯云盾功能 (仅对阿里云和腾讯云服务器有效)

- 使用Nginx作为网站服务

- 使用Xray作为前置分流器

- 使用acme.sh自动申请/更新域名证书

- 支持选择搭建个人网盘作为伪装网页
---

如果有快速安装的需求，推荐在 **[Xray-core#Installation](https://github.com/XTLS/Xray-core#Installation)** 中选择其他脚本

安装流程：

`[升级系统组件]->[安装bbr]->[安装php]->安装Nginx->安装Xray->申请证书->配置文件->[配置伪装网站]`

> 安装向导

```bash
# Debian基系统(包括Ubuntu、Debian、deepin)：
apt --no-install-recommends -qy install wget ca-certificates || (apt update && apt --no-install-recommends -qy install wget ca-certificates)
# Red Hat基系统(包括CentOS、fedora)：
dnf -y install wget ca-certificates || yum -qy install wget ca-certificates
# 获取最新脚本
wget https://raw.githubusercontent.com/jaydiao521/xray/main/Xray-script/xray-TLS+Web-setup.sh
# 开始安装
chmod +x xray-TLS+Web-setup.sh && ./xray-TLS+Web-setup.sh
```
> 伪装网站对比

||优点|缺点|
|-|-|-|
|Nextcloud|功能更多更强大，用的人更多|需要安装php，安装php需要额外很多时间(见 **[安装时长参考](#安装时长参考)**)，同时也比Cloudreve占用更多系统资源，因此不建议小机使用。|
|Cloudreve|轻量化、安装快(不需要php)、占用系统资源少|功能较少，使用的人较少|
> 关于gRPC与WebSocket

当正在使用的CDN同时支持gRPC与WebSocket时，两者之间改如何选择呢？他们的主要区别体现在以下三个方面：ALPN、延迟和性能。

关于ALPN，见[此处](#关于tls握手tls指纹和alpn)。

关于延迟，gRPC自带mux，因此延迟更低。注意这里指的是打开网站的延迟，mux并不能降低游戏延迟。

关于性能，WebSocket的性能更强，如果你的设备性能较弱的话，如家用普通路由器，用WebSocket速度会快一些。
> 安装位置

Nginx：`/usr/local/nginx`

php：`/usr/local/php`

Cloudreve：`/usr/local/cloudreve`

Xray： **[Xray-install](https://github.com/XTLS/Xray-install)**

- 域名证书申请：https://github.com/acmesh-official/acme.sh
- 脚本来自：https://github.com/teddysun/across/blob/master/bbr.sh

- bbr2脚本来自：https://github.com/yeyingorg/bbr2.sh (Ubuntu Debian)  https://github.com/jackjieYYY/bbr2 (CentOS)
- bbrplus脚本来自：https://github.com/chiakge/Linux-NetSpeed

> ⚠️⚠️⚠️

**此脚本仅供交流学习使用，请勿使用此脚本行非法之用途。**
