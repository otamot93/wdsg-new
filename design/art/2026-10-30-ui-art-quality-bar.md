# 首版非 demo 美术观感门槛（Godot 4）

| 字段 | 值 |
|---|---|
| 日期 | 2026-10-30 |
| 引擎 | **Godot 4**（现网 4.7.x） |
| 目的 | 首版 UI **不得**像旧仓 demo 灰白默认那么丑；给主程 / UI / UX / 美术共用的**可执行底线** |
| 壳隐喻 | **司令部有雾读图**；**禁止**案头卷宗嵌窗（覆盖旧 art-bible「默认案头」假设） |
| 风格主锚 | B **扁平高级卡通** · `design/art/map_art_direction/refs/style_B_flat_premium.jpg` |
| 配合 UX | 本门槛管**观感与视觉皮**；**不替代** UX 流程 / 可读性 / 命令焦点签收 |
| 已达标样例 | T07 资产批报 + T08 美术人签（见文末索引）；对照样例，勿整段复制 |

---

## 0. 适用范围

**必须遵守**

- `shell_map_command_intel_feed` 默认壳（地图司令部 + 情报抽屉 + 出征/调防确认 + mapmode / 图例 / HUD）
- 同壳下后续面板（势力 / 军务 / 资源等弹层）：至少 **色板 + 控件皮同族**；不要求一次重做全套 icon kit
- Godot 4 玩家可见 UI；headless / 门禁绿 **不等于** 观感过关

**不覆盖**

- 规则层 Hidden 真值、公式、MapProjector 契约
- UX 信息架构与焦点流程签收（另走 UX）
- 旧 `desk-*` 案头五面板（**Deprecated-as-default**，不得当首版默认壳样板）

---

## 1. 色板底线

### 必须

| 项 | 底线 |
|---|---|
| 主气质 | 粉彩 / 羊皮纸暖色；清晰色块、干净外缘 |
| 纸面 | `#E8DCC4`～`#F3E6D0` 一带 |
| 描边 | `#C4A574` / 加强 `#A8844E`；激活强调 `#C45C4A` |
| 正文 | `#3A342C`；次要 `#6A5E50` |
| 政治色强度 | **中**：`color_strength` / `political_alpha` ≈ **0.70**；wash α ≈ 0.48–0.56 |
| 势力例 | 晋 `#6B9EB2` · 昭义 `#BDA061`；州色粉彩可分（见 palette JSON） |
| 河 | `#7EC8D4` 浅蓝 + 轻外晕 |
| 未知 / 雾底 | `#6E7064` 冷灰绿 |

### 禁止

- 工程师默认 **灰白 Theme**（灰 Button / 白 Panel / 蓝默认 focus）当玩家交付
- 霓虹高饱和、纯游戏引擎 debug 色块感
- 用红绿条 / 星级色暗示**可信度**
- 政治色把山河与标签糊死（过强）或看不出势力/州差（过弱）

### 参照

- `design/art/shell_map_command_intel_feed/sources/palette_B_medium.md`
- `…/palette_B_medium.json`
- `…/chrome/chrome_tokens_B.json` → `colors.*`

---

## 2. 控件皮底线

### 必须（同族羊皮纸 / 粉彩）

| 控件 | 底线 |
|---|---|
| 面板 / 抽屉 | 浅羊皮纸底 + 金褐细边；圆角约 4–8；轻阴影可，勿厚拟物 |
| 确认窗 | 浅色模态（`#F7EDDC` 一带）；最高 chrome 层；与地图同族 |
| mapmode 钮 | 扁平面板；未选 / hover / 选中可辨；高约 28–36 px 量级 |
| 图例 | 解释可知色与「未知 / 旧报」；**非**铁轨工具条 |
| 卡片 | 未读 / 已读除颜色外另有非色区分（点、字重、标签） |
| Theme | 新面板优先吃 `chrome_tokens_B` / StyleBoxFlat 同族值，勿裸用 Project 默认 |

### 禁止

- **Godot 默认灰白控件**未经换皮直接进首版截图 / 签收
- 案头卷宗窗框、嵌窗舆图隐喻
- 过重线框、厚 bevel、炫光 hover、仪表盘玻璃拟物
- 确认窗与抽屉一个深黑一个霓虹，气质断裂

### 参照

- `design/art/shell_map_command_intel_feed/sources/chrome/chrome_tokens_B.json`
- `…/chrome/README.md` 与 runtime 皮：`godot/assets/ui/shell_map_command_intel_feed/`
- UX：`design/ux/shell-map-command-intel-feed.md`（抽屉宽、chrome 层级）

---

## 3. 图标 / 雾 / 地图涂色底线

### 地图涂色

| 必须 | 禁止 |
|---|---|
| 单档 1582×994；ID + LUT + compositor | 每帧 CPU 全图政治烤色；第二 LOD；真 3D 地图 |
| 政治色中等；双 mapmode 可分 | 用填色补全未投影 owner / controller |
| 符号化脊线（吕梁—汾河—太行） | 自然写实山脉、铁轨式图例线 |
| 州界软 AA、线偏细软（可沿用 T09-AA） | 近景硬台阶粗墨当终态 |
| 纸缘 = map-space 司令部外缘 | 烤 fog / 动态归属进 `terrain_base` |

### 雾（三档）

| 档 | 必须观感 |
|---|---|
| `unknown` | 浓雾冷灰绿；一眼「不知」 |
| `partial` | 轻雾降清晰，非全知 |
| `stale` | 陈旧洗 ± 细斜线；**≠已证伪**；摘要须来源+日戳 |
| `clear` | 无 FogOverlay 洗 |

禁止：可信度色条；雾层抢 picker；详情/tooltip 出 `Hidden` / `truth_refs` / confidence。

### 图标

- 城标 / 军标：扁平简洁、同色温；可少勿滥
- 图例色键与 palette 一致；可含「未知 / 旧报」，**不含**可信度图例

### 参照

- 雾：`…/sources/fog/fog_B_spec.md` · `fog_params_B.json`
- 地图清单：`…/features/shell_map_command_intel_feed/art_asset_list.md`
- 隔离组样例：`report/.../assets/art_sources_20261029_B/`

---

## 4. 验收怎么判

### 对照锚（必须打开）

1. **风格图**：`design/art/map_art_direction/refs/style_B_flat_premium.jpg`
2. **色板 / tokens**：`palette_B_medium.*` · `chrome_tokens_B.json`
3. **已达标样例（引用，不复制）**：  
   - T07：`ai-sdlc-docs/versions/V0.0.1/report/shell_map_command_intel_feed/assets/T07_ART_BATCH_20261029.md`  
   - T07 雾/chrome：`…/T07_FOG_CHROME_20261030.md`  
   - T08 美术人签：`…/T08_ART_SIGN.md` + `windows/t08_art_matrix_20261030/`

### 判据

| 结论 | 条件 |
|---|---|
| **pass** | 真实 Godot **窗口**（非 headless）双 mapmode 可见；色板/控件同族羊皮纸粉彩；有雾读图；山河/界可读；无下列 fail |
| **fail** | 灰白默认 Theme 当交付；霓虹/调试色；过重线框或仪表盘感；无雾（邻境全知涂色）；铁轨图例；可信度条/星级色；卷宗嵌窗当默认壳；仅门禁绿无窗口图 |
| **blocked** | 无 GPU / 无真实窗口可采；关键资产未接线导致无法对照 |

### 谁签什么

| 角色 | 签 |
|---|---|
| 美术 | 色 / 皮 / 山河 / 界 / 雾 / chrome 同族（本门槛） |
| UX | 流程、可读、焦点、遮挡、文案字段（**另签**；本门槛不代替） |
| 主程 / UI | 接线不破坏管线；不把默认 Theme 冒充已换皮 |

自动化门禁只守数据/结构；**观感必须以实际窗口为准**。

---

## 5. 给主程 · UI · UX 的速查

### 主程 / UI 程序

- 新 Panel / Button / 弹层：先套 `chrome_tokens_B` StyleBox，再谈功能
- 地图只接兼容 atlas / LUT / FogOverlay；不烤 fog 进 r9 terrain
- 详情与 tooltip：**禁止**接 `confidence` 到玩家文案或色条
- 截图签收前自查：是否还在用默认灰按钮

### UX

- 壳 = 司令部 + 情报流；抽屉约 280–320 px；确认窗最高层
- 评审对照 style_B + T08 窗口矩阵；流程项按 UX 清单，不与本门槛混成一项「全绿」

### 美术 / 技术美术

- 增量资产走隔离目录 + validate；禁直接盖 `godot/assets/map/r9/` 除非发布签收明示
- 新面板 icon 保持 B 扁平；不够就 tokens 纯色块，也胜过默认灰

---

## 6. 一句话红线

> **首版玩家截图里，不许一眼看出「这是没换皮的 Godot demo」。**  
> 羊皮纸粉彩同族、司令部有雾、中等政治色；无卷宗嵌窗、无灰白默认、无可信度色条。

---

## 索引

| 文档 | 用途 |
|---|---|
| `design/ux/shell-map-command-intel-feed.md` | UX IA |
| `design/art/map_art_direction/refs/style_B_flat_premium.jpg` | 视觉主锚 |
| `design/art/shell_map_command_intel_feed/sources/*` | 色板 / chrome / 雾源 |
| `design/art/art-bible.md` | 历史案头美学参考；**壳关系以本门槛与 shell UX 为准** |
| `…/report/shell_map_command_intel_feed/T08_ART_SIGN.md` | 已达标窗口样例签收 |
