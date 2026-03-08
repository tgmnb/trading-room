# 机会排序表

## 通用字段
- **template_id**: opportunity_ranking_form
- **version**: 1.0.0
- **created_at**: {{created_at}}
- **author**: bingbu
- **tags**: 机会, 排序, 兵部

---

## 内容字段

### 1. 排序规则
```yaml
排序规则:
  - 评分维度:
      - 上涨潜力: 权重30%
      - 失效成本: 权重25%
      - 执行难度: 权重20%
      - 证据强度: 权重15%
      - 时机适配: 权重10%
  - 评分方法: {{scoring_method}}
```

### 2. 候选机会列表
```yaml
候选机会列表:
  - 机会1:
      - 标的: {{opportunity1_symbol}}
      - 方向: {{opportunity1_direction}}
      - 综合评分: {{opportunity1_score}}
      - 分项评分:
          - 上涨潜力: {{opportunity1_potential}}
          - 失效成本: {{opportunity1_failure_cost}}
          - 执行难度: {{opportunity1_execution_difficulty}}
          - 证据强度: {{opportunity1_evidence_strength}}
          - 时机适配: {{opportunity1_timing}}
      - 排序理由: {{opportunity1_reason}}
  - 机会2:
      - 标的: {{opportunity2_symbol}}
      - 方向: {{opportunity2_direction}}
      - 综合评分: {{opportunity2_score}}
      - 分项评分:
          - 上涨潜力: {{opportunity2_potential}}
          - 失效成本: {{opportunity2_failure_cost}}
          - 执行难度: {{opportunity2_execution_difficulty}}
          - 证据强度: {{opportunity2_evidence_strength}}
          - 时机适配: {{opportunity2_timing}}
      - 排序理由: {{opportunity2_reason}}
```

### 3. 排序结论
```yaml
排序结论:
  - 优先级排序: {{priority_order}}
  - 建议优先关注: {{top_priority}}
  - 观察池: {{watchlist}}
  - 排除理由: {{exclusion_reasons}}
```
