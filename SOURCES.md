# 规则来源与修改记录

本文件用于集中履行来源标注和修改说明。路径均相对于仓库根目录。

## ACL4SSR

- 上游：[ACL4SSR/ACL4SSR](https://github.com/ACL4SSR/ACL4SSR)
- 核对版本：a32b0cb（2026-08-31）
- 许可证：[CC BY-SA 4.0](./LICENSES/CC-BY-SA-4.0.txt)
- 适用文件：
  - rules/ad/*.list
  - rules/domestic/ChinaDomain.list
  - rules/domestic/applications/Download.list
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
  - rules/global/services/microsoft/*.list
- 本仓库修改：重新组织目录、统一为 Clash classical 文本格式、更新部分规则、移除单文件内完全重复条目和 Mihomo 不支持的 `URL-REGEX` 条目，并同步修改配置引用。

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
  - rules/global/media/Emby.list
  - rules/global/services/Nvidia.list
- 原始 Emby 作者与来源：justdoiting/emby-rules，相关信息保留在规则文件头部。
- 本仓库修改：移除 YAML payload 包装、转换为 Clash classical 文本格式、去除完全重复条目。

## 本仓库自定义内容

- ClashVerge.ini
- README.md
- LICENSE.md
- SOURCES.md

这些内容没有声明来自上述上游；权利由对应贡献者保留。
