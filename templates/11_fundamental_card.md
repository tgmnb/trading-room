# 预期差分析卡

## 通用字段
- **template_id**: fundamental_card
- **version**: 1.0.0
- **created_at**: {{created_at}}
- **author**: bingbu
- **tags**: 基本面, 预期差, 兵部

---

## 内容字段

### 1. 分析对象
```yaml
分析对象:
  - 标的: {{symbol}}
  - 分析领域: 行业/公司/主题/宏观
  - 分析时间: {{analysis_time}}
```

### 2. 预期差分析
```yaml
预期差分析:
  - 市场主流预期: {{market_mainstream_expectation}}
  - 潜在偏差: {{potential_deviation}}
  - 偏差类型: 信息差/理解差/时间差
  - 偏差说明: {{deviation_description}}
```

### 3. 催化剂与验证
```yaml
催化剂与验证:
  - 催化剂: {{catalysts}}
  - 验证节奏: {{verification_timeline}}
  - 逻辑成立条件: {{logic_valid_conditions}}
  - 失效条件: {{invalid_conditions}}
```

### 4. 结论
```yaml
结论:
  - 证据等级: A/B/C
  - 当前判断: 可研究/可观察/可提交候选案
  - 最大不确定点: {{max_uncertainty}}
  - 后续跟踪建议: {{follow_up_suggestions}}
```
