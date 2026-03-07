---
alwaysApply: false
description: 代码风格指南
---
# 代码风格指南

## 2.1 通用规范

- **语言**: 简体中文(代码注释除外)
- **缩进**: 4 空格(Python)，2 空格(JavaScript/TypeScript)
- **行宽**: 最大 120 字符
- **编码**: UTF-8

## 2.2 Python 代码规范

```python
# ✓ 正确示例
def calculate_position_size(capital: float, risk_ratio: float, stop_loss_pct: float) -> float:
    """计算仓位大小"""
    return capital * risk_ratio / stop_loss_pct

# ✗ 错误示例
def calculate(capital, risk_ratio, stop_loss_pct):  # 缺少类型标注
    return capital * risk_ratio / stop_loss_pct    # 缺少文档字符串
```

- 使用 type hints
- 使用 docstring 描述函数功能
- 保持函数简洁(建议 < 50 行)

## 2.3 JavaScript/TypeScript 代码规范

```typescript
// ✓ 正确示例
interface Task {
  id: string;
  title: string;
  state: 'Taizi' | 'Zhongshu' | 'Menxia' | 'Doing' | 'Done';
}

// ✗ 错误示例
interface Task {  // 缺少类型定义
  id,
  title,
  state
}
```

- 使用 TypeScript 强类型
- 使用 const/let，避免 var
- 优先使用箭头函数

## 2.4 文件命名约定

| 类型 | 命名规则 | 示例 |
|------|----------|------|
| Agent 目录 | 中划线分隔 | `zhongshu_news/` |
| SOUL 文件 | 大写 SOUL.md | `agents/zhongshu_news/SOUL.md` |
| Python 模块 | 下划线分隔 | `task_service.py` |
| React 组件 | PascalCase | `TaskModal.tsx` |
| 配置文件 | 小写下划线 | `app_config.json` |
| 测试文件 | `test_` 前缀 | `test_kanban.py` |

## 2.5 常量定义规范

```python
# 状态常量
_STATE_MACHINE = {
    'Taizi': {'next': 'Zhongshu', 'allowed_role': '太子'},
    'Zhongshu': {'next': 'Menxia', 'allowed_role': '中书省'},
    'Menxia': {'next': 'Assigned', 'allowed_role': '门下省'},
    'Assigned': {'next': 'Doing', 'allowed_role': '尚书省'},
    'Doing': {'next': 'Review', 'allowed_role': '六部'},
    'Review': {'next': 'Done', 'allowed_role': '尚书省'},
}

# 证据等级
EVIDENCE_LEVELS = ['A', 'B', 'C']
# A级: 原始数据、公告、行情事实
# B级: 统计研究、历史回测、高质量二手资料
# C级: 经验判断、逻辑推演、主观估计
```
