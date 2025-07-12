# 📦 Xray VLESS-Vision-REALITY 一键部署脚本

基于 Debian 12，从源码自动编译安装 Xray-core，并部署极简、纯净、安全的 VLESS + Reality 节点。

> 🧭 脚本参考教程原文：[vpsdeck.com](https://vpsdeck.com/posts/xray-source-install-vless-reality/)  
> ✍️ 作者出处：Linux Server 频道（[t.me/LinuxServer_Channel](https://t.me/LinuxServer_Channel)）

---

## ✅ 特性说明

- ✅ 自动识别架构（支持 `amd64` 与 `arm64`）
- ✅ 自动获取最新 Go 版本（官方稳定版）
- ✅ 编译最新版 Xray-core（支持 VLESS + REALITY + Vision）
- ✅ 自动生成配置（UUID、私钥、公钥、ShortID）
- ✅ 自动生成 systemd 服务并启用
- ✅ 输出并保存 VLESS 节点链接

---

## 📥 使用方法

下载脚本：

```bash
curl -O https://raw.githubusercontent.com/foxmail1127/Xray-VLESS-Vision-REALITY/main/install_xray-reality.sh
chmod +x install_xray-reality.sh
```

执行部署（支持自定义备注、端口、SNI）：

```bash
./install_xray-reality.sh [备注] [端口] [SNI]
```

示例：

```bash
./install_xray-reality.sh "MyNode" 443 www.cloudflare.com
```

---

## 📌 脚本输出示例

```bash
✅ Xray Reality 节点已部署完成！
📌 节点链接如下：
vless://uuid@IP:port?encryption=none&flow=xtls-rprx-vision...
```

并保存至：

```bash
~/xray_node_link.txt
```

---

## 📝 依赖说明

脚本会自动安装以下依赖：
- Go（从 go.dev 获取最新版）
- Git / Curl / OpenSSL / Vim / Nano / Sudo
- systemd 服务管理

---

## 📂 文件说明

| 路径                            | 说明                     |
|---------------------------------|--------------------------|
| `/usr/local/bin/xray`          | 编译后的 Xray 主程序     |
| `/etc/xray/config.json`        | 生成的配置文件           |
| `/etc/systemd/system/xray.service` | 后台服务定义脚本         |
| `~/xray_node_link.txt`         | 输出的节点链接信息       |

---

## 📣 鸣谢与参考

- [XTLS/Xray-core](https://github.com/XTLS/Xray-core)
- [原教程：VPSDeck](https://vpsdeck.com/posts/xray-source-install-vless-reality/)
- [Linux Server Telegram频道](https://t.me/LinuxServer_Channel)
