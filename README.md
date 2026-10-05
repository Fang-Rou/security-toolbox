# security-toolbox

> 一张**工具清单**，不是工具集合本身。

本地 `D:\security tools` 攒了 3 年，里面有 3 GB 多二进制（Burp、goby、Wireshark、Android platform-tools…）。
直接往 GitHub 推既超单文件限制、又撞各家许可证，所以这里只做**选型笔记**：每个工具一行——用途、官方地址、我常用的版本、一句话评价。

需要时按表去官网下，不要从这里 clone 二进制。

## 抓包 / 代理

| 工具 | 用途 | 官方地址 | 备注 |
|---|---|---|---|
| Burp Suite | Web 抓包改包重放 | https://portswigger.net/burp | 社区版免费；专业版订阅。日常主力 |
| mitmproxy | 命令行 / 脚本化 HTTPS 代理 | https://mitmproxy.org/ | 配合 addon 做自动化抓包改包 |
| Proxifier | 强制指定进程走代理 | https://www.proxifier.com/ | 抓 PC 客户端、APP 流量必装 |
| Wireshark | 二层协议分析 | https://www.wireshark.org/ | 排非 HTTP 问题时用 |

## 侦察 / 资产测绘

| 工具 | 用途 | 官方地址 | 备注 |
|---|---|---|---|
| OneForAll | 子域名收集 | https://github.com/shmilylty/OneForAll | 多引擎聚合，结果去重 |
| subDomainsBrute | 子域爆破 | https://github.com/lijiejie/subDomainsBrute | OneForAll 漏的再用它爆 |
| EHole | 资产指纹 / 端口 | https://github.com/EdgeSecurityTeam/EHole | 红队资产识别 |
| enscan | 端口 + 指纹 | 见 GitHub 搜 `enscan` | 轻量，跑 C 段顺手 |
| fofa_reverse | 公司名 → 资产 | 自研脚本 | 本地脚本，见 pt-workbench |
| Goby | 图形化资产测绘 + POC 框架 | https://gobysec.net/ | 国产，POC 库更新快 |
| superSearchPlus | FOFA / Hunter 批量检索 | 见 GitHub 搜 `superSearchPlus` | 多语法导出 |

## Web 扫描 / 漏洞

| 工具 | 用途 | 官方地址 | 备注 |
|---|---|---|---|
| dirsearch | 目录扫描 | https://github.com/maurosoria/dirsearch | 字典要自己换 big.txt |
| sqlmap | SQL 注入自动化 | https://github.com/sqlmapproject/sqlmap | 改 tamper 绕 WAF |
| JSFinder | JS 接口 / 参数提取 | https://github.com/Threezh1/JSFinder | 挖隐藏 API |
| GitHack | 从 `.git` 还原源码 | https://github.com/lijiejie/GitHack | 泄露场景 |
| ds_store_exp | `.DS_Store` 泄露利用 | https://github.com/lijiejie/ds_store_exp | 苹果机扫出来的目录 |
| CSRFTester | CSRF PoC 构造 | https://github.com/bestony/CSRFTester | 老牌，聊胜于无 |

## 移动端 / 调试

| 工具 | 用途 | 官方地址 | 备注 |
|---|---|---|---|
| scrcpy | 投屏控制 Android | https://github.com/Genymobile/scrcpy | 无 root 也能控制 |
| platform-tools | adb / fastboot | https://developer.android.com/tools/releases/platform-tools | 安卓调试基础 |
| bp-extend | Burp 插件合集 | 见本地 `bp-extend/` | 含 encoder、token 自动重放等 |

## 浏览器

| 工具 | 用途 | 官方地址 | 备注 |
|---|---|---|---|
| Firefox 46.0 + HackBar | 老版本浏览器 | 历史存档 | 复现老漏洞、绕新版浏览器 CSP / SRI |
| HackBar | 地址栏编码 / payload 构造 | https://hackbar.com/ | 老插件版还能用 |

## 选型原则

1. **能脚本化就不用 GUI**：Burp 点一下能做的事，写进 `pt-workbench` 的 scripts 里才能复用。
2. **每个工具只解决一个问题**：不要在 Goby 里做注入，它的活是测绘。
3. **版本跟着靶场走**：老漏洞复现用老环境（Firefox 46、JDK 8），新业务用新工具。
4. **不囤破解版**：Burp 专业版、Proxifier 这种商业工具，自己用社区版或走授权。

## License
本仓库是清单笔记，不包含任何第三方工具二进制。各工具遵循其自身许可证。
