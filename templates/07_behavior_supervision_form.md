# 行为监察单

## 通用字段
- **template_id**: behavior_supervision_form
- **version**: 1.0.0
- **created_at**: {{created_at}}
- **author**: yushitai
- **tags**: 监察, 行为, 御史台

---

## 内容字段

### 1. 监察对象
```yaml
监察对象:
  - 监察对象: 用户本人
  - 监察时间: {{supervision_time}}
  - 触发场景: {{trigger_scenario}}
```

### 2. 违规行为
```yaml
违规行为:
  - 违规/偏差行为: {{violation_behavior}}
  - 对应旧错误标签: {{old_error_tags}}
  - 本次后果: {{current_consequence}}
  - 是否重复错误: 是/否
  - 历史记录: {{historical_records}}
```

### 3. 监察判断
```yaml
监察判断:
  - 监察判断: 轻度/中度/严重
  - 判断理由: {{judgment_reason}}
  - 问责意见: {{accountability_opinion}}
  - 下次强制要求: {{next_time_requirements}}
```
