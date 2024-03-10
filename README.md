# Steam520

[![GitHub license](https://img.shields.io/badge/license-GPLv3-blue?style=flat-square)](https://www.gnu.org/licenses/gpl-3.0)
[![TypeScript Version](https://img.shields.io/github/package-json/dependency-version/pboymt/Steam520/dev/typescript?style=flat-square)](https://typescriptlang.org)
[![Git Commit](https://img.shields.io/github/last-commit/pboymt/Steam520?style=flat-square)](https://github.com/pboymt/Steam520)
![GitHub Sponsors](https://img.shields.io/github/sponsors/pboymt?style=flat-square)

## 介绍

本项目启发自[GitHub520](https://github.com/521xueweihan/GitHub520)。

由[TypeScript](https://typescriptlang.org)编写、[Node.js 16+](https://nodejs.org)驱动，提供Steam遭到类似Github被干扰的解决方案。（无需安装）

---

本项目无需安装任何程序，通过修改本地 hosts 文件，试图解决：

- Steam商店 访问速度慢的问题
- Steam商店 中的图片显示不出的问题

解决不了你知道该骂谁。

## 使用方法

### 手动方式

#### 复制下面的内容
```bash
# This file is generated by fetching the ipaddress.com service.
104.102.129.112     steamcommunity.com
104.102.129.112     www.steamcommunity.com
23.1.198.56         store.steampowered.com
23.1.198.56         api.steampowered.com
                    steamcdn-a.akamaihd.net
                    cdn.akamai.steamstatic.com
                    community.akamai.steamstatic.com
                    store.akamai.steamstatic.com
                    cdn.cloudflare.steamstatic.com
23.66.227.126       steam-chat.com

# Update time: 2024/3/10 22:07:00
# Repo URL: https://github.com/pboymt/Steam520
# Hosts END

```

或直接从链接获取[hosts文件](https://raw.githubusercontent.com/pboymt/Steam520/main/hosts)或[JSON文件](https://raw.githubusercontent.com/pboymt/Steam520/main/hosts)。

上面内容会自动定时更新，保证最新有效。

#### 修改 hosts 文件

hosts 文件在每个系统的位置不一，详情如下：

- Windows 系统：`C:\Windows\System32\drivers\etc\hosts`
- Linux 系统：`/etc/hosts`
- Mac（苹果电脑）系统：`/etc/hosts`
- Android（安卓）系统：`/system/etc/hosts`
- iPhone（iOS）系统：`/etc/hosts`

修改方法，把第一步的内容复制到文本末尾：

1. Windows 使用记事本。
2. Linux、Mac 使用 Root 权限：`sudo vi /etc/hosts`。
3. iPhone、iPad 须越狱、Android 必须要 root。

#### 激活生效
大部分情况下是直接生效，如未生效可尝试下面的办法，刷新 DNS：

1. Windows：在 CMD 窗口输入：`ipconfig /flushdns`

2. Linux 命令：`sudo nscd restart`，如报错则须安装：`sudo apt install nscd` 或 `sudo /etc/init.d/nscd restart`

3. Mac 命令：`sudo killall -HUP mDNSResponder`

**Tips：** 上述方法无效可以尝试重启机器。

### 自动方式

**Tip**：推荐 [SwitchHosts](https://github.com/oldj/SwitchHosts) 工具管理 hosts

以 SwitchHosts 为例，看一下怎么使用的，配置参考下面：

- Title: 随意

- Type: `Remote`

- URL: `https://raw.githubusercontent.com/pboymt/Steam520/main/hosts`

- Auto Refresh: 最好选 `1 hour`

如图：

![](./img/switch-hosts.png)

这样每次 hosts 有更新都能及时进行更新，免去手动更新。

### 2.3 One-liner (适用于类Unix系统)

`sed -i "/# GitHub520 Host Start/Q" /etc/hosts && curl https://raw.githubusercontent.com/pboymt/Steam520/main/hosts >> /etc/hosts`
自动更新`/etc/hosts`文件，可以添加到cron定时执行。使用前确保Github520内容在该文件最后部分。

### 2.4 AdGuard Home 用户（自动方式）

在 **过滤器>DNS 封锁清单>添加阻止列表>添加一个自定义列表**，配置如下：

- 名称: 随意

- URL: `https://raw.githubusercontent.com/pboymt/Steam520/main/hosts`（和上面 SwitchHosts 使用的一样）

更新间隔在 **设置>常规设置>过滤器更新间隔（设置一小时一次即可）**，记得勾选上 **使用过滤器和 Hosts 文件以拦截指定域名**。

**Tip**：不要添加在 **DNS 允许清单** 内，只能添加在 **DNS 封锁清单** 才管用。另外，AdGuard for Mac、AdGuard for Windows、AdGuard for Android、AdGuard for IOS 等等 **AdGuard 家族软件** 添加方法均类似。

## TODO
- [x] 定时自动更新 hosts 内容
- [ ] hosts 内容无变动不会更新
- [ ] 寻到最优 IP 解析结果


## 开源协议

本项目随便使用的GNU Public License v3，欢迎贡献代码，谢谢！

