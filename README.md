# rule

## 特别声明

1. 本项目内所有资源文件，禁止任何公众号、自媒体进行任何形式的转载、发布。
2. 编写本项目主要目的为学习和研究ES6，无法保证项目内容的合法性、准确性、完整性和有效性。
3. 本项目涉及的数据由使用的个人或组织自行填写，本项目不对数据内容负责，包括但不限于数据的真实性、准确性、合法性。使用本项目所造成的一切后果，与本项目的所有贡献者无关，由使用的个人或组织完全承担。
4. 本项目中涉及的第三方硬件、软件等，与本项目没有任何直接或间接的关系。本项目仅对部署和使用过程进行客观描述，不代表支持使用任何第三方硬件、软件。使用任何第三方硬件、软件，所造成的一切后果由使用的个人或组织承担，与本项目无关。
5. 本项目中所有内容只供学习和研究使用，不得将本项目中任何内容用于违反国家/地区/组织等的法律法规或相关规定的其他用途。
6. 所有基于本项目源代码，进行的任何修改，为其他个人或组织的自发行为，与本项目没有任何直接或间接的关系，所造成的一切后果亦与本项目无关。
7. 所有直接或间接使用本项目的个人和组织，应24小时内完成学习和研究，并及时删除本项目中的所有内容。如对本项目的功能有需求，应自行开发相关功能。
8. 本项目保留随时对免责声明进行补充或更改的权利，直接或间接使用本项目内容的个人或组织，视为接受本项目的特别声明。

## 支持

本项目对 Loon、QuantumultX、AdGuard Home、Surge 提供完全支持

优先级：Loon = AdGuard Home = Surge > QuantumultX > Clash

> 经过鄙人的重构，现在提供 Host, DomainSet, Loon, QuantumultX 的支持，各位可以按需引用

> 被迫修改了一些规则的路径和名字，我尽量保证此类事件不再发生

## 使用方法

优先级从高到低：

```ini
FuckRogueSoftware
ProxyRules
...
AppleAPIRules
AppleNoChinaCDNRules
AppleCDNRules
AppleRules
...
DirectRules
BaseRules
```

### Loon

#### Loon 分流规则

```conf
# 去广告
https://raw.githubusercontent.com/kimtomgo/rule/main/ConfigFile/Loon/LoonRemoteRule/FuckRogueSoftwareRules.conf, policy=Advertising, tag=FuckRogueSoftware, enabled=true

# 自定义的代理
https://raw.githubusercontent.com/kimtomgo/rule/main/ConfigFile/Loon/LoonRemoteRule/ProxyRules.conf, policy=PROXY, tag=CustomProxy, enabled=true

https://raw.githubusercontent.com/kimtomgo/rule/main/ConfigFile/Loon/LoonRemoteRule/TelegramRules.conf, policy=PROXY, tag=TelegramRules, enabled=true

# Apple 规则

#Apple update 
#AppleUpdate = select,DIRECT,Proxy,REJECT-DROP,img-url = https://raw.githubusercontent.com/Koolson/Qure/master/IconSet/Color/Apple_Update.png

https://raw.githubusercontent.com/kimtomgo/rule/main/ConfigFile/Loon/LoonRemoteRule/Apple/AppleUpdateRules.conf, policy=AppleUpdate,tag=AppleUpdate, enable=true

https://raw.githubusercontent.com/kimtomgo/rule/main/ConfigFile/Loon/LoonRemoteRule/Apple/AppleNoChinaCDNRules.conf, policy=AppleProxy, tag=AppleNoChinaCDN, enabled=true

https://raw.githubusercontent.com/kimtomgo/rule/main/ConfigFile/Loon/LoonRemoteRule/Apple/AppleAPIRules.conf, policy=AppleProxy, tag=AppleAPI, enabled=true

https://raw.githubusercontent.com/kimtomgo/rule/main/ConfigFile/Loon/LoonRemoteRule/Apple/AppleRules.conf, policy=AppleDirect, tag=AppleRules, enabled=true

https://raw.githubusercontent.com/kimtomgo/rule/main/ConfigFile/Loon/LoonRemoteRule/Apple/AppleCDNRules.conf, policy=AppleDirect, tag=AppleCDN, enabled=true


# 自定义的直连
https://raw.githubusercontent.com/kimtomgo/rule/main/ConfigFile/Loon/LoonRemoteRule/DirectRules.conf, policy=DIRECT, tag=CustomDirect, enabled=true

https://raw.githubusercontent.com/kimtomgo/rule/main/ConfigFile/Loon/LoonRemoteRule/BaseRules.conf, policy=DIRECT, tag=BaseRules, enabled=true

```

### Surge

配置示例

```ini
# REJECT Rules
RULE-SET,https://raw.githubusercontent.com/kimtomgo/rule/refs/heads/main/ConfigFile/Surge/FuckRogueSoftware/domain.list,REJECT,pre-matching
# RULE-SET,https://raw.githubusercontent.com/kimtomgo/rule/refs/heads/main/ConfigFile/Surge/FuckGarbageFeature/domain.list,REJECT,pre-matching

# Apple Update Rules
RULE-SET,https://raw.githubusercontent.com/kimtomgo/rule/refs/heads/main/ConfigFile/Surge/Apple/update-domain.list,AppleUpdate

# ...
# Apple Rules
RULE-SET,https://github.com/kimtomgo/rule/raw/refs/heads/main/ConfigFile/Surge/Apple/no-cn-cdn-domain.list,AppleNoChinaCDN
RULE-SET,https://github.com/kimtomgo/rule/raw/refs/heads/main/ConfigFile/Surge/Apple/api-domain.list,AppleApi
RULE-SET,https://github.com/kimtomgo/rule/raw/refs/heads/main/ConfigFile/Surge/Apple/cdn-domain.list,AppleCDN
RULE-SET,https://github.com/kimtomgo/rule/raw/refs/heads/main/ConfigFile/Surge/Apple/domain.list,Apple
# ...
```


### 对于 FuckRogueSoftware 规则的说明

此规则对某些国内软件强屏蔽，包括但不限于广告，跟踪，数据分析

在 [FuckRogueSoftware.txt](https://github.com/kimtomgo/rule/blob/main/ConfigFile/DataFile/FuckRogueSoftware/domain.txt) 中可以看到部分屏蔽说明

```
# qx
https://raw.githubusercontent.com/kimtomgo/rule/main/ConfigFile/QuantumultX/FuckRogueSoftwareRules.conf, force-policy=FuckRogueSoftware, tag=FuckRogueSoftware, enabled=true

# loon
https://raw.githubusercontent.com/kimtomgo/rule/refs/heads/main/ConfigFile/Loon/FuckRogueSoftware/domain.list, policy=FuckRogueSoftware, tag=FuckRogueSoftwareDomainRules, enabled=true
https://raw.githubusercontent.com/kimtomgo/rule/refs/heads/main/ConfigFile/Loon/FuckRogueSoftware/ip.list, policy=FuckRogueSoftware, tag=FuckRogueSoftwareIPRules, enabled=true

# Surge
RULE-SET,https://raw.githubusercontent.com/kimtomgo/rule/refs/heads/main/ConfigFile/Surge/FuckRogueSoftware/domain.list,REJECT,pre-matching
RULE-SET,https://raw.githubusercontent.com/kimtomgo/rule/refs/heads/main/ConfigFile/Surge/FuckRogueSoftware/ip.list,REJECT
```

### Apple 系统更新

另外，若有屏蔽 Apple 系统更新的需求，可以引用 `AppleUpdateRules` 规则集

```
# loon
AppleUpdate = select,REJECT-DROP,DIRECT,img-url = https://raw.githubusercontent.com/Koolson/Qure/master/IconSet/Color/Apple_Update.png

https://raw.githubusercontent.com/kimtomgo/rule/main/ConfigFile/Loon/LoonRemoteRule/Apple/AppleUpdateRules.conf, policy=REJECT ,tag=AppleUpdate, enable=true

# qx
static= AppleUpdate, reject, direct, img-url = https://raw.githubusercontent.com/Koolson/Qure/master/IconSet/Color/Apple_Update.png

https://raw.githubusercontent.com/kimtomgo/rule/main/ConfigFile/QuantumultX/Apple/AppleUpdateRules.conf, force-policy=AppleUpdate, tag=AppleUpdateRules, enabled=true
```

### 对于 Apple 解锁功能

请查看 [iRingo 解锁完整的 Apple 功能和集成服务](https://github.com/VirgilClyne/iRingo) 仓库

**建议优先采用上文仓库的规则**

### 对于 Apple 分流规则

请参考 [blog.royli.dev/2019/better-proxy-rules-for-apple-services 这篇文章](https://blog.royli.dev/2019/better-proxy-rules-for-apple-services)

对于本项目

AppleRules 是与本地化息息相关的规则，比如地图、天气、查找、Facetime、Apple Pay
( iCloud 上传与下载也归于此规则集

AppleCDNRules 是苹果的全球 CDN

AppleNoChinaCDNRules 是大陆没有的 CDN 节点

AppleAPIRules 是苹果的 API 域名

请把 NoChinaCDN 和 APIRules 放在最前面

#### 使用中国区账号（App Store + iCloud）

AppleRules 直连

AppleCDNRules 直连

AppleNoChinaCDNRules 代理

AppleAPIRules 直连

#### 使用美国区账号（App Store + iCloud）

AppleRules 直连

AppleCDNRules 直连

AppleNoChinaCDNRules 代理

AppleAPIRules 代理

建议 AppleAPIRules 依然直连，上文是根据上述文章给出的建议，请结合自身情况使用

### Loon 插件

#### DNSMap

对常用的国内域名进行 DNS 解析分流，国内走国内的各大 Doh

```
# DNS 映射
https://raw.githubusercontent.com/kimtomgo/rule/main/ConfigFile/Loon/LoonPlugin/DNSMap.plugin, tag=DNS Map, enabled=true
```

#### 抖音屏蔽

部分规则来自 [https://gist.github.com/JamesHopbourn/b5cf9219bdacfa8b6dbb3414276c149b](https://gist.github.com/JamesHopbourn/b5cf9219bdacfa8b6dbb3414276c149b)

在此表示感谢

```
# FuckDouyin
https://raw.githubusercontent.com/kimtomgo/rule/main/ConfigFile/Loon/LoonPlugin/FuckDouyin.plugin, proxy=Advertising, tag=Fuck Douyin, enabled=true
```


## 项目路线图

- [x] 自动化根据规则集生成适配不同客户端的规则文件
- [x] 去重，根据域名后缀去重
- [] 构造域名后缀树，从 HashMap 切换到域名后缀树
- [] 对大佬们的 AdGuard 规则进行去重合并

## 感谢

本项目的数据大部分来自一下项目，在此对他们表示感谢（以下排名不分先后

[SukkaW/Surge](https://github.com/SukkaW/Surge)

[surge-list](https://github.com/geekdada/surge-list)

[GetSomeFries](https://github.com/VirgilClyne/GetSomeFries)

[ios_rule_script](https://github.com/blackmatrix7/ios_rule_script)

[NextDNS 维护的系统级跟踪列表](https://github.com/nextdns/metadata/tree/master/privacy/native)

[Shadowrocket-ADBlock-Rules](https://github.com/h2y/Shadowrocket-ADBlock-Rules)

[neohosts](https://github.com/neoFelhz/neohosts)

[gfwlist](https://github.com/gfwlist/gfwlist)

[SS-Rule-Snippet](https://github.com/Hackl0us/SS-Rule-Snippet#%E5%85%B3%E4%BA%8E%E9%A1%B9%E7%9B%AE)

[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR/tree/master)

[anudeepND-blacklist](https://github.com/anudeepND/blacklist)

[neodevhost](https://github.com/neodevpro/neodevhost)

[BlueSkyXN-AdGuardHomeRules](https://github.com/BlueSkyXN/AdGuardHomeRules)

[WindowsSpyBlocker](https://github.com/crazy-max/WindowsSpyBlocker)

[hoshsadiq/adblock-nocoin-list](https://github.com/hoshsadiq/adblock-nocoin-list/)

