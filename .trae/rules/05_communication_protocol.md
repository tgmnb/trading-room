---
alwaysApply: false
description: Agent 间通信协议
---
# Agent 间通信协议

## 5.1 数据传递格式

所有 Agent 间数据传递使用 JSON 格式：

```json
{
  "task_id": "JJC-20260307-001",
  "from_agent": "zhongshu_news",
  "to_agent": "zhongshu",
  "content_type": "事件卡片",
  "payload": {
    "event_title": "央行降息25bp",
    "event_type": "政策",
    "importance": "高",
    "evidence_level": "A",
    "market_known": "中"
  },
  "timestamp": "2026-03-07T10:00:00Z",
  "require_response": true
}
```

## 5.2 消息类型

| 类型 | 说明 | 响应要求 |
|------|------|----------|
| REQUEST | 请求处理 | 必须响应 |
| RESPONSE | 响应请求 | 无需响应 |
| NOTIFY | 通知 | 可选响应 |
| ALERT | 警告 | 必须响应 |

## 5.3 通信协议

### 5.3.1 中书省 → 门下省

```
方向: 中书省 → 门下省
内容: 提交候选交易案
格式: REQUEST + 候选交易案
```

### 5.3.2 门下省 → 中书省

```
方向: 门下省 → 中书省
内容: 审查结果(同意/封驳/缓议)
格式: RESPONSE + 审查意见
```

### 5.3.3 尚书省 → 六部

```
方向: 尚书省 → 六部
内容: 派发任务
格式: REQUEST + 任务详情
```

### 5.3.4 六部 → 尚书省

```
方向: 六部 → 尚书省
内容: 执行结果
格式: RESPONSE + 执行报告
```

### 5.3.5 任意 → 御史台

```
方向: 任意 → 御史台
内容: 触发监察
格式: ALERT + 监察事项
```

### 5.3.6 御史台 → 用户

```
方向: 御史台 → 用户
内容: 监察报告
格式: NOTIFY + 监察意见
```

## 5.4 调用优先级

| 优先级 | Agent | 场景 |
|--------|-------|------|
| P0 | 太子 | 旨意创建、紧急任务 |
| P1 | 门下省 | 审核任务 |
| P2 | 中书省 | 研究任务 |
| P3 | 六部 | 执行任务 |
| P4 | 御史台 | 监察任务 |

## 5.5 数据流方向

```
用户(下旨)
    ↓
太子(分拣)
    ↓
中书省(研究起草)
    ↓
门下省(审核封驳)
    ↓
尚书省(调度执行)
    ↓
六部(执行)
    ↓
尚书省(汇总)
    ↓
御史台(监察)
    ↓
用户(反馈)
```

## 5.6 状态机定义

```python
_STATE_MACHINE = {
    'Taizi': {'next': 'Zhongshu', 'allowed_role': '太子'},
    'Zhongshu': {'next': 'Menxia', 'allowed_role': '中书省'},
    'Menxia': {'next': 'Assigned', 'allowed_role': '门下省'},
    'Assigned': {'next': 'Doing', 'allowed_role': '尚书省'},
    'Doing': {'next': 'Review', 'allowed_role': '六部'},
    'Review': {'next': 'Done', 'allowed_role': '尚书省'},
    'Blocked': {'next': None, 'allowed_role': '暂停'},
    'Cancelled': {'next': None, 'allowed_role': '终止'},
    'Done': {'next': None, 'allowed_role': '完成'},
}
```
