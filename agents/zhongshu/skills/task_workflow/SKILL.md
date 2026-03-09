---
name: task_workflow
description: 中书省任务闭环流程（基于 sessions_send 回传太子）
version: 1.3.0
---

# task_workflow（中书省）

## 目标
确保中书省完成完整闭环：**接收太子任务 → 门下审议 → 尚书执行 → 回传太子**。

## 强制流程
1. 接收太子任务，明确任务ID、目标、验收标准。
2. 起草执行方案并 `sessions_send(sessionKey="agent:menxia:main", ...)` 给门下省审议。
3. 门下准奏后，`sessions_send(sessionKey="agent:shangshu:main", ...)` 给尚书省执行。
4. 收到尚书省执行回奏后，整理结果与证据。
5. **必须 `sessions_send(sessionKey="agent:taizi:main", ...)` 回传太子**。

## 指定路由（必须显式 sessionKey）
- 门下省：`sessions_send(sessionKey="agent:menxia:main", ...)`
- 尚书省：`sessions_send(sessionKey="agent:shangshu:main", ...)`
- 太子：`sessions_send(sessionKey="agent:taizi:main", ...)`

## 禁止事项
- 禁止把中书当作 subagent 直接返回替代正式回传。
- 禁止在未向太子回传前将任务视为完成。
- 禁止跳过门下审议直接派尚书执行。
