# 替代成本审核单

## 通用字段
- **template_id**: switch_cost_review_form
- **version**: 1.0.0
- **created_at**: {{created_at}}
- **author**: menxia
- **tags**: 替代成本, 审核, 门下省

---

## 内容字段

### 1. 审核对象
```yaml
审核对象:
  - 原持仓/原机会A: {{original_opportunity_a}}
  - 新机会B: {{new_opportunity_b}}
  - 切换申请时间: {{switch_request_time}}
  - 申请切换理由: {{switch_reason}}
```

### 2. A与B综合质量对比
```yaml
A与B综合质量对比:
  - A质量评分: {{a_quality_score}}
  - B质量评分: {{b_quality_score}}
  - 质量差异说明: {{quality_difference_description}}
  - B是否显著优于A: 是/否
  - 判断理由: {{judgment_reason}}
```

### 3. A的状态检查
```yaml
A的状态检查:
  - A是否真的失效: 是/否
  - 失效证据: {{invalid_evidence}}
  - A当前状态: {{a_current_status}}
  - 若A未失效, 继续持有理由: {{if_a_valid_reason}}
```

### 4. 切换成本分析
```yaml
切换成本分析:
  - 直接成本(手续费/滑点): {{direct_cost}}
  - 机会成本: {{opportunity_cost}}
  - 心理成本: {{psychological_cost}}
  - 切换是否值得: 是/否
  - 综合判断: {{comprehensive_judgment}}
```

### 5. 审核结论
```yaml
审核结论:
  - 审核状态: 同意切换/不同意切换/缓议
  - 审核意见: {{review_opinion}}
  - 若同意, 注意事项: {{if_agree_notes}}
  - 若不同意, 替代建议: {{if_disagree_suggestions}}
  - 若缓议, 需补充材料: {{if_defer_materials}}
```
