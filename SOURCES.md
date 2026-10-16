# 规则来源与修改记录

本文件用于集中履行来源标注和修改说明。路径均相对于仓库根目录。

## ACL4SSR

- 上游：[ACL4SSR/ACL4SSR](https://github.com/ACL4SSR/ACL4SSR)
- 核对版本：a32b0cb（2026-08-31）
- 许可证：[CC BY-SA 4.0](./LICENSES/CC-BY-SA-4.0.txt)
- 适用文件：
  - rules/ad/*.list
  - rules/domestic/ChinaDomain.list
  - rules/domestic/Download.list
  - rules/domestic/ip/ChinaCompanyIp.list
  - rules/domestic/media/ChinaMedia.list
  - rules/domestic/network/LocalAreaNetwork.list
  - rules/domestic/services/*.list
  - rules/global/ProxyGFWlist.list
  - rules/global/ai/AI.list
  - rules/global/games/*.list
  - rules/global/media/BilibiliHMT.list
  - rules/global/media/Netflix.list
  - rules/global/media/ProxyMedia.list
  - rules/global/media/YouTube.list
  - rules/global/messaging/Telegram.list
  - rules/global/services/Apple.list
  - rules/global/services/Notion.list
  - rules/global/services/microsoft/*.list
- 本仓库修改：重新组织目录、统一为 Clash classical 文本格式、更新部分规则、移除单文件内完全重复条目和 Mihomo 不支持的 `URL-REGEX` 条目，并同步修改配置引用。

### Notion 补充来源

`rules/global/services/Notion.list` 在 ACL4SSR 的 `notion.so` 规则基础上，按照 [Notion 官方网络白名单](https://www.notion.com/help/allowlist-ip) 补充当前域名及自有 IPv4/IPv6 网段。

## 17mon / IPIP.NET

- 上游：[17mon/china_ip_list](https://github.com/17mon/china_ip_list)
- 核对版本：ad96987
- 许可证：[CC BY-NC-SA 4.0](./LICENSES/CC-BY-NC-SA-4.0.txt)
- 适用文件：rules/domestic/ip/ChinaIp.list
- 本仓库修改：在原始 CIDR 前添加 Clash IP-CIDR 类型，并添加 no-resolve 参数、注释和统计信息。
- 重要限制：该数据仅可用于非商业用途。

## 苍狼山庄 ISP IP

- 上游：[ispip.clang.cn](https://ispip.clang.cn/)
- 原始数据：all_cn_ipv6.txt
- 适用文件：rules/domestic/ip/ChinaIpV6.list
- 本仓库修改：转换为 Clash IP-CIDR6 classical 规则。
- 许可状态：上游页面提供准确性免责声明，但截至 2026-08-31 未找到明确的开放许可证。本仓库不对该数据授予再许可；公开再分发或超出个人使用前，应向数据提供方确认授权。

## blackmatrix7 / ios_rule_script

- 上游：[blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script)
- 许可证：[GPL-2.0](./LICENSES/GPL-2.0-only.txt)
- 适用文件：
  - rules/global/media/AmazonPrimeVideo.list
  - rules/global/media/Emby.list
  - rules/global/services/Nvidia.list
- 原始 Emby 作者与来源：justdoiting/emby-rules，相关信息保留在规则文件头部。
- 本仓库修改：移除 YAML payload 包装、转换为 Clash classical 文本格式、去除完全重复条目。

### Amazon Prime Video

- 上游文件：rule/Clash/AmazonPrimeVideo/AmazonPrimeVideo.list
- 核对版本：933875d42861a7fdfd9f945cd18605d74fa7e943。
- 本仓库修改：保留原始 26 条 classical 规则及作者信息，添加许可证和上游版本注释，并补充下述一条精确域名规则。该规则集独立于 Amazon 商城和通用 AWS 规则集。

#### 补充端点

- `prod.us-east-1.sonar.prime-video.amazon.dev`：出现在 [Prime Video 客户端流量日志](https://github.com/ajstrick81/morphe-androidtv-patches/issues/48)中，按完整主机名添加 `DOMAIN` 规则，避免扩大到整个 `amazon.dev`。
- 核对日期：2026-10-16；以上为社区日志证据，未在本环境中验证真实客户端播放。

## 本仓库自定义内容

- ClashVerge.ini
- README.md
- LICENSE.md
- SOURCES.md

这些内容没有声明来自上述上游；权利由对应贡献者保留。
