<h1 style="text-align: center;" align="center">
浙江电信IPTV单组播收集
</h1>


<h3 style="text-align: center;" align="center">
🆓免费提供 ✅简单易用 ⏰高频更新 🔍自动检测 📥多格式输出 🧩自定义订阅 🔁EPG镜像
</h3>
<div style="text-align: center;" align="center">
<img alt="GitHub Repo stars" src="https://img.shields.io/github/stars/FHZDCJ/Zhejiang_Telecom_IPTV?style=flat">
<img alt="GitHub forks" src="https://img.shields.io/github/forks/FHZDCJ/Zhejiang_Telecom_IPTV?style=flat">
<img alt="GitHub Issues or Pull Requests" src="https://img.shields.io/github/issues/FHZDCJ/Zhejiang_Telecom_IPTV">
<img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/FHZDCJ/Zhejiang_Telecom_IPTV">
</div>


---

## 目录

- [项目简介](#项目简介)
- [频道分辨率及有效性报告](#频道分辨率及有效性报告)
- [项目文件说明](#项目文件说明)
- [使用方法](#使用方法)
    - [订阅链接形式列表](#订阅链接形式列表)
    - [使用台标](#使用台标)
    - [使用.txt文件](#使用txt文件)
- [免责声明 / Disclaimer](#免责声明--disclaimer)

---

## 项目简介

本项目从互联网收录浙江电信IPTV的组播源及单播源地址，提供`.m3u`、`.txt`、`.csv`格式的列表，提供台标。

> ⚠️特别提示：本项目中的全部组成部分来自互联网整理收集，所有内容仅供参考，不可访问。

## 频道分辨率及有效性报告

本项目定期从互联网收集频道分辨率及有效性，并提供报告：

- [浙江组播源检测报告](https://myepg.org/Zhejiang_Multicast/report.html)
- [浙江单播源检测报告](https://myepg.org/Zhejiang_Unicast/report.html)

## 项目文件说明


#### 浙江组播（Zhejiang_Multicast）：


- `Zhejiang_Multicast.m3u`：使用本地台标的m3u列表。
- `Zhejiang_Multicast_OL.m3u`：使用在线台标的m3u列表。
- `Zhejiang_Multicast.txt`：txt格式频道列表。
- `Zhejiang_Multicast.csv`：频道清单。

#### 杭州单播（Zhejiang_Unicast）：


- `Zhejiang_Unicast.m3u`：使用本地台标的m3u列表。
- `Zhejiang_Unicast_OL.m3u`：使用在线台标的m3u列表。
- `Zhejiang_Unicast.txt`：txt格式频道列表。
- `Zhejiang_Unicast.csv`：频道清单。

## 使用方法

### 链接形式列表

你可以在通过以下链接获取自定义播放列表文件：

```
https://myepg.org/api/subscribe/{source}/{type}?udpxy=你的IP:端口&logo=你的地址&ip=替换IP
```

#### 参数说明：

| 参数名 | 示例值 | 必填 | 说明 |
|--------|--------|:----:|------|
| `source` | `multicast` 或 `unicast` | 是 | 数据源类型，组播或单播 |
| `type` | `m3u` 或 `txt` | 是 | 输出文件格式 |
| `udpxy` | `10.30.0.1:2340` | 组播必填 | 格式为 IPv4:端口 |
| `logo` | `logo.example.com` 或 `192.168.1.2:8080` | 否 | 仅当 `type=m3u` 时有效，替换模板中的 `{{your_logo_address}}` |
| `ip` | `10.0.0.1` | 否 | 仅当 `source=unicast` 时有效，替换 RTSP URL 中的 IP 地址 |
| `nocache` | - | 否 | 拒绝使用缓存 |

系统会自动将模板中的 `{{your_udpxy_address}}` 替换为你提供的地址；如果传入了 `logo` 参数且 `type=m3u`，还会替换 `{{your_logo_address}}`。

#### 示例请求

```
# 组播M3U，使用在线台标
https://myepg.org/api/subscribe/multicast/m3u?udpxy=192.168.1.1:2345

# 组播TXT
https://myepg.org/api/subscribe/multicast/txt?udpxy=192.168.1.1:2345

# 组播M3U，使用自定义台标
https://myepg.org/api/subscribe/multicast/m3u?udpxy=192.168.1.1:2345&logo=192.168.1.1:8090

# 单播M3U
https://myepg.org/api/subscribe/unicast/m3u

# 单播M3U，替换RTSP中的IP
https://myepg.org/api/subscribe/unicast/m3u?ip=x.x.x.x

# 单播M3U，拒绝缓存
https://myepg.org/api/subscribe/unicast/m3u?nocache
```

#### 请求限制

为节约服务器资源，本接口有数据缓存，即使源已更新，对于相同的URL请求在一定时间内可能会得到相同的缓存数据，在此情形下不会记入请求次数中。如您需要获取最新数据，可以自行添加 `nocache` 参数。

### 使用台标

**本地台标**：下载 `.m3u` 文件，替换 `{{your_logo_address}}` 为你的 Logo 存放 URL，替换 `{{your_udpxy_address}}` 为 UDPXY 地址。

**在线台标**：下载 `_OL.m3u` 文件（如 `Zhejiang_Multicast_OL.m3u`），仅需替换 `{{your_udpxy_address}}`。

### 使用.txt文件

下载 `.txt` 文件，替换 `{{your_udpxy_address}}` 即可。

---

# 免责声明 / Disclaimer

## 1. 本项目仅供学习与研究用途

本项目中使用的地址来源于网络收集，禁止用于任何商业行为、违反电信用户协议以及违反法律法规的用途。作者不对使用者的任何行为或后果承担责任。

## 2. 项目提示

本项目中的 IPTV 地址仅供参考，不可访问。本项目**不提供任何破解、模拟或绕过认证的工具或方法**。

## 3. 内容版权说明

项目中提及或内嵌的频道名称、台标（Logo）、节目单等，均来源于网络收集。版权归属原版权方与电信运营商所有。项目仅用于组播地址格式演示与技术分析，**未包含任何节目内容或流媒体数据**。

## 4. 责任免除声明

本项目作者不持有任何 IPTV 内容的版权，也不对任何使用本项目所引发的问题（包括但不限于账号封禁、网络封锁、法律责任）承担责任。**使用者对本项目的任何形式的使用（包含但不限于拷贝、分发）必须自行承担一切风险和后果。**

---

> ⚠️ 请合理合法使用本项目内容，禁止用于任何违反当地法律或运营商规定的行为。
