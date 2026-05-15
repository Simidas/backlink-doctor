# Backlink Doctor — MVP 范围收缩文档

**版本**: 1.0  
**日期**: 2026-05-15  
**基于**: PRD v2.0（`/root/backlink-doctor-prd-v2.md`）

---

## 1. MVP 核心原则

**最小可用 = 用户能完整体验一次"丢链→诊断→恢复"闭环**

不是功能最少，而是**价值闭环最短**。砍掉任何阻碍闭环的功能，保留所有加速闭环的功能。

---

## 2. MVP 功能清单（6 周上线）

### 2.1 保留功能（MVP 内）

| 模块 | 子功能 | MVP 实现方式 | 为什么保留 |
|------|--------|-------------|-----------|
| **免费获客工具** | 单次健康检查 | 输入域名 → DataForSEO API 拉取前 100 referring pages → 快速扫描 → 生成健康评分 | 获客引擎，无需注册即可体验价值 |
| **用户系统** | 注册/登录 | Cloudflare Access OAuth（Google），自建 JWT 备用 | Workers 原生认证 |
| **域名管理** | 添加域名 + 外链导入 | DataForSEO API 拉取外链列表，存储到 D1 | 核心数据入口 |
| **监控引擎** | 每日检查 | Python Playwright 爬虫跑在 VPS → 结果推送到 Cloudflare Queues → Workers 处理 | Playwright 不能跑 Workers，分离部署 |
| **AI 诊断** | 丢链原因分类 | Workers 调用 GPT-4o 结构化输出：原因（5 类）+ 置信度 + 恢复可能性 | **核心差异化**，必须上 |
| **恢复优先级** | 综合评分排序 | Workers 内计算：DR×0.4 + 流量×0.3 + 恢复可能性×0.3 | 让用户知道先追哪个 |
| **AI 邮件生成** | 个性化 outreach 邮件 | Workers 调用 GPT-4o 生成邮件，用户复制到自有邮箱发送 | 闭环最后一步 |
| **健康评分** | 0-100 分 | 简化版：稳定性 50% / 质量 30% / 增长 20%，无趋势图 | 给用户一个直观数字 |
| **支付** | Stripe 订阅 | Free / Pro $29 两档，无 Team/Agency | 验证付费意愿 |
| **邮件通知** | 丢链告警邮件 | Workers 调用 Resend/SendGrid API 发送纯文本摘要 | 召回用户回产品 |

### 2.2 砍掉的功能（P0 → MVP 后）

| 功能 | 原 P0 | 砍掉原因 | 移到哪个阶段 |
|------|-------|---------|-------------|
| 变化事件流（Today's Changes feed） | P0 | 时间线 UI 开发重，MVP 用列表+筛选替代 | Phase 2 |
| SEO 影响评估（权重/流量损失估算） | P0 | 需要额外数据，MVP 只给丢链数 | Phase 2 |
| 智能列表（Quick Wins / High Value / At Risk） | P0 | 分类规则需迭代，MVP 用排序列表 | Phase 2 |
| Contact discovery（Hunter.io/Apollo） | P0 | 邮箱查找 API 成本高，MVP 用户手动输入 | Phase 2 |
| 邮件发送追踪（7 天自动复查） | P0 | 需要定时任务+复查逻辑，MVP 用户手动标记 | Phase 2 |
| 健康评分趋势图（90 天） | P0 | 需要时序数据存储，MVP 只显示当前分 | Phase 2 |
| 预测预警（"30 天内可能再丢 X 个"） | P0 | 需要历史数据训练，MVP 不做预测 | Phase 3 |
| 多用户/团队 | P1 | 首版只个人用户 | Phase 2 |
| 白标报告 | P1 | Agency 功能，验证个人付费后再做 | Phase 3 |
| API 接入 | P1 | 需要文档+认证+限流，后期再做 | Phase 3 |
| 更多免费工具（toxic scanner, DR checker） | P1 | 分散开发资源，先做好主工具 | Phase 2 |
| 场景页（/use-cases/agencies） | P1 | 内容页可后补，先做核心转化页 | Phase 2 |
| 竞品对比页 | P2 | SEO 截流，非核心功能 | Phase 2 |
| 内容 SEO 博客 | P1 | 重要但非阻塞，可用 Ghost/Notion 先挂 | Phase 2 |

---

## 3. MVP 技术栈最小化

| 层级 | PRD 建议 | MVP 实际使用 | 砍掉/替代 |
|------|---------|-------------|----------|
| 前端 | Next.js 14 + Tailwind + shadcn/ui | ✅ 保留 | — |
| 图表 | Tremor / Recharts | ❌ 砍掉 | 健康评分用 CSS 进度条，无图表 |
| API | Next.js API Routes + tRPC | ✅ Next.js API Routes，tRPC 可选 | tRPC 可后加 |
| 认证 | NextAuth.js | ❌ 改为 Cloudflare Access / OAuth | Workers 环境兼容 |
| 核心服务 | Node.js/Express | ❌ 砍掉 | 全放 Cloudflare Workers，无独立服务 |
| 爬虫 | Python + Playwright | ✅ 保留（独立脚本，跑在服务器） | Playwright 不能跑 Workers，单独部署 |
| AI | GPT-4o + Claude | ❌ 只用 GPT-4o | Claude 冗余 |
| 数据库 | PostgreSQL | ❌ 改为 Cloudflare D1 | SQLite 兼容，Serverless，零运维 |
| 缓存/队列 | Redis + BullMQ | ❌ 改为 Cloudflare Queues | 原生消息队列，替代 BullMQ |
| 对象存储 | Cloudflare R2 | ✅ 保留 | 存页面快照、导出报告 |
| 分析 | ClickHouse | ❌ 砍掉 | D1 存事件，或直接用 Plausible/Cloudflare Analytics |
| 外部 API | DataForSEO + Ahrefs | ❌ 只用 DataForSEO | Ahrefs API 贵，备用即可 |
| 邮箱查找 | Hunter.io / Apollo | ❌ 砍掉 | MVP 用户手动输入联系人 |
| 邮件发送 | Gmail API / SendGrid | ❌ 砍掉 | 用户复制邮件自行发送 |
| 部署 | Vercel + Railway/Render | ❌ 改为 Cloudflare Workers | 前后端同平台，边缘部署 |

**MVP 实际技术栈（Cloudflare 全家桶）**：
- Next.js 14（前端 + API Routes）
- Tailwind + shadcn/ui
- Cloudflare D1（数据库）
- Cloudflare R2（对象存储）
- Cloudflare Queues（任务队列）
- Cloudflare Workers（后端部署）
- Python + Playwright（爬虫，跑在独立服务器/VPS，通过 Queues 推送结果）
- OpenAI GPT-4o API
- DataForSEO API
- Stripe
- Resend（邮件发送）
- Cloudflare Access / OAuth（认证）
- OpenNext Cloudflare adapter（Next.js → Workers）

---

## 4. MVP 数据库 Schema（最小表）

```
users (id, email, name, image, stripe_customer_id, plan, created_at)
domains (id, user_id, domain, dr, backlink_count, health_score, last_checked_at, created_at)
backlinks (id, domain_id, source_url, target_url, anchor_text, dr, traffic_estimate, status, first_seen_at, last_seen_at, lost_at)
backlink_events (id, backlink_id, event_type [lost/recovered/changed], detected_at, ai_diagnosis, confidence, recovery_likelihood)
recovery_emails (id, backlink_id, user_id, generated_content, sent_at, status [draft/sent/resolved])
events (id, user_id, event_name, properties, created_at)  -- 埋点
```

6 张表，D1 SQLite 兼容。无团队/无快照/无历史趋势/无 API key 管理。

> 💡 **索引建议**：`backlinks(domain_id, status)`、`backlink_events(backlink_id, detected_at)`、`events(user_id, created_at)`。`events` 表写入频繁，可考虑异步批量写入或切到 Plausible 做埋点。

---

## 5. MVP 用户流程

```
[访客]
  ↓ 输入域名
[免费健康检查] → DataForSEO 拉 100 条 → 快速扫描 → 健康评分 + 问题列表
  ↓ 想看详细诊断 / 想监控
[注册]（Google 一键）
  ↓ 添加域名
[后台拉取全量外链] → 首次扫描
  ↓ 每日自动检查
[丢链检测] → 触发 AI 诊断 → 生成优先级列表
  ↓ 用户打开面板
[诊断详情] → 查看原因 + 恢复可能性
  ↓ 点击生成邮件
[AI 生成 outreach 邮件] → 用户复制 → 自行发送
  ↓ 标记为"已联系"
[追踪状态]（手动更新：等待中 / 已恢复 / 已放弃）
```

**关键**：从丢链发现到邮件生成，全程在产品内完成。发送动作在站外，但生成在站内。

---

## 6. MVP 验收标准

| 验收项 | 标准 | 验证方式 |
|--------|------|---------|
| 免费检查完成时间 | < 30 秒 | 手动测试 10 个域名取平均 |
| 丢链检测准确率 | > 90%（MVP 放宽） | 人工抽查 50 条 |
| AI 诊断响应时间 | < 5 秒 | API 日志 |
| 邮件生成可用率 | > 70% 可直接复制发送 | 人工评审 20 封 |
| 注册→添加域名成功率 | > 80% | 埋点漏斗 |
| 支付流程 | Stripe 端到端通过 | 测试卡支付 |
| 每日监控任务 | 稳定运行 7 天不中断 | 日志检查 |

---

## 7. MVP 开发时间估算（6 周）

| 周次 | 任务 | 产出 |
|------|------|------|
| **W1** | 项目初始化 + 数据库 + 认证 + DataForSEO 接入 | 可登录、可添加域名、可拉外链 |
| **W2** | 监控引擎（Python 爬虫 + 调度）+ 丢链检测 | 每日自动检查、可检测 404 |
| **W3** | AI 诊断（GPT-4o prompt + 结构化输出）+ 优先级排序 | 丢链有 AI 原因分析、有排序 |
| **W4** | AI 邮件生成 + 健康评分 + 前端面板 | 核心功能闭环跑通 |
| **W5** | 免费健康检查工具 + 首页 + 定价页 + Stripe 支付 | 可对外展示、可付费 |
| **W6** | 邮件通知 + 埋点 + 测试 + Bug 修复 | 可发布给 beta 用户 |

**假设**：1 个全栈工程师全职，或 2 人（前端+后端）并行。

---

## 8. MVP 成本验算（月）

| 成本项 | MVP 用量 | 月成本 |
|--------|---------|--------|
| DataForSEO API | 10 个域名 × 5000 外链 = 5万 查询 | $150 |
| OpenAI GPT-4o | 5000 诊断 + 2000 邮件 = 7000 次 | $200 |
| 住宅代理 | 5万 请求 | $100 |
| Cloudflare Workers | 100万 请求/天 | $5（免费额度内） |
| Cloudflare D1 | 500万 读/写/天 | $0（免费额度内） |
| Cloudflare R2 | 1GB 存储 | $0（免费额度内） |
| Cloudflare Queues | 100万 消息/月 | $0（免费额度内） |
| VPS（爬虫） | 1 核 2G | $10 |
| **总计** | | **~$465/月** |

**收入假设**：50 付费用户 × $29 = $1,450/月  
**MVP 毛利率**：~68%（Cloudflare 免费额度大幅降低基础设施成本）

---

## 9. 迭代路线

### Phase 2（MVP 后 2-3 个月）
- Gmail API 集成（站内发送邮件）
- 恢复成功自动追踪（7 天后复查）
- Contact discovery（Hunter.io 集成）
- 变化事件流（Today's Changes feed）
- 健康评分趋势图（90 天历史）
- 团队/多用户支持
- 更多免费工具（toxic scanner）
- 内容 SEO 博客上线

### Phase 3（3-6 个月）
- 白标报告（Agency plan）
- API 接入
- 预测预警（AI 预测丢链风险）
- 多语言支持
- Affiliate 系统
- AppSumo 发布

---

## 10. 风险对冲

| 风险 | MVP 对策 |
|------|---------|
| 开发超期 | W3 结束若 AI 诊断未通，砍掉优先级排序，只保留原因分类 |
| 付费转化低 | W5 预留 3 天做定价 A/B（$19 vs $29 vs $39） |
| 爬虫被封 | MVP 监控层主要依赖 DataForSEO API，Playwright 爬虫仅用于免费工具快照和补充验证，规避高频爬取被封 |
| AI 诊断不准 | 显示"置信度"+"这是 AI 分析，建议人工复核"免责声明 |
| 成本超支 | 免费版限制：50 外链 + 3 次诊断/月，硬封顶 |
| D1 性能瓶颈 | 单表 < 100万 行无压力，超了再分片或切 PostgreSQL |
| Workers 冷启动 | OpenNext adapter 优化，首请求 < 500ms |

---

## 11. 决策检查点

| 检查点 | 时间 | 通过标准 | 不通过则 |
|--------|------|---------|---------|
| CP1：数据通路 | W1 结束 | 能拉取外链并存储 | 停，评估 DataForSEO 替代方案 |
| CP2：监控可用 | W2 结束 | 每日任务稳定运行 | 停，简化监控逻辑 |
| CP3：AI 诊断质量 | W3 结束 | 人工评审 20 条，准确率 >70% | 停，重写 prompt 或降级为规则引擎 |
| CP4：闭环跑通 | W4 结束 | 端到端流程无阻塞 | 砍功能保上线 |
| CP5：付费验证 | W6 结束 | 10 个 beta 用户中 ≥1 人付费 | 调整定价或免费版限制 |

---

**总结**：MVP 把 PRD v2.0 的 10 个 P0 功能砍到 7 个核心功能，技术栈从 14 项压到 11 项（Cloudflare 全家桶 + 独立爬虫），6 周上线，月成本 $465。唯一不可砍的是 **AI 诊断 + 邮件生成** 这个闭环。
