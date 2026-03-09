---
name: kanban_cli
description: 太子看板命令规范（含结案归档门禁）
version: 1.2.0
---

# kanban_cli（太子）

## 强制要求
- 一律使用 CLI 更新看板，不直接编辑 JSON。
- **未完成“向皇上主动复命（已实际发出消息）”前，禁止把 state 置为 `Done`。**

## 关键节点
1. 立项后：`state -> Doing`
2. 派发中书后：记录 flow
3. 收到中书回奏后：记录 flow + progress
4. 主动向皇上复命后：才允许 `state -> Done`

## 常用命令
```bash
cd __REPO_DIR__
python3 scripts/kanban_update.py state <id> <Todo|Doing|Blocked|Done> "<说明>"
python3 scripts/kanban_update.py flow <id> "<from>" "<to>" "<remark>"
python3 scripts/kanban_update.py progress <id> "<当前工作>" "<步骤1✅|步骤2🔄|步骤3>"
python3 scripts/kanban_update.py todo <id> <todo_id> "<title>" <status> --detail "<产出详情>"
```
