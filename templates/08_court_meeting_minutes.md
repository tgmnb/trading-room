# 朝会纪要

## 通用字段
- **template_id**: court_meeting_minutes
- **version**: 1.0.0
- **created_at**: {{created_at}}
- **author**: zaochao
- **tags**: 纪要, 朝会, 早朝官

---

## 内容字段

### 1. 朝会基本信息
```yaml
朝会基本信息:
  - 朝会类型: 盘前早朝/盘后小朝/周度大朝/重大失误复盘
  - 朝会时间: {{meeting_time}}
  - 参与部门: {{participating_departments}}
  - 朝会主题: {{meeting_theme}}
```

### 2. 盘前早朝内容(若适用)
```yaml
盘前早朝内容:
  - 今日重点机会: {{today_key_opportunities}}
  - 今日风险点: {{today_risk_points}}
  - 今日执行计划: {{today_execution_plan}}
  - 今日不超过3个重点: {{top_3_focus}}
```

### 3. 盘后小朝内容(若适用)
```yaml
盘后小朝内容:
  - 执行偏差核对: {{execution_deviation_check}}
  - 异常记录: {{abnormal_records}}
  - 今日总结: {{today_summary}}
```

### 4. 周度大朝内容(若适用)
```yaml
周度大朝内容:
  - 本周最优决策: {{weekly_best_decision}}
  - 本周最差决策: {{weekly_worst_decision}}
  - 重复性错误: {{repetitive_errors}}
  - 遗弃机会跟踪: {{abandoned_opportunities_tracking}}
```

### 5. 重大失误复盘内容(若适用)
```yaml
重大失误复盘内容:
  - 失误事件: {{mistake_event}}
  - 失误原因: {{mistake_reason}}
  - 责任界定: {{responsibility_definition}}
  - 改进措施: {{improvement_measures}}
```

### 6. 朝会决议
```yaml
朝会决议:
  - 决议事项: {{resolution_items}}
  - 后续行动: {{follow_up_actions}}
  - 责任人: {{responsible_persons}}
  - 完成时间: {{completion_time}}
```
