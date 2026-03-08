# 执行偏差记录单

## 通用字段
- **template_id**: execution_deviation_form
- **version**: 1.0.0
- **created_at**: {{created_at}}
- **author**: xingbu
- **tags**: 偏差, 执行, 刑部

---

## 内容字段

### 1. 对应计划
```yaml
对应计划:
  - 交易计划书编号: {{trading_plan_id}}
  - 标的: {{symbol}}
  - 计划时间: {{plan_time}}
```

### 2. 偏差记录
```yaml
偏差记录:
  - 实际行为: {{actual_behavior}}
  - 是否按计划执行: 是/否/部分
  - 偏差类型: 提前/延后/漏做/多做/改规则
  - 偏差说明: {{deviation_description}}
  - 偏差后果: {{deviation_consequence}}
```

### 3. 违规判断
```yaml
违规判断:
  - 是否属于重复违规: 是/否
  - 历史类似违规: {{historical_similar_violations}}
  - 初步判断: 执行问题/非执行问题/混合问题
  - 判断理由: {{judgment_reason}}
```

### 4. 问责建议
```yaml
问责建议:
  - 问责等级: 轻度/中度/严重
  - 改进建议: {{improvement_suggestions}}
  - 下次强制要求: {{next_time_requirements}}
```
