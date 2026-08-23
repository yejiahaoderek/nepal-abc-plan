# Hero 素材 Brief — Nepal ABC 2026

给 higgsfield 用的生成规格。**六件素材已全部交付并接入**（实测规格见 §6）。页面按主题与
视口自动选片，不需要改代码；素材全缺时回落到内置 canvas 星空。

- 夜主题：`hero.jpg`（横）/ `hero-portrait.jpg`（竖）/ `hero.mp4`
- 日主题：`hero-day.jpg`（横）/ `hero-day-portrait.jpg`（竖）/ `hero-day.mp4`
- 选片逻辑：竖屏视口优先加载 portrait，加载失败回落横版；**视频只在 `min-width:761px` 时加载**，
  竖屏手机只用静态图，省下 2 至 3 MB，也避免 16:9 视频把竖版构图中心裁掉
- 主题切换（夜 / 日 / 自动）与 `orientationchange` 都会重新选片

## ⚠️ 意象合成声明（K1 口径，先看这条）

`hero.jpg` 是**意象合成**，不是纪实。两点与页面自己的天文结论不一致，都是刻意的艺术选择：

1. **拱桥与峰顶暖橙点亮在物理上互斥**——点亮时太阳约 −3.5°，天空亮到看不见银河
2. 画面右侧有可辨识的**核心隆起**，而页面 §05-B 的结论是「碗内拍不到银河核心」

因此：**hero 不作天文论证依据**，逐夜可拍内容一律以页面 §06「逐夜安排」表为准。
这句话已同步写进 `initial_plan.md` 的 K1 与页面 §06 顶部的提示条。
下一版若要走纪实口径，按 §5 验收清单最后两项重出图。

---

## 0. 硬约束（先看这段）

页面把 hero 当满屏背景用（`object-fit: cover`），文字压在**左下角**，上面盖了一层
自下而上的黑色 scrim。所以：

| 项 | 要求 |
|---|---|
| 画面下方 40% | 必须暗、必须低细节。文字在这里，任何亮部或高频纹理都会打架 |
| 画面上方 55% | 视觉重点全部放这里：银河拱桥 + 峰线 |
| 安全区 | 左下 55% × 40% 区域内不要放主体。桌面端被标题、副标题、按钮、四个数字占满 |
| 右上角 | 也留空。桌面端有一个素材位说明框（接入后可以删） |
| 构图重心 | 略偏右，给左侧文字让位 |

移动端是竖屏裁切（中心裁），所以**主体不能贴左右边缘**，否则竖屏看不到。

---

## 1. 色彩规格（必须和页面一致）

页面的配色是"暖黑底 + 点亮橙 + 星空冰蓝"，素材必须用同一套。

```
天空底      #000000  纯黑，不要深蓝天空、不要藏青
银河/星光   #8AB4D4 → #CBD8E4   冷灰蓝，低饱和
亮星        #FFF6EC  微暖白
峰顶点亮    #E9834F  唯一暖色，只出现在最高那道脊线上
山体        #040404  近乎全黑的剪影，几乎没有细节
```

**明令禁止**：紫色、洋红、青橙互补调色（teal & orange）、霓虹、过饱和银河、
HDR 化的星云粉紫、镜头光晕、无人机航拍味的广角畸变。

参考现实基准：Bortle 2-3 级夜空实拍，白平衡锁 3800-4100K，不加饱和。这也正好是
计划里写死的拍摄参数，素材和真实成片要在同一个色温世界里。

---

## 2. hero.jpg — 静态底图

| 参数 | 值 |
|---|---|
| 比例 | 16:9 主版 + 9:16 竖版（`hero-portrait.jpg`）。**两版都已交付并接入**，竖屏视口优先加载竖版 |
| 分辨率 | ≥ 2560×1440，交付 JPEG quality 82-86 |
| 目标体积 | ≤ 480 KiB（山上网络烂，首屏要快；按二进制读，不是十进制 kB） |
| 模型建议 | Soul / Seedream / FLUX 都行，挑出图最干净、星点最实的那个 |

### 构图

一条横贯画面的**银河拱桥**从左下升起、过天顶、落向右下（页面术语里的"拱桥"，
不是竖直的银河核心）。下方是 Annapurna 圈谷的**黑色山脊剪影**，主峰略偏右，
占画面高度约三分之一。整体感觉是"人站在碗底往上看"，不是航拍。

可选：右侧山脊上一个极小的人形剪影，头灯是一个针尖大的暖点。这是计划里
"让人做尺度"那条的视觉呼应。人要**非常小**，占画面高度不超过 2%。

### Prompt（英文，直接可用）

```
Ultra-wide night landscape from the floor of a glacial cirque in the Nepal
Himalaya. The Milky Way forms a full arch across the top of the frame, rising
from lower left, passing the zenith, descending to lower right. Cold desaturated
blue-grey star clouds, pinpoint stars, deep pure black sky, no nebula colour.
Below, a jagged snow-peak ridgeline rendered as an almost pure black silhouette
with no visible surface detail, main summit slightly right of centre, occupying
roughly the lower third. A single thin warm amber rim of alpenglow on the very
top edge of the highest ridge only. Lower left area of the frame is empty dark
sky and shadow. Real astrophotography look: 21mm, f/2.8, 15 second exposure,
white balance 3900K, Bortle 2 sky, no saturation boost, no lens flare, no
vignette, no HDR. Cinematic, restrained, documentary.
```

### Negative prompt

```
purple, magenta, teal and orange grade, neon, oversaturated, colourful nebula,
lens flare, light leak, HDR glow, drone aerial view, fisheye distortion, people
in foreground, tent, campfire, text, watermark, logo, moon in frame, aurora,
clouds covering the sky
```

**别加月亮。**行程里主力拍摄夜是无月窗口，画面出现月亮和整页的天文论证互相打脸。

---

## 3. hero.mp4 — 循环视频

| 参数 | 值 |
|---|---|
| 比例 | 16:9 |
| 分辨率 | 1920×1080，24 fps |
| 时长 | **6 至 8s**（实测交付 6.750s 与 6.500s；Veo 3.1 支持 4 / 6 / 8s，Grok Imagine 可到 6-15s） |
| 循环 | **首尾必须接得上，看不出接缝**。页面是 `loop` + `muted` + `playsinline` |
| 音轨 | 去掉。页面静音播放，音轨只是白占体积 |
| 编码 | H.264 High、`-movflags +faststart`、CRF 23-26 |
| 目标体积 | ≤ 3 MB。超过就降码率，别降分辨率 |

### 运动设计

**几乎不动。**这是一张会呼吸的照片，不是一段视频。允许的运动只有三种：

1. 星空整体极慢的周日旋转，6 秒内位移小到几乎看不出来
2. 稀疏的星点闪烁（不超过 15% 的星）
3. 可选：一颗流星，0.5 秒划过，整段最多一次

**禁止**：镜头推拉、摇移、视差、云层翻滚、山体变形、时间流逝式的快速星轨。
任何一个都会让文字读不下去。

### 生成方式建议

用 **image-to-video**，起始帧直接喂 `hero.jpg`，保证静态图和视频是同一个画面，
切换时不跳。Veo 3.1 的 Start & End Frame 模式最适合做循环：起始帧和结束帧
喂同一张图，接缝自然消失。

### Prompt（英文）

```
Subtle living still. A static night sky over a black Himalayan ridgeline. The
Milky Way arch stays exactly in place. Only extremely slow celestial rotation
and faint twinkling of scattered stars. The camera does not move at all. No
zoom, no pan, no parallax, no cloud movement. Locked-off tripod astrophotography
timelapse, but at almost real-time speed.
```

### Negative prompt

```
camera movement, zoom, pan, dolly, parallax, star trails, fast timelapse,
moving clouds, morphing terrain, people, text, watermark, flicker, exposure shift
```

---

## 4. 交付与接入

```
web/
  index.html
  hero.jpg                ← 已交付并接入（夜 · 横）
  hero-portrait.jpg       ← 已交付并接入（夜 · 竖，竖屏视口优先加载）
  hero.mp4                ← 已交付并接入（夜 · 视频，仅 ≥761px 加载）
  hero-day.jpg            ← 已交付并接入（日 · 横）
  hero-day-portrait.jpg   ← 已交付并接入（日 · 竖）
  hero-day.mp4            ← 已交付并接入（日 · 视频，仅 ≥761px 加载）
```

发布目录同理（把整个 `web/` 内容同步过去即可）。

`.hero-slot` 素材位说明框已从 HTML 删除，残留的两段 CSS 规则也已清理。

## 5. 验收清单

- [x] 桌面 1920×1080 下，左下角标题与四个数字全部读得清
- [x] 移动端 390×844 竖屏用的是 portrait 版，构图完整
- [x] 画面里没有月亮、没有紫色、没有镜头光晕
- [x] 视频循环点看不出接缝
- [x] `hero.jpg` ≤ 480 KiB（实测 474 KiB），`hero.mp4` ≤ 3 MB（实测 2,845 KiB）
- [x] 峰顶那道暖橙只有一条，颜色在 `#E9834F` 附近
- [ ] **画面里没有可辨识的银河核心隆起悬于脊线之上**　❌ 当前 `hero.jpg` 不满足，已按意象合成声明处理
- [ ] **拱桥与点亮不同框，或已明确声明为合成**　已声明为合成

体积红线按 **KiB（二进制）**读：485,437 B = 474 KiB 达标；按十进制读成 485 kB 只超线 1.1%，不值得重压。

## 6. 实测规格（ffprobe，2026-08-23）

| 文件 | 尺寸 | 体积 | 编码 | 时长 |
|---|---|---|---|---|
| `hero.jpg` | 2560×1440 | 474 KiB | JPEG | — |
| `hero-portrait.jpg` | 1440×2560 | 291 KiB | JPEG | — |
| `hero.mp4` | 1920×1080 | 2,845 KiB | h264 / 24fps | 6.750s |
| `hero-day.jpg` | 2560×1440 | 275 KiB | JPEG | — |
| `hero-day-portrait.jpg` | 1440×2560 | 352 KiB | JPEG | — |
| `hero-day.mp4` | 1920×1080 | 2,197 KiB | h264 / 24fps | 6.500s |

全部达标。

## 7. 日间素材组规格（hero-day.*）

日主题的题材是**日照金山**，不是星空，所以色彩规格另立一套；构图安全区与夜版共用（§0）。

| 项 | 要求 |
|---|---|
| 天空底 | 冷白到浅灰蓝，不要纯蓝，不要 HDR 化 |
| 雪峰 | 主峰受晨光直射呈暖金 `#E9A96B` 至 `#D8823F`，背光面留冷青灰 |
| 前景 | 深色山脊或云海压住画面下缘，给左下角文字让位 |
| 禁止 | 过饱和、紫色阴影、teal & orange 调色、人造光晕、可辨识的人物面孔 |
| 比例与体积 | 与夜版同：16:9 加 9:16，视频 6 至 8s，体积红线同 §2 与 §3 |

日间 prompt 基线：

```
High-altitude Himalayan sunrise. First direct sunlight striking the summit
snowfields in warm gold, shadowed faces still cold blue-grey. Sea of cloud
filling the valley below. Cold pale sky, no HDR, no saturation boost, no lens
flare. Documentary alpine photography, tripod, blue hour to golden hour
transition. Lower left of frame is empty dark cloud and shadow.
```
