# codex-plugin-douyin-content-capture

这是 `douyin-content-capture` 的**独立分发仓库**。

它的目标很单一：

- 给 Codex 提供单技能粒度的 marketplace 安装入口
- 给 Python 用户提供可直接安装的 `douyin-capture` CLI

如果你只想在 Codex 里安装这一个技能，应该使用本仓库，而不是源码总仓库。

## Codex 安装

添加这个单技能 marketplace。注意：这一步只是添加市场源；本仓库的策略是
`policy.installation: "AVAILABLE"`，不会把插件默认全量启用。

```bash
codex plugin marketplace add suengx/codex-plugin-douyin-content-capture
```

如果已经添加过，升级到最新版：

```bash
codex plugin marketplace upgrade suengx-douyin-content-capture
```

然后完全重启 Codex，在插件/市场界面按需安装或启用
`douyin-content-capture`。启用后，新 thread 可用中文 Slash 触发：

```text
/抖音内容抓取
```

也可以直接用自然语言或抖音分享文案触发：

```text
帮我抓取这个抖音视频，并输出转写和报告入口：
https://v.douyin.com/xxxxx/
```

### 干净复测

当前 Codex CLI 没有 `codex plugin install/remove` 子命令；卸载市场请使用：

```bash
codex plugin marketplace remove suengx-douyin-content-capture
```

如需清掉旧缓存后完整复测，可在移除 marketplace 后执行：

```bash
mv ~/.codex/plugins/cache/suengx-douyin-content-capture ~/.codex/plugins/cache/suengx-douyin-content-capture.bak-$(date +%Y%m%d%H%M%S) 2>/dev/null || true
mv ~/.codex/.tmp/marketplaces/suengx-douyin-content-capture ~/.codex/.tmp/marketplaces/suengx-douyin-content-capture.bak-$(date +%Y%m%d%H%M%S) 2>/dev/null || true
```

## Python CLI 安装

完整转写版：

```bash
python -m pip install "douyin-capture[transcribe] @ git+https://github.com/suengx/codex-plugin-douyin-content-capture.git@main#subdirectory=plugins/douyin-content-capture/python-package"
```

轻量版：

```bash
python -m pip install "douyin-capture @ git+https://github.com/suengx/codex-plugin-douyin-content-capture.git@main#subdirectory=plugins/douyin-content-capture/python-package"
```

## 仓库结构

- `.agents/plugins/marketplace.json`：只暴露一个 plugin 的 marketplace
- `plugins/douyin-content-capture/`：插件本体、skill 适配层和 Python 包

## 源码仓库

统一开发仓库在：

- [suengx/codex-skills](https://github.com/suengx/codex-skills)
