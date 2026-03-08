# 技术统计卡

## 通用字段
- **template_id**: technical_card
- **version**: 1.0.0
- **created_at**: {{created_at}}
- **author**: gongbu
- **tags**: 技术, 统计, 工部

---

## 内容字段

### 1. 形态与样本
```yaml
形态与样本:
  - 形态/信号名称: {{pattern_name}}
  - 样本定义: {{sample_definition}}
  - 历史样本数: {{historical_sample_count}}
  - 样本时间范围: {{sample_time_range}}
```

### 2. 统计指标
```yaml
统计指标:
  - 胜率: {{win_rate}}
  - 盈亏比: {{profit_loss_ratio}}
  - 最大回撤特征: {{max_drawdown_feature}}
  - 常见持有周期: {{common_holding_period}}
```

### 3. 当前案例分析
```yaml
当前案例分析:
  - 当前案例与样本相似点: {{similar_points}}
  - 当前案例与样本差异点: {{different_points}}
  - 当前最大缺陷: {{current_max_defect}}
  - 证据等级: A/B/C
  - 当前判断: 可研究/可观察/可提交候选案/证据不足
```
