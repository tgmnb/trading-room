---
name: task_workflow
description: 中书省任务闭环流程（含向太子回传）
version: 1.2.0
---

# task_workflow（中书省）

## 目标
确保中书省完成完整闭环：**接收太子任务 → 门下审议 → 尚书执行 → 回传太子**。

## 强制流程
1. 接收太子任务，明确任务ID、目标、验收标准。
2. 起草执行方案并 `sessions_send` 给门下省审议。
3. 门下准奏后，`sessions_send` 给尚书省执行。
4. 收到尚书省执行回奏后，整理结果与证据。
5. 向太子回传（必须二选一且仅一条主路径）：
   - **subagent 模式（优先）**：若当前由太子调用，直接返回结果文本给调用方，不再额外 `sessions_send`。
   - **独立会话模式**：使用 `sessions_send(sessionKey="agent:taizi:main", ...)` 显式回传。

## 指定路由（必须显式 sessionKey）
- 门下省：`sessions_send(sessionKey="agent:menxia:main", ...)`
- 尚书省：`sessions_send(sessionKey="agent:shangshu:main", ...)`
- 太子（仅独立会话模式）：`sessions_send(sessionKey="agent:taizi:main", ...)`

## 禁止事项
- 禁止在未向太子回传前将任务视为完成。
- 禁止跳过门下审议直接派尚书执行。
- 禁止同时“直接返回 + sessions_send”造成重复回传。
