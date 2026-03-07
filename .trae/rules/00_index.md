# 规则文档索引

本文档为开发规则的索引目录，便于按需查阅。

## 文件清单

| 文件 | 内容 |
|------|------|
| [01_architecture.md](01_architecture.md) | 项目架构规范 - 太子+三省六部+早朝官+御史台+专项机构架构、目录结构、系统分层 |
| [02_code_style.md](02_code_style.md) | 代码风格指南 - Python/TypeScript 规范、文件命名 |
| [03_agent_definitions.md](03_agent_definitions.md) | Agent 功能定义 - 所有核心 Agent 详细职责（太子/三省/六部/早朝官/御史台/专项机构） |
| [04_trigger_conditions.md](04_trigger_conditions.md) | Agent 触发条件 - 任务流转（标准即时/国策议题/定时）、特殊触发、流程触发规则、关键制度铁律触发 |
| [05_communication_protocol.md](05_communication_protocol.md) | 通信协议 - JSON格式、消息类型、优先级、状态机定义 |
| [06_exception_handling.md](06_exception_handling.md) | 异常处理 - Agent/流程/数据异常处理 |
| [07_permission_matrix.md](07_permission_matrix.md) | 权限矩阵 - Agent通信权限、禁止越权规则 |
| [08_template_spec.md](08_template_spec.md) | 模板规范 - 通用字段、模板优先级、详细模板规范 |

## 快速查找

### Agent 定义
- 太子 → [03_agent_definitions.md](03_agent_definitions.md#31-太子-agent)
- 中书省 → [03_agent_definitions.md](03_agent_definitions.md#32-中书省-agent)
- 门下省 → [03_agent_definitions.md](03_agent_definitions.md#33-门下省-agent)
- 尚书省 → [03_agent_definitions.md](03_agent_definitions.md#34-尚书省-agent)
- 早朝官 → [03_agent_definitions.md](03_agent_definitions.md#35-早朝官-agent)
- 吏部 → [03_agent_definitions.md](03_agent_definitions.md#36-吏部-agent)
- 户部 → [03_agent_definitions.md](03_agent_definitions.md#37-户部-agent)
- 礼部 → [03_agent_definitions.md](03_agent_definitions.md#38-礼部-agent)
- 兵部 → [03_agent_definitions.md](03_agent_definitions.md#39-兵部-agent)
- 刑部 → [03_agent_definitions.md](03_agent_definitions.md#310-刑部-agent)
- 工部 → [03_agent_definitions.md](03_agent_definitions.md#311-工部-agent)
- 御史台 → [03_agent_definitions.md](03_agent_definitions.md#312-御史台-agent)
- 皇城司 → [03_agent_definitions.md](03_agent_definitions.md#313-皇城司-agent)
- 发改委 → [03_agent_definitions.md](03_agent_definitions.md#314-发改委-agent)

### 工作流程
- 标准即时任务链 → [04_trigger_conditions.md](04_trigger_conditions.md#411-标准即时任务链)
- 国策议题链（延迟汇报）→ [04_trigger_conditions.md](04_trigger_conditions.md#413-国策议题链延迟汇报)
- 定时任务链 → [04_trigger_conditions.md](04_trigger_conditions.md#414-定时任务链)
- 盘前/盘中/盘后/周度流程 → [04_trigger_conditions.md](04_trigger_conditions.md#43-流程触发规则)
- 通信协议 → [05_communication_protocol.md](05_communication_protocol.md)
- 异常处理 → [06_exception_handling.md](06_exception_handling.md)

### 开发规范
- 目录结构 → [01_architecture.md](01_architecture.md#15-目录结构规范)
- 代码风格 → [02_code_style.md](02_code_style.md)
- 权限控制 → [07_permission_matrix.md](07_permission_matrix.md)
- 模板规范 → [08_template_spec.md](08_template_spec.md)

### 核心制度铁律
- 关键制度铁律 → [01_architecture.md](01_architecture.md#附录关键制度铁律)
- 铁律触发条件 → [04_trigger_conditions.md](04_trigger_conditions.md#44-关键制度铁律触发)
