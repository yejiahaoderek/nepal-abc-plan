# AGENTS.md — nepal-abc-plan

面向在此 repo 工作的 AI agent（Claude Code / Codex / Pi / OpenClaw 等）。人类用户：Jet（帅）。

## 事实源与裁决顺序

- `initial_plan.md` 是唯一事实源，当前 **v1.3**（Part A-K + 附录）。
- **Research bridge（持续输入）**：`research/hatch-abc-reference.md` — 指向公开干净页 `https://agent.meta.ai/s/abc-2026-oxr60xzdxpxx1cq`（as of 2026-08-31），含路线/地图、风险 Q&A、guide/porter/jeep 候选、T-14/T-7/T-24–48h 触发器；**网页是 research input，不自动覆盖事实源**，需按 L0-L3 证据等级提 delta 后合入。
- 路线 / 风险 / 交通 / 保险类任务的读取顺序：`initial_plan.md` → `research/hatch-abc-reference.md`（check As of 与「已知冲突项」）→ `CONTEXT.md` → 对比 last reviewed 时间再合入。该页的行程逻辑信息（会合地、班次、闸门日期）已知与事实源冲突，勿引用。
- 冲突裁决顺序：**Part K > Part G / H / I / J > Part C > Part B**；Part D 已整体作废仅存档；Part E 为过期开放问题存档。
- 术语一律用 `CONTEXT.md` 定义（E 版 / D 版 / 预案② / 降级形态 / 无月窗口 / 拱桥 / 核心机位 / 点亮 / 进山证 / 保险三轨 / 4,600m 红线）。
- 任何数字、日期、价格带核查状态（证实 / 证伪 / 核实中）与来源日期，沿用 Part G-J / K 写法；未核实的写「核实中」，不得写成事实。
- 日期用绝对表述（YYYY-MM-DD 或 M/D）。

## 修改流程

1. 先改 `initial_plan.md`，再改衍生物（网页、简报、邮件草稿）。
2. `initial_plan.md` 实质修改后：同步 `web/index.html` 内容 → 用 pagedrop 技能重发同一 slug（保持 URL 稳定）→ commit → push。
3. 内容同步不触碰设计系统；设计方向以 `web/` 内既有文件为准。
4. Hero 素材由 higgsfield 按 `web/HERO_ASSET_BRIEF.md` 规格生成；六件已交付（2026-08-23），页面按夜/日主题自动选素材，零改码接入。

## 发布

- 官网：https://private.jetd.one/2026-08-23-nepal-abc-2026/（Jet 的 private 空间，SSO 保护；深链对未登录返回 401 是 2026-08-31 前后的 Hermes 侧行为变化，非本 repo 发布问题）
- 发布目录须与 repo 的 `web/` 逐字节一致。
- pagedrop 操作细节看 pagedrop 技能；SSO / 权限问题看 hermes-ops 技能。

## Git

- remote：`ssh://git@ssh.github.com:443/jetd1/nepal-abc-plan.git`（本机网络封 22 端口，2026-09-01 起 SSH 走 443；若换网络后 22 可用可改回 `git@github.com:jetd1/nepal-abc-plan.git`）。
- main 直推；不留未提交改动。
- commit / PR 末尾带 harness 对应 trailer（Claude Code：`Co-Authored-By: CCCha <cccha@jetd.one> via Claude Code`）。

## 结构

- `initial_plan.md` — 计划本体（Part A-K + 附录），单一事实源
- `research/hatch-abc-reference.md` — Hatch ABC 研究稳定桥接（canonical: `https://agent.meta.ai/s/abc-2026-oxr60xzdxpxx1cq`，as of 2026-08-31），机器可读入口，L0-L3 证据等级与 merge 规则
- `CONTEXT.md` — 术语表
- `webpage-extract-raw.txt` — Meta AI 原计划抽取存档，只读（旧链 `abc-2026-ye-and-shuai` 已废弃）
- `outreach/` — 向导社询价邮件草稿（当前 v3，三家同发）
- `review/` — 对抗审查 findings 存档（只读，不作为事实源）
- `web/` — 计划网页（`index.html`）与 hero 素材（六件：夜/日 × 横/竖图 + 夜视频）、`HERO_ASSET_BRIEF.md`

## 当前状态与关键节点（2026-09-02 口径）

- **2026-09-02 路况**：KTM↔PKR 陆路（Prithvi Highway）09-01 在 Dhading Krishnabhir 完全断路（08-26 以来第二次），断路期间 10/6 航班取消的陆路兜底不存在；进山口 Birethanti / Modi Khola 两轮冲毁（07-12、08-13/14）后无通车通告，Ghurjung 桥修复无消息。详见 `initial_plan.md` G1「最新状态」与 G1b。

- v1.3 完成：94 条对抗审查 findings 已采纳（89 workflow + 5 Codex，存档 `review/2026-08-23-findings.md`）。
- **2026-09-03 深度审计**：`review/2026-09-03-findings.md`（195 条 findings，存活 193：P0 5 / P1 23 / P2 111 / INFO 54；20 条更优方案候选；只读存档，**尚未采纳入 `initial_plan.md`**）。P0 全部是执行层逾期项（国际 / 国内机票未出票、定社逾期、叶证件与 MSP 未闭合、保险 J5 未闭合、摄影两人未指名、疫苗）；户外侧新增硬缺口：Kimrong（Ghurjung）吊桥 2026-07-12 冲毁压在 9/30 Tadapani→Chhomrong 徒步主线、Jhinu 温泉 2026-08-13 全毁、9/28 与 10/5 时间链算术证伪。采纳时按该文件「对 initial_plan.md 的修改清单」逐 Part 合入，DISPUTED 条目先裁决。
- 待 Jet 拍板：10/6 PKR→KTM 班次甲/乙（计划推荐乙 16:50/18:00）、摄影两人指名（8/26 已过，阻塞器材清单与专属背夫分配）、Dwarika's 房型（默认 Junior Suite ×2）、小费档（默认上调档 $550-700）、在途值守人。
- 关键日期：9/13 前国内三人装备采购打包；9/13-9/15 入境在线预填；9/16 + 9/19 Birethanti/Ghurjung 实地复查；**9/20 E/D 版闸门**（未通车切 D-Phedi 形态）；9/24 晚叶值机；9/26 四人加都会合。
- Birethanti 是进出山共同瓶颈（2026-08-14 冲毁抢修中），出山侧对称预案与 D-Phedi 完整逐日表见 G1 / G6。

## 行为红线（改计划不得触碰）

- **4,600m 红线**：行程任何时刻越过 4,600m（乘机除外），Global Rescue 野外救援与医疗转运同时失效。禁止任何加垭口 / 加高点动议，此条写进向导社合同。
- 保险出单前 J5 八项书面确认逐轨闭合；叶 MSP 无效且无替代医疗层 = 出行阻断项。
- 直升机应急只能由队员自己联系保险 / Global Rescue 发起；向导社、向导、山屋、医院无发起权（2026 年尼泊尔假救援骗保案背景）。
- 被诉直升机公司避开：Mountain Helicopters、Manang Air（现名 Basecamp Helicopters）、Altitude Air。
- **隐私**：本 repo 为 public。任何文件不得新增团员真名、可识别昵称、GitHub 用户名或护照 / 证件信息；既有化名（叶 / 帅 / Jet）不扩展。对外页面只用「四位团员」或 A/B/C/D 代号。
