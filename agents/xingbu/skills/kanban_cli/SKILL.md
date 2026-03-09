---
name: kanban_cli
description: 看板命令规范（统一使用 scripts/kanban_update.py）
version: 1.0.0
---

# kanban_cli

## 强制要求
- 一律使用 CLI 更新看板，不直接编辑 JSON。
- 进入任务、关键节点、完成/阻塞都要更新。

## 常用命令
```bash
cd __REPO_DIR__
python3 scripts/kanban_update.py state <id> <Todo|Doing|Blocked|Done> "<说明>"
python3 scripts/kanban_update.py flow <id> "<from>" "<to>" "<remark>"
python3 scripts/kanban_update.py progress <id> "<当前工作>" "<步骤1✅|步骤2🔄|步骤3>"
python3 scripts/kanban_update.py todo <id> <todo_id> "<title>" <status> --detail "<产出详情>"
```
