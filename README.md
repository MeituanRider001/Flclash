# FlClash · Concord

基于 [Concord](https://github.com/chen08209/concord) 内核的自用配置与覆写脚本，由 [MeituanRider001/Mihomo](https://github.com/MeituanRider001/Mihomo) 整理而来。

> [!WARNING]
>
> **本项目为个人自用配置**
>
> 按自身机场与使用习惯调整，**非通用方案**，不保证适配所有机场与客户端，也不接受适配类问题反馈。

## 目录结构

```text
concord/
├── Config/          静态 YAML，Concord 可直接读取
│   ├── MihomoConfig.yaml
│   ├── MihomoConfigLite.yaml
│   └── MihomoConfigRelay.yaml
└── Script/          mihomo 覆写脚本，需客户端支持脚本覆写
    ├── MihomoScript.js
    └── MihomoScriptLite.js
```

## 配置文件

| 文件 | 策略组 | 说明 |
|---|---|---|
| `MihomoConfig.yaml` | 23 | 全量：5 地区手动组 + 5 自动测速组 + `Other` + 功能分流组 |
| `MihomoConfigLite.yaml` | 17 | 精简：5 地区手动组 + 功能分流组，无 `Other` 与自动组 |
| `MihomoConfigRelay.yaml` | 25 | 代理链：全量 + 入口 / 落地双订阅 |

## 覆写脚本

| 文件 | 行数 | 说明 |
|---|---|---|
| `MihomoScript.js` | 584 | 全量版，策略组与分流规则最完整 |
| `MihomoScriptLite.js` | 508 | 精简版，策略组更少 |

Concord 内核本身只读取 YAML、不执行脚本；`Script/` 供支持脚本覆写的客户端使用。

## Concord 适配

以下字段在 Concord 中被忽略或不受支持，本仓库的配置与脚本已移除：

| 字段 | 级别 | 说明 |
|---|---|---|
| `bind-address` | T2 | 忽略 |
| `external-controller` | T1 | 嵌入 App 时由 App 接管 |
| `external-ui` / `external-ui-url` | T2 | Concord 不提供 Web UI |
| `tun.auto-redirect` | T2 | 忽略 |
| `geodata-mode` | T2 | Concord 只读 mmdb，`GeoIP.dat` 不生效 |
| `geox-url.geoip` | T2 | 同上 |

`path-in-bundle` 在 Concord 中会直接导致整份配置被拒绝、全部流量走直连，本仓库未使用该字段。

分层的含义：T0 完全支持，T1 部分支持，T2 忽略并产生 `unsupported_key` 警告。定义见 Concord 的 `crates/config/src/keys.rs`。

## 图标

策略组图标托管在 [Mihomo 仓库](https://github.com/MeituanRider001/Mihomo/tree/main/Icons/svg)，脚本中的 `iconBaseUrl` 指向该地址，无需在本仓库另存。

## 致谢

- [MetaCubeX/mihomo](https://github.com/MetaCubeX/mihomo)
- [chen08209/concord](https://github.com/chen08209/concord)
- [AIsouler/MyClash](https://github.com/AIsouler/MyClash)

## 免责声明

本项目仅供个人学习与自用。使用本仓库配置所产生的任何后果由使用者自行承担，作者不对可用性、安全性或合规性作任何保证。
