# 事件卡片

## 通用字段
- **template_id**: event_card
- **version**: 1.0.0
- **created_at**: {{created_at}}
- **author**: bingbu
- **tags**: 事件, 情报, 兵部

---

## 内容字段

### 1. 事件基本信息
```yaml
事件基本信息:
  - 事件标题: {{event_title}}
  - 事件时间: {{event_time}}
  - 事件类型: 新闻/公告/政策/产业链/突发
  - 事实摘要: {{fact_summary}}
```

### 2. 影响分析
```yaml
影响分析:
  - 直接相关对象: {{direct_related_objects}}
  - 潜在影响路径: {{potential_impact_path}}
  - 市场已知程度: 低/中/高
  - 事件重要性: 低/中/高
```

### 3. 判断与建议
```yaml
判断与建议:
  - 证据等级: A/B/C
  - 当前判断: 噪音/进入观察池/可提交候选案
  - 最大不确定点: {{max_uncertainty}}
  - 后续跟踪建议: {{follow_up_suggestions}}
```
