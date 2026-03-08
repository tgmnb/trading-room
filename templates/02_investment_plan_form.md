# 投资旨意规划书

## 通用字段
- **template_id**: investment_plan_form
- **version**: 1.0.0
- **created_at**: {{created_at}}
- **author**: zhongshu
- **tags**: 规划, 拆解, 投资

---

## 内容字段

### 1. 问题定义
```yaml
问题定义:
  - 原始任务标题: {{original_task_title}}
  - 核心问题: {{core_question}}
  - 问题边界:
      - 必须回答的问题: [{{must_answer_questions}}]
      - 不涉及的问题: [{{not_include_questions}}]
  - 交付标准: {{delivery_standard}}
```

### 2. 流程选择
```yaml
流程选择:
  - 采用完整治理链: 是/否
  - 采用简化链: 是/否
  - 流程选择理由: {{process_choice_reason}}
```

### 3. 子任务拆解
```yaml
子任务拆解:
  - 子任务列表:
    - 子任务1:
        - 编号: {{subtask1_id}}
        - 标题: {{subtask1_title}}
        - 负责部门: {{subtask1_dept}}
        - 前置依赖: [{{subtask1_dependencies}}]
        - 优先级: 高/中/低
    - 子任务2:
        - 编号: {{subtask2_id}}
        - 标题: {{subtask2_title}}
        - 负责部门: {{subtask2_dept}}
        - 前置依赖: [{{subtask2_dependencies}}]
        - 优先级: 高/中/低
  - 执行顺序: {{execution_order}}
```

### 4. 证据需求
```yaml
证据需求:
  - A级证据要求(必须):
      - [{{required_grade_a_evidence}}]
  - B级证据要求(建议):
      - [{{required_grade_b_evidence}}]
  - C级证据(允许):
      - [{{allowed_grade_c_evidence}}]
  - 证据不足时: {{when_insufficient_evidence}}
```

### 5. 输出模板要求
```yaml
输出模板要求:
  - 各部门输出模板:
      - {{dept1}}: {{dept1_template}}
      - {{dept2}}: {{dept2_template}}
  - 质量门槛: {{quality_threshold}}
  - 禁止输出: {{forbidden_output}}
```

### 6. 时间与资源
```yaml
时间与资源:
  - 预期完成时间: {{expected_completion_time}}
  - 关键节点: {{key_milestones}}
  - 资源需求: {{resource_requirements}}
```

### 7. 规划结论
```yaml
规划结论:
  - 规划状态: 待审议/已通过/已驳回
  - 风险提示: {{risk_warnings}}
  - 备注: {{remarks}}
```
