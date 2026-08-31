# CLAUDE.md — nepal-abc-plan

尼泊尔 ABC 2026 徒步计划 repo。4 人：叶（YVR 出发，中国护照、常居加拿大）、帅 + 两位朋友（PVG 出发，中国护照）。假期窗口 2026-09-25 ~ 10-07，固定不可移；行程实际跨度叶 2026-09-24 ~ 10-08、国内三人 2026-09-25 ~ 10-07（保险按实际跨度出单，见 `CONTEXT.md`）。

## 规则

- `initial_plan.md` 是唯一事实源。改网页、简报等衍生物之前，先改它。
- 术语一律用 `CONTEXT.md` 的定义（点亮、拱桥、核心机位、无月窗口、E 版 / D 版、进山证、野奢、保险三轨 / 4,600m 红线 / 预案② / 降级形态）。
- 任何数字、日期、价格必须带核查状态（证实 / 证伪 / 核实中，附来源与信息日期），沿用各核查组 Part（G / H / I / J / K）的写法。未核实的不得写成事实。
- 日期用绝对表述（YYYY-MM-DD 或 M/D），禁止"下周"类相对日期。
- **网页发布**：`web/index.html` 是计划的对外呈现。`initial_plan.md` 每次实质修改后，同步更新网页内容并用 pagedrop 技能重新发布到 Jet 的 private 空间（复用同一 drop，保持 URL 稳定）。改内容不改设计系统；设计方向以 `web/` 内既有文件为准。
- Hero 素材由 higgsfield 生成，规格见 `web/HERO_ASSET_BRIEF.md`；素材未就绪时保留占位。

## 结构

- `initial_plan.md` — 计划本体（Part A-K + 附录），单一事实源
- `CONTEXT.md` — 术语表
- `AGENTS.md` — AI agent 协作规则（事实源裁决顺序、修改与发布流程、红线）
- `webpage-extract-raw.txt` — Meta AI 原计划抽取存档，只读
- `outreach/` — 向导社询价邮件草稿
- `review/` — 对抗审查 findings 存档（只读，不作为事实源）
- `web/` — 计划网页与 hero 素材：`index.html`（对外网页）、`HERO_ASSET_BRIEF.md`（hero 素材规格）、`hero.jpg` / `hero-portrait.jpg` / `hero.mp4` / `hero-day.jpg` / `hero-day-portrait.jpg` / `hero-day.mp4`（已交付素材，截至 2026-08-23）
