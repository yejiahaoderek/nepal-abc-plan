# Hero 素材 Brief — Nepal ABC 2026

给 higgsfield 用的生成规格。页面已经预留好接口：把成品命名为 `hero.jpg` 与 `hero.mp4`
放进 `web/`（以及发布目录）即可自动接管，**不需要改任何代码**。没放的时候，页面用内置
canvas 星空占位。

- `hero.jpg` 存在 → 顶掉 canvas，作为静态底图
- `hero.mp4` 存在且能播 → 再顶掉静态图，自动静音循环播放
- 两个都没有 → canvas 星空（星等分布 + 银河拱带 + 山脊剪影 + 峰顶点亮线）

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
| 比例 | 16:9 主版；另出 9:16 竖版备用（命名 `hero-portrait.jpg`，需要时再接） |
| 分辨率 | ≥ 2560×1440，交付 JPEG quality 82-86 |
| 目标体积 | ≤ 480 KB（山上网络烂，页面首屏要快） |
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
| 时长 | 6s 或 8s（Veo 3.1 支持 4 / 6 / 8s；Grok Imagine 可到 6-15s） |
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
  hero.jpg          ← 放这里
  hero.mp4          ← 放这里
  hero-portrait.jpg ← 可选，暂未接
```

发布目录同理（把整个 `web/` 内容同步过去即可）。

接入后记得删掉 `index.html` 里那个 `.hero-slot` 素材位说明框，它现在挂在
`<div class="hero-slot">`，直接整段删就行。

## 5. 验收清单

- [ ] 桌面 1920×1080 下，左下角标题与四个数字全部读得清
- [ ] 移动端 390×844 竖屏裁切后，银河拱桥还在画面里
- [ ] 画面里没有月亮、没有紫色、没有镜头光晕
- [ ] 视频循环点看不出接缝
- [ ] `hero.jpg` ≤ 480 KB，`hero.mp4` ≤ 3 MB
- [ ] 峰顶那道暖橙只有一条，颜色在 `#E9834F` 附近
