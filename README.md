# Surge 规则配置完全指南

Surge 是 iOS/macOS 上最强大的代理工具，本教程介绍进阶规则配置。

## 基本结构

```ini
[General]
loglevel = notify
allow-wifi-access = true

[Proxy]
ProxyA = http, your-proxy.com, 8080

[Proxy Group]
AutoSelect = url-test, ProxyA, interval=300
Manual = select, ProxyA

[Rule]
DOMAIN-SUFFIX,google.com,AutoSelect
GEOIP,CN,DIRECT
FINAL,Manual
```

## 策略组类型

| 类型 | 说明 | 使用场景 |
|------|------|---------|
| url-test | 自动测速选择最快 | 日常浏览 |
| fallback | 优先第一个，失败切换 | 重要节点 |
| load-balance | 轮询分配 | 分担流量 |
| select | 手动选择 | 自选节点 |

## 实用规则模板

```ini
# 广告拦截
DOMAIN-SUFFIX,doubleclick.net,REJECT

# 社交媒体
DOMAIN-SUFFIX,facebook.com,Proxy

# 国内网站
DOMAIN-SUFFIX,baidu.com,DIRECT
GEOIP,CN,DIRECT

# 默认
FINAL,Proxy
```

---

推荐工具：

- [Clash for Windows](https://clashforwindows.site/)
- [ClashMI](https://clashmi.site/)
- [FlClash](https://flclash.us/)
