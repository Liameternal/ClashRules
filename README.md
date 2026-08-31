# ClashRules

供 Clash / Mihomo 及兼容客户端使用的分流规则库。规则采用 Clash `classical` 文本格式，可作为 `rule-providers` 引用。

规则文件只描述“匹配哪些流量”，不决定直连、代理或拒绝。实际路由动作由 Clash 配置中的规则顺序和策略组决定。例如，位于 `global/services/Apple.list` 的规则仍可在配置中指向直连策略。

## 目录结构

```text
rules/
├── ad/
│   ├── BanAD.list
│   ├── BanProgramAD.list
│   └── UnBan.list
├── domestic/
│   ├── ChinaDomain.list
│   ├── Download.list
│   ├── ip/
│   │   ├── ChinaCompanyIp.list
│   │   ├── ChinaIp.list
│   │   └── ChinaIpV6.list
│   ├── media/
│   │   └── ChinaMedia.list
│   ├── network/
│   │   └── LocalAreaNetwork.list
│   └── services/
│       ├── GoogleCN.list
│       └── GoogleFCM.list
└── global/
    ├── ProxyGFWlist.list
    ├── ai/
    │   └── AI.list
    ├── games/
    │   ├── Epic.list
    │   ├── Game.list
    │   ├── Nintendo.list
    │   ├── Sony.list
    │   ├── Steam.list
    │   └── Xbox.list
    ├── media/
    │   ├── BilibiliHMT.list
    │   ├── Emby.list
    │   ├── Netflix.list
    │   ├── ProxyMedia.list
    │   └── YouTube.list
    ├── messaging/
    │   └── Telegram.list
    └── services/
        ├── Apple.list
        ├── Nvidia.list
        ├── Notion.list
        └── microsoft/
            ├── Microsoft.list
            └── OneDrive.list
```

- `ad`：广告、应用净化和误杀白名单。
- `domestic`：国内域名、IP、媒体、网络及相关服务。
- `global`：国外通用流量以及 AI、媒体、游戏、通信和厂商服务。

文件名尽量沿用 ACL4SSR 的语义名称，便于与上游直接比较和同步。不为统一目录形式额外创建没有明确业务含义的 `general.list`。

## 合集与细分规则

ACL4SSR 的 `ProxyGFWlist.list`、`ProxyMedia.list` 等合集可以独立使用，也会与 `AI.list`、`YouTube.list` 等细分规则产生交集。这是上游规则的预期结构，不代表文件被重复复制。

同时使用合集和细分规则时，应把细分 provider 放在合集之前。Clash 按规则顺序首次匹配生效，因此可以让 AI、YouTube 等进入独立策略组，其余内容再由合集接管。单个文件内部的完全重复条目会被清理，跨文件的上游交集则予以保留。

## Clash Verge 配置

[`ClashVerge.ini`](./ClashVerge.ini) 是 Clash Verge Rev 的扩展配置片段，已同步当前目录下的 Raw GitHub URL。当前主要顺序为：

1. 局域网和广告误杀白名单；
2. 广告拦截；
3. 国内媒体、域名、IP 与服务；
4. AI、Microsoft、Telegram、游戏、YouTube、Nvidia、Notion 和国外媒体；
5. `ProxyGFWlist` 通用国外规则；
6. `MATCH` 兜底。

配置只加载当前实际使用的 provider。Netflix、Emby 和 Bilibili 港澳台等文件保留为可选规则，可根据需要添加 provider。

规则 provider 每 24 小时检查一次更新。从旧版升级时，根目录下的 `*.list` 已迁移到 `rules/`，旧 Raw URL 不再有效。新目录和配置应在同一次提交中发布。

## 来源与许可证

本仓库是多来源规则集合，不适用单一许可证，主要用于个人、非商业用途：

- ACL4SSR 衍生规则遵循 CC BY-SA 4.0。
- 17mon/IPIP.NET 中国 IPv4 数据遵循 CC BY-NC-SA 4.0，不得用于商业目的。
- blackmatrix7 衍生文件按其仓库声明遵循 GPL-2.0。
- 中国 IPv6 数据来源页面未提供明确开放许可证，公开再分发前应另行确认。

完整的逐类来源、上游版本和修改记录见 [SOURCES.md](./SOURCES.md)，许可证全文及适用范围见 [LICENSE.md](./LICENSE.md) 和 [LICENSES/](./LICENSES/)。

上游规则核对日期：2026-08-31。
