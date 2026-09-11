# 原生 Agent 组织白皮书草案 v0.1

## 1. 为什么提出这个模型

今天绝大多数“企业 AI 化”都建立在一个既有组织之上。

人已经在公司里，部门已经划分，流程已经形成，软件系统已经部署，权力结构和工作习惯也已经稳定。AI 最后才进入。

这意味着 AI 天生处于“外挂”位置。

典型链路是：

```text
采购 AI
↓
部署系统
↓
培训员工
↓
员工采用
↓
改变工作习惯
↓
AI 才开始产生价值
```

整个价值链依赖“人的主动 adoption”。

原生 Agent 组织提出另一种起点：

> 如果公司本来就是为 Agent 时代设计的，它是否根本不需要经历“AI 化”这一步？

---

## 2. 核心定义

原生 Agent 组织，是一种以 **Role（岗位）为持久组织单元**、以 Agent 为默认认知执行层、以 Human 为可按需接入能力资源的组织模型。

核心关系：

```text
Role > Agent
Role > Human
Role > Model
Role > Tool
```

这里的“大于”不是权力关系，而是生命周期关系：

- Agent 可以替换，Role 不消失；
- Human 可以离职，Role 不消失；
- Model 可以升级，Role 不消失；
- Tool 可以更换，Role 不消失。

---

## 3. Role Object

每一个 Role 至少应该具备：

- Identity：岗位身份
- Mission：使命
- Objectives：目标
- KPI：衡量标准
- Capability Requirements：所需能力
- Authority：权限
- Policies：政策和约束
- Memory：长期记忆
- State：当前状态
- Decision History：决策历史
- Tools：工具
- Resident Agent：常驻岗位 Agent
- Human Assignments：当前接入的人类

Role 才是组织连续性的核心。

---

## 4. Agent 先于 Human 工作

假设公司需要一个“北美商务拓展”岗位。

传统公司先招聘销售。

原生 Agent 组织先创建：

```text
ROLE-00017
North America Business Development
```

Role Agent 可以立即开始：

- 市场研究
- 潜客搜索
- CRM 建档
- 开发信
- 客户跟进
- 会议材料
- Pipeline 分析
- SOP 形成
- 成功/失败复盘

因此可能出现：

> 岗位已经工作了，但暂时没有人类员工。

---

## 5. Capability Gap

Role Agent 在持续运行过程中，比较：

```text
岗位需要的能力
-
现有 Agent 能力
-
现有人类能力
-
现有 Tool / Vendor 能力
=
Capability Gap
```

例如：

```text
Negotiation       缺口 30
Relationship      缺口 55
Offline Presence  缺口 70
```

系统不应该立刻得出“招人”。

而应该依次判断：

```text
Build
Buy
Automate
Delegate
Outsource
Assign Existing Human
Hire New Human
```

因此招聘只是 Capability Acquisition 的一种方式。

---

## 6. Machine-Initiated Hiring

当某个能力缺口：

- 持续存在；
- 明显影响目标；
- 无法通过模型、工具或外包合理解决；
- 招聘 Human 在成本和可靠性上更优；

Role Agent 可以生成 Hiring Request。

不是：

> 我要一个销售。

而是：

> 我的当前目标被以下能力缺口限制，我需要一个具备这些能力的人类协作者。

People Agent 再去寻找候选人。

---

## 7. Role Agent 参与面试

传统面试由 HR 与主管主导。

原生 Agent 组织中，Role Agent 本身已经长期处理真实工作，因此能够参与工作能力评估。

例如用真实匿名化案例：

> 客户认为报价过高。现在由你接管谈判，我扮演客户。

这样评估的是实际 Capability，而不是抽象 JD 匹配。

高影响用工决策仍需明确人类审批与责任。

---

## 8. Assignment，而不是“人和 Agent 绑死”

Human 与 Role 之间通过 Assignment 连接：

```text
Human
  ↓
Assignment
  ↓
Role
```

这样支持：

- 一个 Role 多个人；
- 一个人多个 Role；
- 临时接入；
- Fractional Role；
- 无 Human 运行；
- 人员离职后的连续运行。

---

## 9. Agent-led Onboarding

新人入职时，进入的是一个已经运行的 Role。

Role Agent 可以直接说明：

- 当前目标；
- 当前客户；
- 当前任务；
- 历史策略；
- 失败经验；
- 风险；
- 今天最应该处理什么。

因此 Onboarding 从：

> 教员工如何使用 AI

变成：

> 让 Agent 教会员工如何完成这个 Role。

---

## 10. Active Organizational Memory

传统知识库是被动的：

> 不知道时去搜。

原生 Agent 组织需要主动式组织记忆：

> 因为我知道过去发生过什么，所以我主动影响现在的行动。

建议至少分：

1. Organization Memory
2. Role Memory
3. Entity Memory
4. Working Memory
5. Decision Log

---

## 11. Capability Allocation

传统企业管理 Headcount。

原生 Agent 组织管理 Capability。

不是先问：

> 需要多少人？

而是先问：

> 完成目标需要什么能力？

然后由：

- Agent
- Model
- API
- Software
- Vendor
- Freelancer
- Human

组成最优能力组合。

Headcount 成为结果，而不是起点。

---

## 12. Boss Agent

Boss Agent 不应该是“什么都能干的超级聊天机器人”。

它更像 Organization Orchestrator：

- 公司目标拆解；
- Role 创建；
- 跨 Role 协调；
- 资源配置；
- Capability Allocation；
- 冲突处理；
- 权限升级；
- Human / Agent 协同。

---

## 13. 这不是无人公司

原生 Agent 组织并不假设 Human 不再重要。

它只否定一个默认前提：

> 为什么每一个岗位都必须先由一个人类占据？

人类仍然在信任、关系、责任、伦理、复杂判断、创造和现实世界行动中拥有关键作用。

---

## 14. 最小可验证产品

第一版不应该做“整家公司”。

只验证一个完整闭环：

```text
Create Organization
↓
Create BD Role
↓
Role Agent starts work
↓
Memory & State accumulate
↓
Capability Gap detected
↓
Hiring Request
↓
Candidate evaluation
↓
Human Assignment
↓
Agent-led onboarding
↓
Human + Agent continue Role
```

如果这个闭环成立，“原生 Agent 组织”就从概念进入可实验阶段。

---

## 15. 核心命题

> **岗位先于员工存在。**
>
> **Agent 先于人类上岗。**
>
> **能力先于人头规划。**
>
> **组织记忆不应跟着员工离职。**
>
> **未来公司可能不再只是招聘员工填补岗位，而是岗位主动寻找人类来补全自己的能力。**

---

## 相关文档

- [README.zh-CN.md](../README.zh-CN.md) — 中文项目说明与术语表
- [README.md](../README.md) — English README
- [docs/MANIFESTO.md](MANIFESTO.md) — 宣言：九条主张
- [docs/CONCEPT.md](CONCEPT.md) — 概念模型
- [architecture/OVERVIEW.md](../architecture/OVERVIEW.md) — 参考架构 v0.1
- [architecture/DIAGRAMS.md](../architecture/DIAGRAMS.md) — 架构图
- [spec/ROLE_OBJECT.md](../spec/ROLE_OBJECT.md) — Role 对象规范
- [spec/CAPABILITY_MODEL.md](../spec/CAPABILITY_MODEL.md) — 能力模型
- [spec/ASSIGNMENT_OBJECT.md](../spec/ASSIGNMENT_OBJECT.md) — Assignment 对象规范
- [GOVERNANCE.md](../GOVERNANCE.md) — 治理原则
- [PUBLICATION.md](../PUBLICATION.md) — 公开发布记录
