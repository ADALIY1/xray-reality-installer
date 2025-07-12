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

> ❗ 注意：某些精简系统（如最小化 Debian/Ubuntu）默认未安装 curl，如运行 `curl -O` 提示 `command not found`，请先运行以下命令安装 curl：
>
> ```bash
> sudo apt update && sudo apt install -y curl
> ```

下载脚本：

```bash
curl -O https://raw.githubusercontent.com/ADALIY1/xray-reality-installer/refs/heads/main/install_xray-reality.sh
chmod +x install_xray-reality.sh
```

执行部署（支持自定义备注、端口、SNI）：

```bash
./install_xray-reality.sh [备注] [端口] [SNI]
```

| 参数位置 | 名称     | 是否可选 | 用途说明 |
|----------|----------|----------|-----------|
| `$1`     | **备注**   | ✅ 可选   | 最终节点链接中 `#` 后的部分，建议使用英文或加引号包裹中文，例如 `"MyNode"`、`"DC9 🇺🇸"` |
| `$2`     | **端口**   | ✅ 可选   | Xray 监听的端口（默认：51888），支持任意五位数，避免常规端口被封 |
| `$3`     | **伪装域名 (SNI)** | ✅ 可选   | Reality 使用的伪装目标，需为可正常 TLS 访问的域名（默认：`www.microsoft.com`） |

---

### 📌 示例用法解析

#### ✅ 示例 1：使用全部默认值

```bash
./install_xray-reality.sh
```

- 节点备注：Reality_Auto  
- 监听端口：51888  
- 伪装域名：`www.microsoft.com`  

---

#### ✅ 示例 2：仅自定义备注

```bash
./install_xray-reality.sh "搬瓦工 🇺🇸 DC9"
```

- 节点备注：搬瓦工 🇺🇸 DC9  
- 端口：51888（默认）  
- SNI：`www.microsoft.com`（默认）

---

#### ✅ 示例 3：自定义备注 + 端口

```bash
./install_xray-reality.sh "洛杉矶备用" 443
```

- 节点备注：洛杉矶备用  
- 端口：443  
- SNI：`www.microsoft.com`（默认）

---

#### ✅ 示例 4：完全自定义

```bash
./install_xray-reality.sh "MyNode-US" 14433 www.cloudflare.com
```

- 节点备注：MyNode-US  
- 端口：14433  
- SNI：`www.cloudflare.com`

---

执行完后，终端会输出完整节点链接，并保存至本地：

```bash
~/xray_node_link.txt
```


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
