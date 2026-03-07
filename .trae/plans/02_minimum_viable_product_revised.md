# 最小可运行版本（MVP）的修改

本文件说明完成一个最小可运行的投资版三省六部系统需要进行哪些修改。

## MVP 目标

实现"分拣—规划—审议—派发—执行—回奏—朝会—监察"的闭环，使用最小可用编制。

## MVP 最小可用编制

根据设计文档，第一阶段建议先跑治理骨架：

### 治理层（必需）
- ✅ 太子：任务分拣与立项官
- ✅ 中书省：总规划官、任务拆解官、证据需求官、交付标准官
- ✅ 门下省：规划审查官、反证官、时机官、替代成本官
- ✅ 尚书省：总调度官、状态官、回奏汇总官、归档官
- ✅ 早朝官：盘前早朝官、盘后小朝官、周度大朝官

### 六部（必需）
- ✅ 吏部：行为画像官、训练教官
- ✅ 户部：仓位官、止损官
- ✅ 礼部：盘前官、盘后官、文书官
- ✅ 兵部：新闻情报官、基本面预期差官、机会排序官、计划官
- ✅ 刑部：执行督军、偏差归因官、越权官
- ✅ 工部：技术统计官、回测官、监控官

### 御史台（必需）
- ✅ 御史台：行为监察御史、机会遗弃御史

## 具体修改清单

### 1. 配置文件修改（无需代码改动）

#### 1.1 更新现有 Agent 的 SOUL.md

| 文件 | 修改内容 |
|------|---------|
| `agents/taizi/SOUL.md` | 更新为太子·任务分拣与立项官的职责 |
| `agents/zhongshu/SOUL.md` | 更新为中书省·规划中心（只做规划，不做研究） |
| `agents/menxia/SOUL.md` | 更新为门下省·审议与封驳中心（强化必经节点） |
| `agents/shangshu/SOUL.md` | 更新为尚书省·派发、状态与回奏中心 |
| `agents/libu_hr/SOUL.md` | 更新为吏部·行为画像与成长训练部 |
| `agents/hubu/SOUL.md` | 更新为户部·资金、仓位与组合部 |
| `agents/libu/SOUL.md` | 更新为礼部·流程、文书与简报部（定时任务与配额治理先保留设计，不要求在 MVP 阶段可用） |
| `agents/bingbu/SOUL.md` | 更新为兵部·投资研究与计划部 |
| `agents/xingbu/SOUL.md` | 更新为刑部·纪律、稽核与问责部 |
| `agents/gongbu/SOUL.md` | 更新为工部·数据、回测、技术统计与自动化部 |
| `agents/zaochao/SOUL.md` | 更新为早朝官·制度节律与会议节点 |

#### 1.2 新增 Agent 的 SOUL.md

| 文件 | 内容 |
|------|------|
| `agents/yushitai/SOUL.md` | 御史台·独立监察机构 |
| `agents/huangchengsi/SOUL.md` | 皇城司·资讯中台（可先占位，MVP 可暂不实现功能） |
| `agents/fagaiwei/SOUL.md` | 发改委·长期逻辑（可先占位，MVP 可暂不实现功能） |

#### 1.3 修改 dashboard/server.py 的 _AGENT_DEPTS

在 `dashboard/server.py` 第 657-669 行修改：

```python
_AGENT_DEPTS = [
    {'id':'taizi',   'label':'太子',  'emoji':'🤴', 'role':'太子',     'rank':'储君'},
    {'id':'zhongshu','label':'中书省','emoji':'📜', 'role':'中书令',   'rank':'正一品'},
    {'id':'menxia',  'label':'门下省','emoji':'🔍', 'role':'侍中',     'rank':'正一品'},
    {'id':'shangshu','label':'尚书省','emoji':'📮', 'role':'尚书令',   'rank':'正一品'},
    {'id':'hubu',    'label':'户部',  'emoji':'💰', 'role':'户部尚书', 'rank':'正二品'},
    {'id':'libu',    'label':'礼部',  'emoji':'📝', 'role':'礼部尚书', 'rank':'正二品'},
    {'id':'bingbu',  'label':'兵部',  'emoji':'⚔️', 'role':'兵部尚书', 'rank':'正二品'},
    {'id':'xingbu',  'label':'刑部',  'emoji':'⚖️', 'role':'刑部尚书', 'rank':'正二品'},
    {'id':'gongbu',  'label':'工部',  'emoji':'🔧', 'role':'工部尚书', 'rank':'正二品'},
    {'id':'libu_hr', 'label':'吏部',  'emoji':'👔', 'role':'吏部尚书', 'rank':'正二品'},
    {'id':'zaochao', 'label':'早朝官','emoji':'🌅', 'role':'早朝官',   'rank':'正三品'},
    {'id':'yushitai','label':'御史台','emoji':'⚡', 'role':'御史中丞', 'rank':'从三品'},
]
```

### 2. 代码框架修改（必需）

#### 2.1 状态机补充（如需）

检查现有状态是否满足 MVP 需求：

| 现有状态 | 是否满足 | 说明 |
|---------|---------|------|
| Taizi | ✅ | 太子分拣 |
| Zhongshu | ✅ | 中书省规划 |
| Menxia | ✅ | 门下省审议 |
| Assigned | ✅ | 尚书省派发 |
| Doing | ✅ | 六部执行 |
| Review | ✅ | 审查 |
| Done | ✅ | 完成 |
| Blocked | ✅ | 阻塞 |
| Cancelled | ✅ | 取消 |

**结论：现有状态机已满足 MVP 需求，无需修改。**

#### 2.2 状态映射补充

检查 `_STATE_AGENT_MAP` 和 `_ORG_AGENT_MAP`：

现有映射（dashboard/server.py 第 862-876 行）：
```python
_STATE_AGENT_MAP = {
    'Taizi': 'taizi',
    'Zhongshu': 'zhongshu',
    'Menxia': 'menxia',
    'Assigned': 'shangshu',
    'Doing': None,
    'Review': 'shangshu',
    'Next': None,
    'Pending': 'zhongshu',
}
_ORG_AGENT_MAP = {
    '礼部': 'libu', '户部': 'hubu', '兵部': 'bingbu',
    '刑部': 'xingbu', '工部': 'gongbu', '吏部': 'libu_hr',
    '中书省': 'zhongshu', '门下省': 'menxia', '尚书省': 'shangshu',
}
```

**需要补充：**
```python
_ORG_AGENT_MAP = {
    '礼部': 'libu', '户部': 'hubu', '兵部': 'bingbu',
    '刑部': 'xingbu', '工部': 'gongbu', '吏部': 'libu_hr',
    '中书省': 'zhongshu', '门下省': 'menxia', '尚书省': 'shangshu',
    '早朝官': 'zaochao', '御史台': 'yushitai',  # 新增
}
```

**说明：** `_AGENT_DEPTS` 和 `_ORG_AGENT_MAP` 都属于少量注册类代码修改，不是框架级重写，但也不应再视为“纯配置”。

### 3. MVP 工作流验证

确保以下工作流可以正常运行：

#### 3.1 标准即时任务链
```
用户 → 太子分拣 → 中书省规划 → 门下省审议 → 尚书省派发 → 六部执行 → 尚书省汇总 → 早朝官 → 御史台
```

#### 3.2 关键制度验证
- ✅ 门下省必经节点：现有代码已实现
- ✅ 封驳返工：现有代码已实现
- ✅ 状态机流转：现有代码已实现

## MVP 验收标准

完成以下检查项即为 MVP 完成：

- [ ] 所有现有 Agent 的 SOUL.md 已更新为投资版职责
- [ ] 新增御史台 Agent（SOUL.md + 配置）
- [ ] dashboard/server.py 的 _AGENT_DEPTS 已更新
- [ ] _ORG_AGENT_MAP 已补充早朝官和御史台
- [ ] 可以成功运行标准即时任务链
- [ ] 门下省可以封驳任务
- [ ] 任务可以正常流转到完成状态

## MVP 不包含的内容（后续迭代）

以下内容 MVP 阶段可以暂不实现，留待后续迭代：

- ❌ 皇城司（资讯中台）
- ❌ 发改委（长期逻辑）
- ❌ 国策库（延迟汇报机制）
- ❌ 礼部的配额治理（可先保留配置设计，但不要求 MVP 阶段真正可用）
- ❌ 定时任务链（可先保留任务表 schema，但不要求 MVP 阶段真正可用）
- ❌ 完整的模板文件（可以先在 SOUL.md 中描述格式）
