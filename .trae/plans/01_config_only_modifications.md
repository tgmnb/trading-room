# 只需要修改配置或文档的内容

本文件说明哪些功能可以通过修改配置或文档（SOUL.md、配置文件、说明性文本）来实现，而不需要修改原有的项目框架代码。

## 1. Agent 定义（SOUL.md 文件）

### 1.1 现有的 Agent（无需新增）

现有项目已经有以下 Agent，只需要更新他们的 SOUL.md 文件：

| Agent ID | 现有位置 | 需修改内容 |
|---------|---------|-----------|
| `taizi` | `agents/taizi/SOUL.md` | 更新为"太子·任务分拣与立项官"职责 |
| `zhongshu` | `agents/zhongshu/SOUL.md` | 更新为"中书省·规划中心"职责（不再直接做研究） |
| `menxia` | `agents/menxia/SOUL.md` | 更新为"门下省·审议与封驳中心"，强化必经节点和封驳权 |
| `shangshu` | `agents/shangshu/SOUL.md` | 更新为"尚书省·派发、状态与回奏中心" |
| `libu_hr` | `agents/libu_hr/SOUL.md` | 更新为"吏部·行为画像与成长训练部" |
| `hubu` | `agents/hubu/SOUL.md` | 更新为"户部·资金、仓位与组合部" |
| `libu` | `agents/libu/SOUL.md` | 更新为"礼部·流程、文书、定时任务与配额治理部" |
| `bingbu` | `agents/bingbu/SOUL.md` | 更新为"兵部·投资研究与计划部" |
| `xingbu` | `agents/xingbu/SOUL.md` | 更新为"刑部·纪律、稽核与问责部" |
| `gongbu` | `agents/gongbu/SOUL.md` | 更新为"工部·数据、回测、技术统计与自动化部" |
| `zaochao` | `agents/zaochao/SOUL.md` | 更新为"早朝官·制度节律与会议节点"（从"钦天监"改为"早朝官"） |

### 1.2 需要新增的 Agent（但仍为配置文件）

虽然需要创建新目录，但这些仍属于配置/文档层面：

| Agent ID | 建议位置 | 说明 |
|---------|---------|------|
| `yushitai` | `agents/yushitai/SOUL.md` | 御史台（独立监察机构） |
| `huangchengsi` | `agents/huangchengsi/SOUL.md` | 皇城司（资讯中台与议题入池中心） |
| `fagaiwei` | `agents/fagaiwei/SOUL.md` | 发改委（长期逻辑与行业景气中心） |

## 2. 看板显示配置（仅需修改 server.py 的 _AGENT_DEPTS）

现有项目在 `dashboard/server.py` 中有 `_AGENT_DEPTS` 配置，只需要修改这个数组：

### 2.1 需要修改的配置项

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
    # 修改：从'钦天监'改为'早朝官'
    {'id':'zaochao', 'label':'早朝官','emoji':'🌅', 'role':'早朝官',   'rank':'正三品'},
    # 新增：御史台
    {'id':'yushitai','label':'御史台','emoji':'⚡', 'role':'御史中丞', 'rank':'从三品'},
    # 新增：皇城司
    {'id':'huangchengsi','label':'皇城司','emoji':'🏯', 'role':'皇城司使', 'rank':'正四品'},
    # 新增：发改委
    {'id':'fagaiwei','label':'发改委','emoji':'📊', 'role':'发改委主任', 'rank':'正四品'},
]
```

## 3. 模板文件（配置级）

新设计中的所有模板都可以作为配置文件放在单独的目录中，不需要修改代码框架：

| 模板名称 | 建议位置 | 说明 |
|---------|---------|------|
| 立项分拣单 | `templates/lixiang_fenjiandan.md` | 太子输出 |
| 投资旨意规划书 | `templates/touzi_zhiyi_guihuashu.md` | 中书省输出 |
| 议题卡 | `templates/yiti_card.md` | 皇城司输出 |
| 事件卡片 | `templates/shijian_card.md` | 兵部·新闻情报官输出 |
| 技术统计卡 | `templates/jishu_tongji_card.md` | 工部·技术统计官输出 |
| 预期差分析卡 | `templates/yuqicha_fenxi_card.md` | 兵部·基本面预期差官输出 |
| 反证审查单 | `templates/fanzheng_shenchadan.md` | 门下省·反证官输出 |
| 替代成本审核单 | `templates/ticaidai_cost_shenhedan.md` | 门下省·替代成本官输出 |
| 机会排序表 | `templates/jihui_paixubiao.md` | 兵部·机会排序官输出 |
| 交易计划书 | `templates/jiaoyi_jihuashu.md` | 兵部·计划官输出 |
| 执行偏差记录单 | `templates/zhixing_piancha_jiludan.md` | 刑部·执行督军输出 |
| 行为监察单 | `templates/xingwei_jianchadan.md` | 御史台·行为监察御史输出 |
| 朝会纪要 | `templates/chaohui_jiyao.md` | 早朝官输出 |

## 4. 配置文件

以下配置文件可以直接修改或新增，无需改动代码：

| 配置项 | 文件位置 | 说明 |
|-------|---------|------|
| Agent 配置 | `data/agent_config.json` | 可以配置各 Agent 的模型、技能等 |
| 定时任务表 | `data/scheduled_tasks.json`（需新增） | 礼部·时程官使用的 Cron 表 |
| 配额配置 | `data/quota_config.json`（需新增） | 礼部·配额官使用的配额配置 |
| 国策库数据 | `data/guoceluku.json`（需新增） | 国策库议题存储 |

## 5. 总结

**不需要修改代码框架的部分：**

1. ✅ 所有 Agent 的 SOUL.md 文件更新
2. ✅ 看板显示的 Agent 列表（_AGENT_DEPTS）
3. ✅ 新增 Agent（只要在 SOUL.md 和配置中注册）
4. ✅ 所有输出模板（作为配置文件存放）
5. ✅ 新增的配置数据文件

**需要修改代码框架的部分：**

1. ❌ 状态机流转逻辑（如需新增状态）
2. ❌ 任务派发逻辑（如需修改默认派发规则）
3. ❌ 新的 API 端点（如需新增功能）
4. ❌ 前端组件（如需新增功能面板）
