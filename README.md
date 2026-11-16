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

## 致谢

- [MetaCubeX/mihomo](https://github.com/MetaCubeX/mihomo)
- [chen08209/concord](https://github.com/chen08209/concord)
- [AIsouler/MyClash](https://github.com/AIsouler/MyClash)

## 免责声明

本项目仅供个人学习与自用。使用本仓库配置所产生的任何后果由使用者自行承担，作者不对可用性、安全性或合规性作任何保证。
