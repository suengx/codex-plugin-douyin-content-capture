# codex-plugin-douyin-content-capture

这是 `douyin-content-capture` 的**独立分发仓库**。

它的目标很单一：

- 给 Codex 提供单技能粒度的 marketplace 安装入口
- 给 Python 用户提供可直接安装的 `douyin-capture` CLI

如果你只想在 Codex 里安装这一个技能，应该使用本仓库，而不是源码总仓库。

## Codex 安装

添加这个单技能 marketplace：

```bash
codex plugin marketplace add suengx/codex-plugin-douyin-content-capture
```

建议随后开启一个新 thread，再显式使用：

```text
使用 $douyin-content-capture 帮我处理这个抖音链接
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

