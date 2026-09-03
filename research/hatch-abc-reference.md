# research/hatch-abc-reference.md — Hatch ABC Research Bridge

> 供此 repo 内所有 AI agent（Claude Code / Codex / Pi / OpenClaw / Meta AI 等）持续 reference 的稳定入口。
> 本文件是 **机器可读 + 人可读** 的 canonical bridge，不存完整计划正文，只存：去哪看、什么时候更新的、能信到什么程度、怎么合进 `initial_plan.md`。

## 1. Canonical Source

- **公开页（干净版，去个人信息）**：`https://agent.meta.ai/s/abc-2026-oxr60xzdxpxx1cq`
  - Slug：`abc-2026`
  - 标题：`2026-08 泥石流对 10 月 ABC 的影响`（含 T-14 / T-7 / T-24–48h 触发器）
  - As of：**2026-08-31**（页面口径）
  - **Last verified：2026-09-02（CCCha）**：页面 HTTP 200 可达；正文无真名（用「四位团员」与 A/B/C/D 代号）；含风险简报 `#risk-2026-08`、T−14 / T−7 / T−24–48h 触发器、路线地图、三家示例渠道、两程吉普节点。
  - 旧链（已废弃，勿引用）：`https://agent.meta.ai/s/abc-2026-ye-and-shuai-xzv5xtxmxvxvxtxrx0xf` — 含人名，已被新链取代，仅在 `webpage-extract-raw.txt` 作存档

- **本地镜像**：本 repo 不存网页全文镜像，避免 drift。如需快照，引用 `webpage-extract-raw.txt`（旧版）+ 本文件时间戳。

## 2. 页面提供什么（能力清单）

| 能力 | 页面有 | 本 repo 事实源 |
|---|---|---|
| 路线与地图（图例先看 + 跟手轮播） | ✅ 可视化卡片，手机可读 | `initial_plan.md` Part G6 E版 为准 |
| 风险 Q&A（2026-08 灾害） | ✅ 地图后、机票前独立章节 | 需按 §4 规则合入 Part C / K |
| guide / porter / jeep 候选 | ✅ 候选清单（待核验书面确认） | `outreach/` 询价后以书面确认为准 |
| T-14 / T-7 / T-24–48h 决策框架 | ✅ 触发器卡片 | `initial_plan.md` Part K4 / AGENTS.md 行为红线 |
| 航班 / 保险 / 进山证入口 | ⚠️ 入口卡片，未直链章节 | 以 Part H / J 为准 |

> **已知与事实源冲突项（2026-09-02 核对，页面仍在线显示）**：
> - 页面「已确认：西雅图→上海已定；9-25 上海会合确定」「9/25 四位团员在上海会合」：**2026-09-03 翻转：已证实**。叶 DL281 SEA→PVG（9/24 16:00 → 9/25 19:50 T1，Flying Blue 里程票，**已出票**，叶 PR #2）；❌ 原「3U 经成都 9/26 抵 KTM」作废。**9/26 四人会合方式待帅确认**（四人 PVG 同机 vs 帅组维持 9/25 21:40 隔夜联程），以 initial_plan.md H2 为准。
> - 页面「9/16 合同硬闸门 · 定向导」：事实源 H6 P0-1 定社窗口为 2026-08-23 当周；9/16 在事实源里是 Birethanti 第一次实地复查日。
> - 页面吉普节点「Samrung 最深但常断路 / Syauli 柏油尽头最稳 / Matkyu 河边老叫法」：事实源 G5 只核到 Samrung；Syauli 作为停车点**核实中**，可作询价时的追问项。
> 结论：该页的**行程逻辑信息一律以 `initial_plan.md` 为准**；只把它的风险 Q&A、触发器框架与询价字段当 research input。

## 3. 证据等级（Provenance）

按 LLM 专家视角，合入时必须标注：

- **L0 官方来源**：ACAP/NTNC、TAAN、NTB、尼泊尔民航局、USGS、WHO Nepal。日期 + URL 必带。
- **L1 当地 operator 书面确认**：向导社邮件 / WhatsApp 截图，含确认人、日期、流域/路段。
- **L2 商业来源**：航司、酒店、保险条款页，需截图 + 访问日期。
- **L3 推测 / 模型**：skyfield 天文、地形仰角估算、LLM 总结，标「推测」不得写成事实。

冲突解决：L0 > L1 > L2 > L3；同级以时间新者为准；任何未标注等级的数字不得写入 `initial_plan.md`。

## 4. Merge 规则（技术专家视角）

1. **网页 = research input，不自动覆盖 `initial_plan.md`**。`initial_plan.md` 仍是唯一事实源。
2. 先提 delta：对比 `last reviewed` 与网页更新时间，列出新增/变更事实。
3. 再核验：
   - 来源日期 ≥ 2026-08-26？
   - 流域/路线关联：是否落在 **Modi Khola / Birethanti / ABC 进出走廊**？还是 **Rasuwa / Lhende Khola / Bhote Koshi / Trishuli** 系统？
   - 不把「尼泊尔灾害」泛化为全国停摆。
4. 最后写入：按 Part K > G/H/I/J > C > B 裁决顺序，带核查状态（证实/证伪/核实中）与来源日期。
5. 禁止把网页文案整段复制成第二份计划。

## 5. 2026-08 灾害必须区分（尼泊尔 hike 专家视角）

### 5.1 2026-08-14 Birethanti / Modi Khola 暴洪
- **直接影响 ABC**：进出山共同瓶颈，道路冲毁抢修中。
- Repo 已有预案：
  - 2026-09-16 + 09-19 实地复查
  - 2026-09-20 E/D 版闸门（未通车切 D-Phedi）
  - 2026-09-25 ~ 09-27 再复查
  - 2026-10-03 出山路线确认
- 对称预案与 D-Phedi 逐日表见 G1 / G6。

### 5.2 2026-08-26 Rasuwa / Bhote Koshi 冰岩崩塌—泥石流—洪水
- **主体不在 ABC**：初步机制 = 高海拔冰岩崩塌 → 临时堵河 → 溃决含泥石山洪 → 沿 Lhende Khola / Bhote Koshi / Trishuli 传播（USGS preliminary）。
- **对 ABC 是间接风险**：
  1. 季风尾声新滑坡、道路/桥梁中断（尤其 Kathmandu–Pokhara 地面交通可能受广泛季风修复影响）
  2. 航班/物资/地面接驳延误
  3. 沿线饮水与食物卫生（WASH）
  4. 后续官方 closure / 持续强降雨预警 / outbreak alert
- WHO 列出 Gandaki Province 的 Gorkha、Tanahun 为受影响区之一，方向是按流域说关联，不写"完全隔壁省无关"，也不泛化成全国疫情。
- **截至 2026-08-31**：USGS/WHO 均为 preliminary，当前无证据需因 08-26 事件直接取消 10 月 ABC，按 T-14/T-7 再复核。

### 5.3 写作方向（不是硬封禁，是怎么把话说对）

> 目标：让后续 agent 写风险时，不为了自洽而发明数字或确定性。

- **不编概率**：没有 USGS/WHO/官方给的数字，就不写 `<5%`、`10–15%` 这类。方向是写机制和触发器：「截至 2026-08-31 的 preliminary 判断，08-26 主体在 Rasuwa 侧流域，对 ABC 是间接提醒，当前无证据需直接取消，见 §5.2 和来源链接」。
- **不把地理切成两块**：不写"完全不同省所以无关"，也不写"全国都受影响"。方向是按流域和走廊说：「08-14 落在 Modi Khola / Birethanti（ABC 进出瓶颈），08-26 落在 Lhende / Bhote Koshi / Trishuli，WHO 也提到 Gandaki 的 Gorkha/Tanahun，两件事分开看，全国交通/WASH 是间接提醒」。
- **不武断说路没事**：Kathmandu–Pokhara 公路是否受损要看当日复核和修复进度，方向是「需在 T-14/T-7 复核 Prithvi 公路 Muglin 段、航班、物资接驳」。
- **不拿"没通知"当证据**：NTB/TAAN/ACAP 是否有关闭，方向是「标复核日期和来源，写'截至某日未见关闭公告，需 T-7 再查'」。
- **不把"照常"写成结论**：方向是「现在维持行程，不因社交媒体传言取消；最终 go/no-go 看 ABC 沿线官方状态和当地书面确认」。

### 5.4 行动阈值（产品经理视角）
- **现在**：维持行程，不因社交媒体传言取消；最终 go/no-go 只看 ABC 沿线官方状态和当地书面确认。
- **T-14**：向 ACAP/NTNC、TAAN、当地向导、航司复核。（按 9/28 进山起算 ≈ 9/14；事实源 H6 已有 **9/16 + 9/19 两次实地复查、9/20 E/D 闸门**，日期以 H6 为准，T-14 框架只作对照）
- **T-7**：复核饮水系统、道路通断、航班。（≈ 9/21，落在 H6 闸门次日；对应事实源 9/25-9/27 抵尼后的复查与 9/27 briefing）
- **T-24–48h**：官方关闭、连续 flash-flood warning、饮水系统中断或 outbreak alert 才触发 Plan B。
- Agent 快速回答模板：「现在要不要取消？」「什么时候触发 Plan B？」「谁确认、确认什么？」— 不堆材料，直接给触发器。

## 6. 对 Agents 的固定读取顺序

任何处理路线、风险、交通、保险问题时：

1. `initial_plan.md`（唯一事实源，v1.3，Part K > G/H/I/J > C > B）
2. `research/hatch-abc-reference.md`（本文件，check `As of`）
3. `CONTEXT.md`（术语）
4. 对比 `last reviewed` 时间，网页新增事实按 L0-L3 等级纳入
5. 写回 `initial_plan.md` 时带来源 + 日期 + 核查状态

## 7. 维护

- 本文件 `As of` 每次网页更新后手动 bump，格式 `YYYY-MM-DD`。
- 链接健康检查：每月 `curl -I https://agent.meta.ai/s/abc-2026-oxr60xzdxpxx1cq`，2xx 正常，4xx/5xx 报修。
- 关键来源（截至 2026-08-31）：
  - USGS 2026 Nepal debris avalanche and flash flood: https://www.usgs.gov/programs/landslide-hazards/science/2026-nepal-debris-avalanche-and-flash-flood（preliminary/provisional）
  - WHO Nepal 2026 Rasuwa flash floods: https://www.who.int/nepal/emergencies/2026-rasuwa-flash-floods

## 8. 隐私

- 公开页仅用「四位团员」或 A/B/C/D 代号，**不得出现任何团员真名、可识别昵称或 GitHub 用户名**（本节亦不得罗列真名作「黑名单」：本 repo 为 public，罗列即泄露）。
- 本 repo 为 **public**：`initial_plan.md` 内的化名叶 / 帅 / Jet 已是既成公开信息，不再扩展；航班号、酒店、日期等行程细节已公开在 repo，团员自行评估。`web/index.html` 走 SSO private 空间，发布前仍做脱敏检查。

## 9. UI/UX 方向（轻量灵感，非硬性规定）

> 给后续改 `web/index.html` 和公开页的 agent 看的：不是硬规，是思考方式。Agent 自己做网页是 OK 的，可参考现有网页设计，取好的整合。

核心问题：小白一眼能不能看懂顺序是否合理。

### 建议顺序（已验证好用，灵感级）

1. **Overview + 地图** — 四人十三天摘要 + 地图直接嵌在一起，一句话说清 9/25-10/07 去哪儿，地图标出各种方案（E 版 vs D-Phedi 分歧点可视），图例先看再看图
2. **To-do 展开** — 待拍板清单可展开看细节，不一次性全铺；全局可达：顶部 sticky nav `本周待办` 和 Hero `本周待办 · 8 项` 都是指向 `#booking` 的浮动锚点，任何位置都能一键跳到待办
3. **具体详情** — 装备 / 航班 / 保险 / 进山证，按需展开
4. **Timeline** — 关键节点时间线，不做 micro Day 计数，回指地图上的段

这个顺序是产品直觉：先给全貌和空间锚点（Overview + 地图），再给待办，再给细节，最后具体到时间。

### 地图本身是很好的 — 怎么守住

> 用户原话：地图本身是很好的。方向是保留优点，不把问题修成仪表盘。

- 地图保留地形肌理、路线高程和重要节点，E 版与 D-Phedi 分歧点在图上可视，不藏进长文
- 横向卡片原生跟手拖动，有惯性、回弹、snap，手机一指可拨
- 地图前固定"图例先看"，不让用户猜符号
- 不为"功能完整"改成高对比 dashboard，保留现有视觉体系
- 地图直接在 Overview 段可视，不藏到 Timeline 之后

### 给 Agent 的灵感

- 现有 `web/index.html` 的纸感、留白和信息层级已经是对的，改时参考它，不要推翻重做
- 可复制的原文 / 信件与操作按钮放同卡，不让用户跳页
- 风险 Q&A 保持"地图后、机票前"，不要因为补信息把它移到最前或最后
- 风险数字带 `as of` 和来源，不写死结论
- 少一点，不要硬性规定：给方向和例子，不给 `--bg:#000000` 这类底线式规定

---
*Maintained by Hatch (阿宝) — LLM / 尼泊尔 hike / 技术 / 产品四视角。*
