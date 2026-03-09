---
name: task_workflow
description: 门下省审议流程（含必须回传中书省）
version: 1.1.0
---

# task_workflow（门下省）

## 目标
确保门下省审议形成闭环：**接收中书方案 → 审议结论 → 回传中书省**，并在准奏时同步尚书省进入执行。

## 强制流程
1. 接收中书省审议请求，核对任务ID、目标、验收标准。
2. 执行审议：检查方案完整性、风险、依赖与边界合规。
3. 形成结论：`准奏` 或 `封驳`，并给出理由与修改条件。
4. **必须 `sessions_send` 回传中书省主会话**，禁止只在本地输出不回传。
5. 若为准奏，**可并行 `sessions_send` 尚书省主会话**，附执行前提与边界。

## 指定路由（必须显式 sessionKey）
- 回传中书省：`sessions_send(sessionKey="agent:zhongshu:main", ...)`
- 准奏同步尚书省：`sessions_send(sessionKey="agent:shangshu:main", ...)`

## 输出结构
1. 任务ID
2. 审议结论（准奏/封驳）
3. 审议依据（关键证据）
4. 风险与限制条件
5. 后续动作（中书修订项或尚书执行前提）

## 禁止事项
- 禁止绕过中书省直接把“审议结果”当最终结果交付。
- 禁止隐式路由、禁止 generic spawn。
