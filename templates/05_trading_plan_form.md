# 交易计划书

## 通用字段
- **template_id**: trading_plan_form
- **version**: 1.0.0
- **created_at**: {{created_at}}
- **author**: bingbu
- **tags**: 交易, 计划, 兵部

---

## 内容字段

### 1. 基本信息
```yaml
基本信息:
  - 标的: {{symbol}}
  - 方向: 做多/做空
  - 当前优先级: 1/2/3
  - 计划类型: 试仓/正式/观察
  - 核心逻辑: {{core_logic}}
  - 为什么它比其他候选更强: {{why_better_than_others}}
```

### 2. 进场条件
```yaml
进场条件:
  - 首次进场条件: {{first_entry_condition}}
  - 首次仓位建议: {{first_position}}
  - 加仓条件: {{add_position_condition}}
  - 加仓比例: {{add_position_ratio}}
```

### 3. 退出条件
```yaml
退出条件:
  - 减仓条件: {{reduce_condition}}
  - 止损条件: {{stop_loss_condition}}
  - 止盈/退出条件: {{take_profit_condition}}
  - 失效条件: {{invalid_condition}}
```

### 4. 时间与替代
```yaml
时间与替代:
  - 最大容忍时间: {{max_tolerant_time}}
  - 若不触发则如何处理: {{if_not_triggered}}
  - 若出现替代机会则如何处理: {{if_alternative}}
```

### 5. 审核状态
```yaml
审核状态:
  - 门下省放行情况: 已放行/待放行/被封驳
  - 门下省意见: {{menxia_opinion}}
  - 户部风控情况: {{hubu_risk_control}}
  - 户部意见: {{hubu_opinion}}
```
