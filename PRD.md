# Backlink Doctor — Product Requirements Document (PRD)

**Version**: 2.0  
**Date**: 2026-05-15  
**Status**: Draft for Review  
**Author**: AI Product Team  
**Target**: AI-powered backlink health platform for SEO professionals, agencies, and SaaS founders

---

## 0. 结论先行

### 0.1 要不要做
**做。** `backlink monitor tool` 方向有 3 个 2025-2026 年新站（BacklinkVigil、Linkoxy、Backmetric）已进入 SERP 前 10，证明市场可容纳新玩家。但纯监控功能已红海，必须以 **AI 诊断 + 主动恢复** 作为核心差异化切入。

### 0.2 为什么做
- 现有工具只会告警"链丢了"，不会诊断"为什么丢"和"怎么恢复"
- SEO 从业者每周花费 5-10 小时手动诊断丢链、写 outreach 邮件
- 没有工具系统追踪"恢复成功率"
- AI 技术成熟度足够支撑自动化诊断和邮件生成

### 0.3 一句话定位
**Backlink Doctor 是第一个 AI 驱动的外链健康平台——诊断丢链原因、按业务价值排序恢复优先级、生成个性化 outreach 邮件，把被动监控变为主动恢复。**

### 0.4 首版做什么
- 外链监控引擎（新/丢/变检测）
- AI 丢链诊断（5 大原因分类 + 恢复可能性评估）
- 恢复优先级排序（综合评分算法）
- AI 邮件生成 + 发送追踪
- 外链健康评分（0-100）
- 免费健康检查工具（获客漏斗）

### 0.5 明确不做什么（NOT-DO）
- ❌ 外链建设/购买（不是 link building tool）
- ❌ 关键词排名追踪（Ahrefs/Semrush 已做透）
- ❌ 网站技术审计（偏离核心定位）
- ❌ 自建外链索引数据库（成本不可控，用第三方 API）
- ❌ 多语言支持（首版只英文）
- ❌ 移动端原生 App（先做 Web）

---

## 1. 市场概述

### 1.1 目标关键词

| 关键词 | 角色 | 趋势判定 | 备注 |
|---|---|---|---|
| `backlink monitor tool` | 主词 | watch（依附于 backlink checker 3.18x） | 无独立 strong 数据 |
| `backlink checker` | 上位词 | 3.18x / watch | 流量大但竞争激烈 |
| `lost backlink recovery` | 长尾机会词 | 未验证 | BacklinkRecovery.com 已验证需求存在 |
| `AI backlink monitor` | 差异化词 | 新词 | BacklinkScan 刚出现，窗口期 |
| `backlink health check` | 品牌词机会 | 新词 | 无人占位 |

### 1.2 搜索量 / CPC / KD（待验证）

> ⚠️ 以下数据基于 SERP 观察和竞品反推，非一手关键词工具数据。上线前需用 Ahrefs/Semrush 验证。

| 关键词 | 预估月搜索量 | 预估 CPC | 预估 KD | 数据来源 |
|---|---|---|---|---|
| `backlink monitor tool` | 1,000-3,000 | $3-5 | 35-45 | 竞品反推 |
| `backlink checker` | 50,000+ | $4-6 | 60+ | 行业常识 |
| `lost backlink recovery` | 500-1,000 | $5-8 | 25-35 | BacklinkRecovery.com 存在证明 |
| `free backlink checker` | 10,000+ | $2-3 | 50+ | 行业常识 |

### 1.3 趋势判断
- **长期需求**：外链监控是 SEO 基础设施，需求稳定
- **AI 叠加趋势**：2025-2026 年 "AI + SEO tool" 是新窗口，BacklinkScan、Backlinker.ai 等已入场
- **窗口期判断**：`AI backlink monitor` 方向竞争尚不激烈，有 6-12 个月先发优势窗口

### 1.4 机会判断
- ✅ SERP 有独立小站存活（BacklinkVigil、Linkoxy、Backmetric）
- ✅ 用户有明确付费场景（现有工具均收费 $14-29/月起）
- ✅ 首版可低成本实现（API 组合型产品，无需自建索引）
- ⚠️ 主词无 strong 趋势红利，需靠差异化功能 + 内容 SEO 获客

**结论**：3-4 个强信号，继续做 PRD。

---

## 2. SERP 与竞品分析

### 2.1 SERP 实扫（2026-05-15）

**目标词**：`backlink monitor tool`

**Top 10 类型分布**：
- 工具页：6 个（Linkody、BacklinkVigil、Linkoxy、Seobility、Backmetric、Backlinks360）
- 内容页：3 个（Backlinko、SeoProfy、TheCMO）
- 巨头工具：1 个（Ahrefs）

**大站 vs 小站**：
- 大站/成熟品牌：4 个（Ahrefs、Backlinko、Linkody、Seobility）
- 独立小站（<2年）：4 个（BacklinkVigil 2025-07、Linkoxy 2026-03、Backmetric 2025-10、Backlinks360 2025-01）

**搜索意图判断**：工具型 —— 用户想找一个能监控外链状态的工具

**产品方向**：AI 驱动的诊断+恢复工具（不是纯监控）

### 2.2 Top 3 竞品深度分析

#### 竞品 A：BacklinkVigil（backlinkvigil.com）

| 维度 | 详情 |
|---|---|
| 域名年龄 | 2025-07（<1年） |
| 定价 | $20/月起，免费版有限 |
| 核心功能 | 每日监控、丢链检测、干净告警 |
| 收入规模 | $1.1K/年，20 用户（GetLatka 数据） |
| 优势 | 专注监控、界面简洁、Capterra/G2 收录 |
| 弱点 | 无 AI 诊断、无恢复辅助、规模极小 |
| 用户评价 | "准确但功能基础" |

#### 竞品 B：Linkoxy（linkoxy.com）

| 维度 | 详情 |
|---|---|
| 域名年龄 | 2026-03（2个月） |
| 定价 | 免费起步，无信用卡 |
| 核心功能 | 免费外链追踪、锚文本监控、状态检测 |
| 优势 | 免费版 generous、无门槛注册 |
| 弱点 | 功能极浅、无 AI、刚上线未验证 |
| 威胁等级 | 中 —— 免费策略可能拉低市场价格预期 |

#### 竞品 C：BacklinkScan（backlinkscan.com）

| 维度 | 详情 |
|---|---|
| 定位 | AI-powered backlink checker |
| 核心功能 | 每日监控、AI 毒性检测、自动 disavow、Search Console 集成 |
| 优势 | 已有 AI 功能、G2/Capterra 收录、有免费工具 |
| 弱点 | 还是"检查器"思维，无恢复闭环、无诊断深度 |
| 威胁等级 | 高 —— 最接近的 AI 竞品，但方向不同 |

### 2.3 三层竞品分级

| 层级 | 竞品 | 关系 | 策略 |
|---|---|---|---|
| **Tier 1 直接竞品** | BacklinkVigil、Linkoxy、Backmetric、Linkwatcher | 同品类监控工具 | 功能碾压 + AI 差异化 |
| **Tier 2 相邻方案** | BacklinkScan、Ahrefs、Semrush、Linkody | 功能重叠的大工具/AI工具 | 单点打穿，不做大而全 |
| **Tier 3 现状/不做** | Excel 手动追踪、Google Sheets、不监控 | 最大竞品群 | 把手动用户变成自动化用户 |

**重点**：很多潜在用户现在用 Excel 或干脆不监控——这是最大的市场。

### 2.4 用户痛点证据

| 来源 | 痛点 | 证据 |
|---|---|---|
| BacklinkVigil 评价 | "准确但功能基础" | Capterra/G2 评论 |
| BacklinkRecovery.com | "手动丢链恢复耗时" | 产品定位语 |
| SEO 社区（推断） | 每周 5-10 小时手动诊断 | 行业常识，待 Reddit 验证 |
| BacklinkScan 定位 | " clarity over complexity" | 说明现有工具太复杂或太简单 |

---

## 3. 目标用户

### 3.1 用户细分

| 用户 | 画像 | 痛点 | 触发场景 | 付费意愿 | 出现渠道 |
|---|---|---|---|---|---|
| **SEO Agency 老板** | 管理 5-50 个客户外链 | 客户问"链接怎么了"答不上来；手动报告耗时 | 月度客户汇报前 | 高（$79-199/月） | LinkedIn、SEO 会议 |
| **In-house SEO** | SaaS/E-com 公司 | 外链丢了不知道，排名掉了才反应 | 排名下降排查时 | 中（$29-79/月） | SEO 社区、Twitter |
| **Freelance SEO** | 个人服务 3-10 客户 | 没有工具预算，用 Excel 追踪 | 客户增加时 | 低-中（$29/月） | Twitter、Reddit r/SEO |
| **SaaS 创始人** | 自己做 SEO | 不懂技术，需要"告诉我做什么" | 融资后想增长 | 中（$29/月） | Indie Hackers、Product Hunt |

### 3.2 主力用户

**SEO Agency 老板（5-20 个客户）**

- **Why 最痛**：客户付费买链接，丢了 = 钱白花了 = 客户投诉
- **Why 愿付**：一个客户月费 $500-2000，工具费 $79/月 = 成本可忽略
- **Why 易触达**：LinkedIn 精准定位、SEO 社群活跃、口碑传播强
- **触发事件**：丢了一个高价链接被客户发现

### 3.3 用户触发场景

```
场景 A：Agency 日常
"早上打开邮箱，客户问：'我们上个月买的那个 DR60 的链接怎么没了？'
→ 慌张去查 Ahrefs → 发现确实丢了 → 不知道怎么丢的 → 手动写邮件给站长"

场景 B：In-house SEO
"周会汇报，老板问外链建设进展 → 打开 Excel → 数据是上周的 → 不知道这周丢了几个"

场景 C：Freelance SEO
"同时管 8 个客户的外链 → 每个客户 20-50 个链接 → 每周花 6 小时逐个检查状态"
```

---

## 4. 产品定位

### 4.1 竞争替代分析

| 替代方案 | 用户现在怎么做 | 痛点 |
|---|---|---|
| Ahrefs/Semrush | 看 New/Lost links 报表 | 只告诉"丢了"，不告诉"为什么"和"怎么办" |
| BacklinkVigil | 用基础监控工具 | 只告警，无诊断，无恢复辅助 |
| Excel/Google Sheets | 手动记录链接列表 | 耗时、不及时、无法诊断 |
| 不监控 | 等排名掉了才发现 | 被动、损失已造成 |
| 雇 VA | 让虚拟助理手动检查 | 成本高、质量不稳定 |

### 4.2 独有属性 → 价值映射

| 属性 | 解决什么问题 | 用户价值 |
|---|---|---|
| AI 诊断丢链原因 | 不用手动猜为什么丢了 | 节省 2-3 小时/周 |
| 恢复可能性评分 | 知道该优先追哪个 | 提高恢复成功率 |
| AI 生成 outreach 邮件 | 不用写邮件 | 节省 1-2 小时/周 |
| 恢复成功追踪 | 知道努力有没有结果 | 可量化的 ROI |
| 健康评分趋势 | 提前预警问题 | 从被动变主动 |

### 4.3 定位语句

```
FOR SEO agencies and professionals
WHO lose backlinks and don't know why or how to recover them
Backlink Doctor IS AN AI-powered backlink health platform
THAT diagnoses why you lost links, prioritizes recovery by value, and generates personalized outreach
UNLIKE passive monitoring tools like BacklinkVigil or complex suites like Ahrefs
Backlink Doctor turns backlink monitoring from passive alerting into active recovery
```

### 4.4 消息层级

| 层级 | 内容 |
|---|---|
| **Headline** | Stop Losing Backlinks. Start Recovering Them. |
| **Subhead** | AI diagnoses why your links disappear, ranks them by recovery value, and writes the outreach email. |
| **Benefit 1** | Know WHY — AI analyzes every lost link and tells you exactly what happened |
| **Benefit 2** | Recover FAST — Smart priority scoring tells you which links to chase first |
| **Benefit 3** | Close the Loop — AI writes personalized recovery emails and tracks your success rate |
| **Proof** | "We recovered 12 high-value links in our first month" — SEO Agency Owner |

### 4.5 差异化优先级

1. **更聚焦的单点定位**：不做全能 SEO 工具，只做"外链健康+恢复"
2. **更清楚的场景切入**：从"丢链后的慌乱"切入，不是"日常监控"
3. **更低摩擦的免费使用**：免费健康检查无需注册，先体验价值
4. **更强的 AI 闭环**：诊断 → 排序 → 邮件 → 追踪，全流程自动化
5. **更合适的定价**：比 Ahrefs 便宜 10 倍，比 BacklinkVigil 多 5 倍价值

### 4.6 禁词清单

| 不要用 | 原因 |
|---|---|
| "Best backlink tool" | 无法证明，且大站已占位 |
| "#1" / "Top rated" | 无依据，广告法风险 |
| "Guaranteed recovery" | 无法保证，引发投诉 |
| "Replace Ahrefs" | 不现实，定位不同 |
| "Fully automated" | 过度承诺，需要人工审核 |

---

## 5. 功能规划

### 5.1 核心功能（P0）

| 模块 | 功能 | 说明 |
|---|---|---|
| **监控引擎** | 外链状态监控 | 每日爬取 referring pages，检测 404/301/nofollow/锚文本变化 |
| | 变化事件流 | "Today's Changes"  feed，按时间线展示所有变化 |
| **AI 诊断** | 丢链原因分类 | AI 识别：页面删除、内容更新、站点重构、故意移除、域名过期 |
| | 恢复可能性评分 | 0-100%，基于站点活跃度、可联系性、历史行为 |
| | SEO 影响评估 | 估算丢链的权重/流量损失 |
| **恢复系统** | 优先级排序 | 综合算法：DR×0.25 + 流量×0.2 + 相关性×0.2 + 恢复可能×0.2 + 时效×0.15 |
| | 智能列表 | "Quick Wins"、"High Value"、"At Risk" 自动分类 |
| **AI 邮件** | 联系人发现 | 集成 Hunter.io / Apollo 找编辑邮箱 |
| | 邮件生成 | 基于诊断结果生成个性化 outreach 邮件 |
| | 发送追踪 | 标记发送状态，7 天后自动复查链接是否恢复 |
| **健康评分** | 综合评分 | 0-100 分，5 维度加权 |
| | 趋势图表 | 90 天趋势 + AI 自然语言总结 |
| | 预测预警 | "按当前趋势，30 天内可能再丢 X 个高价值链接" |

### 5.2 Landing Page & SEO（P0-P1）

| 页面 | 目标 | 优先级 |
|---|---|---|
| `/` | 首页：转化 + 工具入口 | P0 |
| `/free-health-check` | 免费健康检查工具 | P0 |
| `/features` | 功能详情 | P1 |
| `/pricing` | 定价页 | P0 |
| `/blog` | 内容 SEO | P1 |
| `/blog/how-to-recover-lost-backlinks` | 信息词引流 | P1 |
| `/alternative/backlinkvigil` | 截流竞品词 | P2 |
| `/alternative/ahrefs` | 截流大竞品 | P2 |
| `/use-cases/agencies` | Agency 场景页 | P1 |
| `/use-cases/saas` | SaaS 场景页 | P1 |

### 5.3 付费与转化（P0-P1）

| 功能 | 说明 | 优先级 |
|---|---|---|
| 免费版限制 | 50 外链、每周检查、3 次 AI 诊断/月 | P0 |
| 升级提示 | 免费版用完配额时提示升级 | P0 |
| 支付集成 | Stripe 订阅 | P0 |
| Pro 解锁 | 无限 AI 诊断、每日检查、邮件发送 | P0 |
| Team 功能 | 多用户、客户管理 | P1 |
| Agency 白标 | 白标报告、自定义域名 | P1 |

### 5.4 合规与基础设施（P0-P1）

| 功能 | 说明 | 优先级 |
|---|---|---|
| 用户认证 | Google / GitHub / Email | P0 |
| Privacy Policy | GDPR/CCPA 合规 | P0 |
| Terms of Service | 标准条款 | P0 |
| 埋点分析 | 见第 10 章转化漏斗 | P0 |
| 错误监控 | Sentry | P1 |
| 邮件通知 | 每日/每周摘要邮件 | P1 |

### 5.5 NOT-DO（明确不做）

| 功能 | 不做原因 |
|---|---|
| 自建外链索引库 | 成本不可控，用 DataForSEO/Ahrefs API |
| 关键词排名追踪 | 偏离定位，Ahrefs 已做透 |
| 网站技术审计 | 偏离定位 |
| 外链建设/购买市场 | 法律风险、运营重 |
| 多语言界面 | 首版聚焦英文市场 |
| 移动端原生 App | Web 优先，PWA 可选 |
| 实时聊天客服 | 成本过高，邮件+文档优先 |
|| 自定义 AI 模型训练 | 用 GPT-4o API，不自训 |

---

### 5.6 MVP 范围说明

PRD 第 5.1 节所列 P0 功能为**完整版产品范围**。首版 MVP 基于 Cloudflare 全家桶技术栈，从 P0 中进一步收缩为 7 个核心功能，确保用户能完整体验"丢链→诊断→恢复"闭环。

**MVP 保留**：免费健康检查、用户系统、域名管理、监控引擎（简化版）、AI 诊断、恢复优先级排序、AI 邮件生成、健康评分（简化版）、Stripe 支付、邮件通知

**MVP 砍掉**：变化事件流、SEO 影响评估、智能列表分类、Contact discovery、邮件发送追踪、健康评分趋势图、预测预警、多用户/团队、白标报告、API 接入

详细功能清单、技术栈、数据库 schema、验收标准、开发时间线见配套文档：
📄 `/root/backlink-doctor-mvp-scope.md`

---

## 6. 页面信息架构

### 6.1 首页结构

```
1. HERO
   - Headline: "Stop Losing Backlinks. Start Recovering Them."
   - Subhead: "AI diagnoses why your links disappear, ranks them by recovery value, and writes the outreach email."
   - 首屏工具入口：输入域名 → 免费健康检查
   - CTA: "Check My Backlinks Free" / "See How It Works"

2. PROBLEM / PAIN POINT
   - "You get an alert: 'Link lost.' Now what?"
   - 3 个痛点卡片：不知道原因 / 不知道优先追哪个 / 写邮件耗时

3. HOW IT WORKS（三步流程）
   - Step 1: Monitor — 我们监控你的外链 24/7
   - Step 2: Diagnose — AI 告诉你为什么丢了
   - Step 3: Recover — 智能排序 + AI 邮件 + 追踪结果

4. DEMO / 效果展示
   - 真实诊断案例截图（脱敏）
   - Before/After：从"手动 Excel"到"自动恢复"

5. USE CASES（3 个场景）
   - For Agencies: 客户外链保护
   - For SaaS: 产品页外链监控
   - For Freelancers: 多客户管理

6. FEATURES（功能亮点）
   - AI Diagnosis / Smart Priority / Auto Outreach / Health Score / White-label Reports

7. PRICING
   - Free / Pro $29 / Team $79 / Agency $199
   - 每个 plan 的核心限制对比

8. FAQ（覆盖 Top 8 顾虑）
   - 免费版限制？
   - 怎么发现我的外链？
   - 恢复成功率多少？
   - 支持哪些邮箱？
   - 数据安全？
   - 能导出数据吗？
   - 怎么取消订阅？
   - 有 API 吗？

9. FOOTER CTA
   - "Ready to stop losing links?"
   - 输入域名 → 免费检查
```

### 6.2 转化检查清单

- [x] Hero 3 秒内说明价值
- [x] 首屏可直接使用工具（输入域名）
- [x] CTA 是"动词 + 结果"（Check My Backlinks Free）
- [x] 有 How It Works
- [x] 有真实样例/结果展示
- [x] FAQ 覆盖价格、质量、隐私、限制
- [x] 定价区先展示价值再展示价格

### 6.3 SEO 页面矩阵

| 页面 | 目标关键词 | 搜索意图 | 目的 | 优先级 |
|---|---|---|---|---|
| `/` | `backlink monitor tool`, `AI backlink monitor` | 工具型 | 转化 | P0 |
| `/free-health-check` | `free backlink health check` | 工具型 | 获客 | P0 |
| `/features` | `backlink monitor features` | 信息型 | 教育 | P1 |
| `/pricing` | `backlink monitor pricing` | 对比型 | 转化 | P0 |
| `/blog/how-to-recover-lost-backlinks` | `how to recover lost backlinks` | 信息型 | 引流 | P1 |
| `/blog/why-did-my-backlink-disappear` | `why did my backlink disappear` | 信息型 | 引流 | P1 |
| `/use-cases/agencies` | `backlink monitor for agencies` | 工具型 | 场景转化 | P1 |
| `/alternative/backlinkvigil` | `backlinkvigil alternative` | 对比型 | 截流 | P2 |
| `/alternative/linkody` | `linkody alternative` | 对比型 | 截流 | P2 |
| `/tools/free-backlink-status-checker` | `free backlink checker` | 工具型 | 获客 | P1 |
| `/tools/toxic-link-scanner` | `toxic backlink checker` | 工具型 | 获客 | P1 |

---

## 7. 定价设计

### 7.1 竞品价格锚点

| 竞品 | 起步价 | 免费版 | 上限 |
|---|---|---|---|
| Linkody | ~$14/月 | 30 天试用 | $140/月 |
| BacklinkVigil | $20/月 | 有限免费 | 未知 |
| Linkoxy | 免费 | 无限（功能受限） | 未知 |
| Backmetric | $14.99/月 | 14 天试用 | 未知 |
| BacklinkRecovery | $13/月 | 无 | 未知 |
| Linkwatcher | 免费 | 25 链接 | $79/月 |

### 7.2 定价方案

| 功能 | Free | Pro ($29/月) | Team ($79/月) | Agency ($199/月) |
|---|---|---|---|---|
| 监控外链数 | 50 | 500 | 2,000 | 10,000 |
| 监控域名数 | 1 | 3 | 10 | 无限 |
| 检查频率 | 每周 | 每日 | 每日 | 每日 |
| AI 诊断 | 3 次/月 | 无限 | 无限 | 无限 |
| 恢复邮件 | 5 封/月 | 无限 | 无限 | 无限 |
| 健康评分历史 | 30 天 | 1 年 | 2 年 | 无限 |
| 白标报告 | ❌ | ❌ | ✅ | ✅ |
| 团队人数 | 1 | 1 | 5 | 无限 |
| API 接入 | ❌ | ❌ | ✅ | ✅ |
| 优先支持 | ❌ | 邮件 | 邮件+聊天 | 专属 |

### 7.3 免费版策略

**免费版是获客引擎，不是试用**：
- 50 外链永久免费监控（足够小网站使用）
- 每周检查（付费每日）
- 3 次 AI 诊断/月（体验价值，用完想看更多→付费）
- 5 封恢复邮件/月（体验闭环，用完→付费）

**升级触发点**：
- AI 诊断次数用完时 → "查看完整诊断需升级"
- 外链数超 50 → "监控更多外链需升级"
- 邮件发送完 → "继续发送恢复邮件需升级"

### 7.4 成本验算（1000 付费用户 — 完整版）

> 💡 此为完整版产品成本估算（基于第 8.3 节技术栈）。MVP 版基于 Cloudflare 全家桶，成本大幅降低，详见配套文档 `/root/backlink-doctor-mvp-scope.md` 第 8 节。

| 成本项 | 月成本 | 说明 |
|---|---|---|
| OpenAI GPT-4o | $500 | 50K 诊断调用 |
| DataForSEO API | $300 | 1M backlink 查询 |
| 住宅代理 | $400 | 5M 爬取请求 |
| Hunter.io | $200 | 10K 邮箱查找 |
| 基础设施 | $300 | Vercel + Railway + DB |
| **总成本** | **$1,700** | |
| **收入（ARPU $45）** | **$45,000** | |
| **毛利率** | **96%** | |

---

## 8. 域名与技术栈

### 8.1 域名候选

| 域名 | 状态 | 后缀 | 评价 |
|---|---|---|---|
| backlinkdoctor.ai | 待查 | .ai | 品牌名直接，定位清晰 |
| linkguard.ai | 待查 | .ai | 短、好记、保护感强 |
| linkhealth.ai | 待查 | .ai | 健康平台定位 |
| reclaimlink.ai | 待查 | .ai | 恢复导向 |
| linkrevive.ai | 待查 | .ai | 复活感 |
| backlinkmd.com | 待查 | .com | MD=医生，谐音梗 |
| getlinkguard.com | 待查 | .com | 经典前缀型 |
| linkguardian.com | 待查 | .com | 守护感，可能已注册 |

### 8.2 推荐 Top 3

1. **linkguard.ai** — 短（9 字母）、好拼、有保护感、.ai 符合 AI 产品定位
2. **backlinkdoctor.ai** — 定位最直接，但较长（16 字母）
3. **linkhealth.ai** — 健康平台概念更广，未来可扩展

### 8.3 技术栈建议（完整版）

| 层级 | 技术 | 理由 |
|---|---|---|
| 前端 | Next.js 14 + Tailwind + shadcn/ui | SEO 友好、速度快、组件丰富 |
| 图表 | Tremor / Recharts | 数据可视化 |
| API | Next.js API Routes + tRPC | 全栈统一、类型安全 |
| 认证 | NextAuth.js | Google/GitHub/Email |
| 核心服务 | Node.js/Express | 业务逻辑、调度 |
| 爬虫 | Python + Playwright | 防 block、JS 渲染 |
| AI | OpenAI GPT-4o + Claude | 诊断 + 邮件生成 |
| 数据库 | PostgreSQL | 关系数据 |
| 缓存/队列 | Redis + BullMQ | 任务队列、缓存 |
| 对象存储 | Cloudflare R2 | 页面快照、低成本 |
| 分析 | ClickHouse | 时序数据、埋点 |
| 外部 API | DataForSEO / Ahrefs | 外链数据源 |
| 邮箱查找 | Hunter.io / Apollo | 联系人发现 |
| 邮件发送 | Gmail API / SendGrid | 多渠道备用 |

> ⚠️ **MVP 技术栈已切换至 Cloudflare 全家桶**，详见配套文档 `/root/backlink-doctor-mvp-scope.md` 第 3 节。完整版技术栈保留作为规模扩展参考。

---

## 9. GTM 策略

### 9.1 发布阶段

| 阶段 | 时间 | 目标 | 关键动作 |
|---|---|---|---|
| **Alpha** | Month 1-2 | 验证核心链路 | 10 个 beta 用户（个人网络） |
| **Beta** | Month 2-3 | 收集反馈迭代 | Product Hunt "Coming Soon"、waitlist |
| **Public Launch** | Month 3 | 首次公开获客 | Product Hunt 正式发布、Hacker News、Twitter |
| **Growth** | Month 4-6 | 内容 SEO 驱动 | 每周 1 篇内容、免费工具矩阵 |
| **Scale** | Month 7-12 | 渠道扩展 | AppSumo、affiliate、API 生态 |

### 9.2 首周动作

**Product Hunt 发布日**：
- 提前 2 周准备：产品截图、演示视频、创始人故事
- 发布当天：创始人 + 团队全员在社交媒体同步
- 目标：500+ upvotes、Top 5 Product of the Day

**同步渠道**：
- Hacker News Show HN
- Reddit r/SEO、r/SideProject
- Twitter/X 线程（创始人故事 + 产品演示）
- Indie Hackers 发布

### 9.3 内容 SEO 管线

| 内容类型 | 频率 | 目标关键词 | 目的 |
|---|---|---|---|
| 工具落地页 | 1 个/周 | `free backlink checker`, `backlink health check` | 直接获客 |
| 诊断指南 | 2 篇/月 | `why did my backlink disappear`, `how to recover lost backlinks` | 信息引流 |
| 竞品对比 | 1 篇/月 | `backlinkvigil vs linkody`, `best AI backlink tool` | 截流 |
| 案例研究 | 1 篇/月 | `how agency recovered 50 links` | 信任建立 |
| 行业报告 | 1 篇/季度 | `state of backlink health 2026` | 品牌权威 |

---

## 10. 转化漏斗与埋点

### 10.1 核心转化漏斗

```
访问首页 ──→ 开始免费检查 ──→ 查看结果 ──→ 注册 ──→ 添加域名 ──→ 收到第一个告警 ──→ 查看诊断 ──→ 升级付费
  │              │              │          │          │              │            │
  ▼              ▼              ▼          ▼          ▼              ▼            ▼
page_view   tool_start    tool_success  signup   domain_add    alert_open   diagnosis_view  upgrade_click
                                                                                          │
                                                                                          ▼
                                                                                    checkout_start
                                                                                          │
                                                                                          ▼
                                                                                    payment_success
```

### 10.2 埋点事件清单

| 事件 | 触发时机 | 属性 | 优先级 |
|---|---|---|---|
| `page_view` | 每次页面加载 | page_path, referrer, utm | P0 |
| `tool_start` | 点击免费检查 | tool_type, input_domain | P0 |
| `tool_success` | 检查完成 | result_score, issue_count | P0 |
| `tool_error` | 检查失败 | error_type | P1 |
| `cta_click` | 点击任何 CTA | cta_location, cta_text | P0 |
| `signup_start` | 点击注册 | method (google/github/email) | P0 |
| `signup_success` | 注册完成 | method | P0 |
| `domain_add` | 添加监控域名 | domain_count | P0 |
| `alert_open` | 打开告警邮件 | alert_type, alert_count | P1 |
| `diagnosis_view` | 查看 AI 诊断 | diagnosis_type, confidence | P0 |
| `email_generate` | 生成恢复邮件 | template_type | P1 |
| `email_send` | 发送邮件 | send_method | P1 |
| `upgrade_click` | 点击升级 | from_feature, plan_target | P0 |
| `checkout_start` | 进入支付 | plan_selected | P0 |
| `payment_success` | 支付完成 | plan, amount, coupon | P0 |
| `payment_fail` | 支付失败 | error_code | P1 |

### 10.3 关键指标看板

| 指标 | 计算公式 | M3 目标 | M6 目标 | M12 目标 |
|---|---|---|---|---|
| 首页→工具启动率 | tool_start / page_view | 30% | 40% | 45% |
| 工具→注册率 | signup / tool_success | 20% | 25% | 30% |
| 注册→活跃率 | MAU / total_signups | 50% | 60% | 70% |
| 免费→付费转化率 | paid / total_users | 3% | 5% | 8% |
| 付费用户月流失率 | churn / paid_users | <10% | <8% | <5% |
| ARPU | MRR / paid_users | $35 | $40 | $45 |
| LTV | ARPU × 平均留存月 | $210 | $320 | $450 |
| CAC | 营销成本 / 新付费用户 | < $50 | < $40 | < $30 |
| LTV/CAC | LTV / CAC | > 3 | > 4 | > 5 |

---

## 11. 风险评估

### 11.1 SEO 风险

| 风险 | 可能性 | 影响 | 缓解措施 |
|---|---|---|---|
| 主词 `backlink monitor tool` 无 strong 趋势 | 高 | 中 | 靠长尾词矩阵 + 内容 SEO 补量 |
| 新站 sandbox 期排名慢 | 高 | 中 | 免费工具获客 + Product Hunt 冷启动 |
| 竞品模仿 AI 功能 | 高 | 中 | 速度优先，6 个月内建立品牌认知 |
| Google 算法打击 AI 内容站 | 中 | 高 | 工具型页面为主，非纯内容站 |

### 11.2 技术风险

| 风险 | 可能性 | 影响 | 缓解措施 |
|---|---|---|---|
| 爬虫被目标站 block | 高 | 中 | 住宅代理轮换、降频、缓存 fallback |
| AI 诊断幻觉/不准确 | 中 | 高 | 置信度分数、结构化 prompt、用户反馈迭代 |
| 数据成本超预算 | 中 | 高 | 定价与 crawl 量挂钩、智能缓存 |
| 第三方 API 涨价/断供 | 低 | 高 | 多供应商备份（DataForSEO + Ahrefs） |

### 11.3 成本风险

| 风险 | 可能性 | 影响 | 缓解措施 |
|---|---|---|---|
| 免费用户过多导致亏损 | 中 | 中 | 免费版限制严格、AI 诊断次数封顶 |
| 付费转化低于预期 | 中 | 高 | A/B 测试定价、调整免费版限制 |
| 服务器成本随用户增长失控 | 低 | 中 | 按量定价、缓存策略、渐进扩容 |

### 11.4 合规风险

| 风险 | 可能性 | 影响 | 缓解措施 |
|---|---|---|---|
| GDPR 数据合规 | 中 | 中 | Privacy Policy、数据删除功能、EU 服务器 |
| 爬取行为法律争议 | 低 | 高 | 尊重 robots.txt、合理频率、公开透明 |
| 邮件发送被标记垃圾 | 中 | 中 | SPF/DKIM 配置、发送频率控制、退订机制 |

### 11.5 商业化风险

| 风险 | 可能性 | 影响 | 缓解措施 |
|---|---|---|---|
| 用户认为 AI 诊断不够准 | 中 | 高 | 置信度展示、人工审核入口、持续迭代 |
| Agency 客户要求定制化 | 中 | 中 | Agency plan 提供白标 + API |
| 大工具（Ahrefs）推出类似功能 | 中 | 高 | 单点打穿、速度、价格优势 |

---

## 12. 交接摘要

### 12.1 给文案

```
产品名：Backlink Doctor
定位语句：第一个 AI 驱动的外链健康平台——诊断丢链原因、按业务价值排序恢复优先级、生成个性化 outreach 邮件
Headline：Stop Losing Backlinks. Start Recovering Them.
Subhead：AI diagnoses why your links disappear, ranks them by recovery value, and writes the outreach email.
核心 Benefits：
1. Know WHY — AI 分析每个丢链并告诉你确切原因
2. Recover FAST — 智能优先级告诉你先追哪个
3. Close the Loop — AI 写个性化恢复邮件并追踪成功率

FAQ 必须覆盖：
- 免费版能监控多少外链？（50 个）
- 怎么发现我的外链？（DataForSEO API + 用户导入）
- 恢复成功率多少？（取决于原因，Quick Wins 类 30-50%）
- 支持哪些邮箱发送？（Gmail、Outlook、SMTP）
- 数据安全吗？（加密存储、不分享数据）
- 能导出数据吗？（Pro 以上支持 CSV/PDF 导出）
- 怎么取消？（随时取消，无合约）
- 有 API 吗？（Team 以上支持）

不能把产品说成：
- "最好的外链工具"（无法证明）
- "保证恢复"（无法保证）
- "替代 Ahrefs"（定位不同）
- "全自动"（需要人工审核和发送）

CTA 格式：动词 + 结果
- ✅ Check My Backlinks Free
- ✅ Start Recovering Lost Links
- ✅ See My Link Health Score
- ❌ Submit
- ❌ Click Here
```

### 12.2 给设计

```
首页结构（从上到下）：
1. Hero：深色背景，左侧文字+CTA，右侧产品界面截图/Demo
2. Problem：3 张痛点卡片，配图标
3. How It Works：3 步横向流程图，带箭头连接
4. Demo：真实诊断面板截图（脱敏数据）
5. Use Cases：3 个场景卡片（Agency/SaaS/Freelancer）
6. Features：6 个功能图标+简短说明
7. Pricing：4 列对比表，Free 列突出，Pro 列高亮推荐
8. FAQ：手风琴展开式
9. Footer CTA：大号输入框+按钮

首屏重点：
- 域名输入框必须显眼（这是免费工具入口）
- 输入框占位符："Enter your domain (e.g., example.com)"
- 按钮："Check My Backlinks Free →"

核心交互：
- 诊断面板：左侧丢链列表，右侧 AI 诊断详情
- 邮件编辑器：类似 Gmail 的简洁编辑界面
- 健康评分：圆形进度条 + 趋势折线图

视觉参考：
- 主色：深蓝 (#1e3a5f) + 青色强调 (#00d4aa)
- 风格：专业、可信、科技感（不是花哨）
- 字体：Inter / Geist

移动端要求：
- 诊断面板改为上下布局（列表在上，详情在下）
- 输入框全宽
- CTA 按钮全宽

不需要设计：
- 复杂的 3D 图形
- 插画风格（用图标+截图即可）
- 深色/浅色主题切换（先做深色）
```

### 12.3 给开发

```
技术栈（完整版）：
- 前端：Next.js 14 App Router + Tailwind + shadcn/ui
- 后端：Node.js/Express + tRPC
- 数据库：PostgreSQL + Redis
- 爬虫：Python + Playwright（独立 VPS 部署，通过 Queues 与主服务通信）
- AI：OpenAI GPT-4o API
- 部署：Vercel (前端) + Railway/Render (后端)
- 存储：Cloudflare R2 (快照)

> ⚠️ **MVP 技术栈已切换至 Cloudflare 全家桶**（Workers + D1 + R2 + Queues），详见 `/root/backlink-doctor-mvp-scope.md` 第 3 节。

P0 功能（MVP）：
1. 用户注册/登录（NextAuth：Google/GitHub/Email）
2. 域名添加 + 外链导入（CSV + DataForSEO API）
3. 外链监控引擎（每日爬取 + 变化检测）
4. AI 诊断（GPT-4o 结构化输出：原因/置信度/恢复可能性）
5. 恢复优先级排序（综合评分算法）
6. AI 邮件生成（基于诊断的个性化邮件）
7. 健康评分（0-100 + 趋势）
8. 免费健康检查工具（无需注册，top 100 链接分析）
9. Stripe 订阅支付
10. 基础邮件通知（每日摘要）

P1 功能（M2-M3）：
1. Gmail API 集成（直接发送）
2. 恢复成功追踪（7 天后自动复查）
3. 团队/多用户支持
4. 白标报告
5. API 接入
6. 更多免费工具（toxic scanner, DR checker）

API 链路：
用户添加域名 → 调用 DataForSEO API 获取外链列表 → 存储到 DB → 
调度爬虫任务 → Playwright 爬取每个 referring page → 对比历史快照 → 
检测变化 → 触发 AI 诊断 → 生成事件 → 通知用户 → 用户查看诊断 → 
点击生成邮件 → 调用 GPT-4o → 用户发送/复制 → 标记恢复中 → 
7 天后复查 → 更新状态

数据结构（核心表）：
- users, teams, team_members
- domains (监控的域名)
- backlinks (外链记录)
- backlink_events (变化事件)
- recovery_attempts (恢复尝试)
- snapshots (页面快照 S3 key)

NOT-DO：
- 不自建外链索引库
- 不做关键词排名追踪
- 不做网站技术审计
- 不训练自有 AI 模型
- 首版不做多语言

验收标准：
- [ ] 添加域名后 24 小时内完成首次全量扫描
- [ ] 丢链检测准确率 > 95%
- [ ] AI 诊断 API 响应 < 3 秒
- [ ] 邮件生成质量通过人工抽检（80% 可直接发送）
- [ ] 免费健康检查完成时间 < 30 秒
- [ ] 支付流程端到端测试通过
```

---

## 13. 质量检查清单

PRD 完成前自查：

- [x] 有明确关键词
- [x] 有搜索量/CPC/KD（标注待验证）
- [x] SERP 经过实扫
- [x] 搜索意图判断清楚
- [x] Top 3 竞品写清楚
- [x] 竞品做了三层分级
- [x] 至少拆了 3 个用户场景
- [x] 选定主力用户
- [x] 有结构化定位语句
- [x] 消息层级清楚
- [x] 功能范围分 P0/P1/NOT-DO
- [x] 首页 IA 可以直接给设计使用
- [x] SEO 页面矩阵明确
- [x] 定价有竞品锚点和成本意识
- [x] 域名有 Top 3 推荐
- [x] GTM 有首周动作
- [x] 埋点事件明确
- [x] 风险有缓解措施
- [x] 有交接摘要（文案/设计/开发）

---

**End of PRD v2.0**
