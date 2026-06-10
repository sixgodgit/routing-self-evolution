# 路由自我进化系统

## 核心机制

**自主路由 = 奖励，依赖专家 = 消耗**

```
┌─────────────────────────────────────┐
│  路由决策                            │
│  ├─ 自主完成 → +1 积分              │
│  └─ 咨询专家 → -2 积分              │
│                                     │
│  积分池：初始 0 分                   │
│  ├─ ≥ 5 分 → 解锁「自信模式」       │
│  ├─ ≤ -3 分 → 进入「谨慎模式」      │
│  └─ 其他 → 正常模式                 │
└─────────────────────────────────────┘
```

## 三种模式

| 模式 | 积分 | 行为 |
|------|------|------|
| **自信模式** | ≥ 5 | 减少咨询，尝试新路由 |
| **正常模式** | 0-4 | 标准规则 |
| **谨慎模式** | ≤ -3 | 多咨询，重点学习 |

## 积分规则

| 行为 | 积分变化 |
|------|----------|
| 自主路由成功 | +1 |
| 自主路由失败 | -3 |
| 咨询 GPT-5.4 | -2 |
| 咨询后学到新规则 | +1 |
| 连续 5 次自主成功 | +2（额外奖励） |
| 连续 3 次咨询 | -1（额外惩罚） |

## 进化目标

- **3 个月**：咨询频率 30% → 10%，积分 ≥ 5
- **6 个月**：咨询频率 → 5%，形成完整路由知识库

## 工作流程

```
遇到不确定的任务
    ↓
明确任务？→ 是 → 直接路由，不问
    ↓ 否
构造轻量咨询（< 100 tokens）
    ↓
问 GPT-5.4（~0.05-0.10 元/次）
    ↓
获取建议 → 记录 → 提取模式 → 更新规则
    ↓
我的最终决策 → 执行
```

## 学习机制

### 1. 记录每次咨询
- 我的判断 vs GPT 建议 vs 理由
- 结果：谁的路由更好

### 2. 提取模式
- 从 GPT 的建议中提取可复用的路由规则
- 更新到 core-task-routing 技能

### 3. 定期回顾
- 每周：自主路由准确率、咨询次数
- 每月：积分变化趋势、进化进度

## 文件结构

```
├── README.md                    # 项目说明
├── docs/
│   ├── evolution.md             # 进化机制详解
│   └── learning-examples.md     # 学习案例
├── src/
│   ├── routing-rules.md         # 路由规则表
│   └── expert-consultation.md   # 专家咨询模板
└── references/
    └── gpt-patterns.md          # GPT 建议模式库
```

## 相关技能

- `core-task-routing`：核心任务路由规则
- `model-routing-consultant`：老专家咨询系统
- `routing-self-evolution`：本技能（自我进化）

---

## 📄 License

This project is licensed under **CC BY-NC 4.0** — [Creative Commons Attribution-NonCommercial 4.0](https://creativecommons.org/licenses/by-nc/4.0/)

- ✅ **Free to use** — personal, educational, and open-source projects
- ✅ **Free to modify and distribute**
- ✅ **Attribution required** — Credit: **sixgod** ([@sixgodgit](https://github.com/sixgodgit))
- ❌ **No commercial use** — Selling or profit-making from this code is prohibited

**Author:** sixgod | **GitHub:** [github.com/sixgodgit](https://github.com/sixgodgit)

