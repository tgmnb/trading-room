# 反证审查单

## 通用字段
- **template_id**: counterevidence_review_form
- **version**: 1.0.0
- **created_at**: {{created_at}}
- **author**: menxia
- **tags**: 反证, 审查, 门下省

---

## 内容字段

### 1. 审查对象
```yaml
审查对象:
  - 对应规划书编号: {{plan_form_id}}
  - 规划书标题: {{plan_form_title}}
  - 核心逻辑: {{core_logic}}
```

### 2. 反证审查
```yaml
反证审查:
  - 最危险误判点: {{most_dangerous_mistake}}
  - 逻辑跳步点:
      - 跳步1: {{logic_jump_1}}
      - 跳步2: {{logic_jump_2}}
  - 偷换概念点:
      - 点1: {{concept_swap_1}}
      - 点2: {{concept_swap_2}}
  - 反向证据搜索结果:
      - 找到的反向证据: {{found_counterevidence}}
      - 反向证据强度: 强/中/弱/无
```

### 3. 审查结论
```yaml
审查结论:
  - 审查状态: 通过/封驳/缓议
  - 审查意见: {{review_opinion}}
  - 若封驳, 返工要求: {{rework_requirements}}
  - 若缓议, 需补充材料: {{supplementary_materials}}
  - 风险等级: 低/中/高
```
