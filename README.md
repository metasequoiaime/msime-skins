# msime-skins

水杉输入法（Metasequoia IME）的外部皮肤合集。

## 皮肤列表

| 目录 | 名称 | 说明 |
| --- | --- | --- |
| [`niya-demo`](niya-demo/) | Niya Demo | 官方外部皮肤样例：候选框上方的人物装饰图、星点背景图、12dip 圆角，以及配套的悬浮工具栏配色 |
| [`bigfish`](bigfish/) | 蓝色大肥鱼 | 鲸鱼女仆角色装饰、海底气泡背景，深海蓝配色搭配金色序号 |
| [`qq-blue`](qq-blue/) | QQ 经典蓝 | 腾讯 QQ 配色：亮蓝光标与序号，深蓝选中块 |
| [`sogou`](sogou/) | 搜狗经典 | 搜狗经典配色：白底、蓝色候选、橙红高亮、红色光标 |

所有皮肤均基于 `fluent`，支持横排 / 竖排布局以及深色 / 浅色主题。

## 安装

把想用的皮肤目录整个复制到：

```
%LOCALAPPDATA%\metasequoiaime\skins\
```

例如 `%LOCALAPPDATA%\metasequoiaime\skins\qq-blue\skin.toml`，然后在输入法设置中选择对应皮肤即可。

## 皮肤结构

每个皮肤是一个独立目录，至少包含一个 `skin.toml`，图片等资源放在目录内（如 `assets/`）：

```
my-skin/
├── skin.toml
└── assets/          # 可选
    ├── background.png
    └── character.png
```

`skin.toml` 主要字段：

| 表 / 键 | 说明 |
| --- | --- |
| `schema_version` | 皮肤格式版本，目前为 `1` |
| `id` / `name` / `version` / `author` / `description` | 基本信息，`id` 建议与目录名一致 |
| `base` | 继承的内置皮肤，如 `fluent`；未写的键沿用 base |
| `[supports]` | `layouts`（`horizontal` / `vertical`）、`themes`（`dark` / `light`） |
| `[candidate_window]` | `min_width_dip`、`corner_radius_dip`（0–32） |
| `[candidate_window.decoration]` | 卡片上方的装饰图：`image`、`top_inset_dip`、`width_dip`、`align`（`left` / `center` / `right`） |
| `[candidate_window.background]` | 卡片背景图：`image`、`fit`（`cover` / `contain` / `stretch`）、`opacity`（0–1） |
| `[candidate.dark]` / `[candidate.light]` | 候选配色：`accent`、`selected`、`hover`、`surface`、`border`、`text`、`number`、`translation`、`show_selected_bar` |
| `[toolbar]` / `[toolbar.dark]` / `[toolbar.light]` | 悬浮工具栏：`corner_radius_dip`，以及 `background`、`border`、`handle`、`divider`、`icon`、`hover` |
| `[license]` | `code`、`assets`、`source`：代码与素材的授权信息 |

颜色支持 `#RRGGBB` 与 `rgba(r, g, b, a)` 写法。图片路径相对于皮肤目录，且不能指向目录之外。完整的带注释示例见 [`niya-demo/skin.toml`](niya-demo/skin.toml)。

## 授权说明

`niya-demo` 中的图片素材授权尚未核实（`assets = "UNVERIFIED-DEMO-ONLY"`），仅作演示用途，请勿直接用于再分发的皮肤。
