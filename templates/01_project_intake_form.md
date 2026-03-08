# 立项分拣单

## 通用字段
- **template_id**: project_intake_form
- **version**: 1.0.0
- **created_at**: {{created_at}}
- **author**: taizi
- **tags**: 立项, 分拣

---

## 内容字段

### 1. 原始输入
```yaml
原始输入:
  - 用户原话: {{user_original_input}}
  - 输入时间: {{input_time}}
```

### 2. 任务分类
```yaml
任务分类:
  - 是否正式任务: 是/否
  - 任务类型:
      - 研究类: 是/否
      - 监控类: 是/否
      - 计划类: 是/否
      - 复盘类: 是/否
      - 问责类: 是/否
  - 任务简要说明: {{task_summary}}
```

### 3. 任务提炼
```yaml
任务提炼:
  - 任务标题: {{task_title}}
  - 核心诉求: {{core_requirement}}
  - 紧急程度: 低/中/高
  - 预估复杂度: 简单/中等/复杂
```

### 4. 流程判断
```yaml
流程判断:
  - 是否需要完整三省六部流程: 是/否
  - 是否可以走短链路: 是/否
  - 短链路理由(若适用): {{short_chain_reason}}
  - 推荐处理部门: {{recommended_dept}}
```

### 5. 分拣结论
```yaml
分拣结论:
  - 分拣状态: 已立项/转闲聊/缓议
  - 下一步动作: {{next_action}}
  - 备注: {{remarks}}
```
