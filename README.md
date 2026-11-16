# FlClash · Concord

基于 [Concord](https://github.com/chen08209/concord) 内核的自用配置与覆写脚本，由 [MeituanRider001/Mihomo](https://github.com/MeituanRider001/Mihomo) 整理而来。

> [!WARNING]
>
> **本项目为个人自用配置**
>
> 按自身机场与使用习惯调整，**非通用方案**，不保证适配所有机场与客户端，也不接受适配类问题反馈。

## 覆写脚本（推荐）

覆写脚本不改动机场订阅正文，客户端启动时动态注入策略组、清洗节点名称、补全国旗。机场换节点后无需手动调整配置，始终与节点列表保持同步。

> [!NOTE]
>
> 脚本仅用于覆写**机场提供的订阅配置**，不要用于覆写本仓库的静态 YAML，二者会互相冲突。

### 全量版

[concord/Script/MihomoScript.js](/concord/Script/MihomoScript.js)，复制下方链接使用 👇

```text
https://raw.githubusercontent.com/MeituanRider001/Flclash/main/concord/Script/MihomoScript.js
```

### 精简版

[concord/Script/MihomoScriptLite.js](/concord/Script/MihomoScriptLite.js)，复制下方链接使用 👇

```text
https://raw.githubusercontent.com/MeituanRider001/Flclash/main/concord/Script/MihomoScriptLite.js
```

---

## 配置文件

静态 YAML 不依赖客户端脚本支持，任何 mihomo 内核客户端与 Concord 均可直接读取；代价是**无法像脚本那样动态处理**，某个地区没有匹配到节点时该策略组会为空。

### 全量版

[concord/Config/MihomoConfig.yaml](/concord/Config/MihomoConfig.yaml) 👇

```text
https://raw.githubusercontent.com/MeituanRider001/Flclash/main/concord/Config/MihomoConfig.yaml
```

### 精简版

[concord/Config/MihomoConfigLite.yaml](/concord/Config/MihomoConfigLite.yaml) 👇

```text
https://raw.githubusercontent.com/MeituanRider001/Flclash/main/concord/Config/MihomoConfigLite.yaml
```

### 代理链版

[concord/Config/MihomoConfigRelay.yaml](/concord/Config/MihomoConfigRelay.yaml) 👇

```text
https://raw.githubusercontent.com/MeituanRider001/Flclash/main/concord/Config/MihomoConfigRelay.yaml
```

适用于「中转入口 + 落地出口」双订阅。两条订阅分别填写：

```yaml
proxy-providers:
  Subscribe-In:                      # 第一跳：中转入口
    url: http://your-entry-provider
    <<: *p
  Subscribe-Out:                     # 第二跳：最终落地
    url: http://your-exit-provider
    <<: *p
    override:
      dialer-proxy: Entry-Group      # 关键：出口节点自动借道入口组
```

`Entry-Group` 绑定 `Subscribe-In` 选择中转节点，`Exit-Group` 绑定 `Subscribe-Out` 选择落地节点，流量路径为 `本机 → Entry-Group → Exit-Group → 目标站点`。

## 免责声明

本项目仅供个人学习与自用。使用本仓库配置所产生的任何后果由使用者自行承担，作者不对可用性、安全性或合规性作任何保证。
