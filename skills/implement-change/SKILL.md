---
name: implement-change
description: Use when the requirement and solution are already decided and the work is ready for implementation, especially when changes span multiple classes or modules, large code areas, or multiple subsystems and need plan-driven execution with stepwise verification.
---

# 实现改动（最小闭环）

用于把已确认的需求和方案落成代码改动。简单任务走最小切片，复杂任务强制进入 `.wxt` 计划驱动模式。

## 目标

1. 按既定方案推进，不在实现阶段重新发散。  
2. 最小化改动面，优先复用现有结构和约定。  
3. 每个实施切片完成后立刻验证，不攒到最后一起赌。  
4. 复杂任务必须先落地详细 todo，再按 todo 推进和回写状态。  

## 适用场景

1. 需求和方案都已明确，可以直接进入代码落地。  
2. 本次改动有清晰文件范围、模块范围或接口范围。  
3. 用户要的是交付结果，不是继续讨论备选路线。  

## 执行流程

1. 先判断复杂度  
   - 命中任一条件，视为复杂任务：  
     - 预计涉及 `>= 4` 个类或模块。  
     - 预计新增/修改/删除代码合计 `>= 150` 行。  
     - 预计跨 `>= 3` 个目录、子系统或独立职责区域。  
   - 复杂度不明时，默认按复杂任务处理。  
2. 复杂任务先建 `.wxt` todo  
   - 在当前项目根目录下创建或更新 `.wxt/<模块>-<本次需求>.md`。  
   - 若 `.wxt/` 不存在，先创建目录。  
   - 文件名必须体现“改动归属模块 + 本次需求主题”，禁止使用 `todo.md`、`plan.md`、`implement-change-todo.md` 这类通用名。  
   - 模块名用当前任务最主要的业务模块、页面、服务、子系统或能力名；需求名用本次任务的最小可识别主题。  
   - 在改生产代码前，把目标、范围、切片、验证方式写进去。  
3. 先列改动点  
   - 写明会改哪些文件、哪些模块、哪些行为。  
   - 如果文件影响面还不清，退回 `understand-project` 或 `design-solution`。  
4. 按切片实现  
   - 一次只推进一个最小切片。  
   - 不把无关重构、顺手优化、风格清理混入本次任务。  
5. 保持兼容  
   - 有旧行为时，先判断是否必须兼容。  
   - 破坏旧契约必须与方案保持一致。  
6. 每步即验  
   - 每个切片完成后立刻跑对应验证。  
   - 验不过，不进入下一个切片。  
7. 回写 todo 与阻塞  
   - 复杂任务每完成一项，立刻更新对应的 `.wxt/<模块>-<本次需求>.md` 中的状态、验证结果和下一项。  
   - 发现新切片、新风险或范围变化时，先更新 todo，再继续写代码。  
8. 记录阻塞  
   - 发现新事实冲击原方案时，不强推，及时回退到前一阶段。  

## 复杂任务 Todo 模式

复杂任务必须使用如下最小模板：

```md
# <模块>-<本次需求>

## Goal
- 本次目标：

## Why Complex
- 命中的复杂条件：

## Scope
- 相关模块/类：
- 相关文件：
- 兼容要求：

## Task List
| ID | Task | Files/Modules | Verify | Status | Evidence |
| --- | --- | --- | --- | --- | --- |
| 1 |  |  |  | todo |  |

## Rules
- 同时只能有一个 `in_progress`
- 每完成一项立刻更新 `Status` 和 `Evidence`
- 新增任务先补表，再继续实现
```

命名示例：

- `.wxt/payment-retry-policy.md`
- `.wxt/aigc-video-add-multi-shot.md`
- `.wxt/chat-session-fix-scroll-jump.md`
- `.wxt/homepage-adjust-sidebar-layout.md`

## 输出模板

1. 当前实施目标  
2. 改动范围  
3. 当前切片  
4. 已完成项与验证证据  
5. 进行中项  
6. 阻塞与处理动作  
7. 下一步  

## 质量闸门

1. 方案未定，不进入实现。  
2. 一次只允许一个主切片处于进行中。  
3. 没有验证证据的改动，不能标记完成。  
4. 若发现新需求混入，先拆出去，不在实现阶段偷偷扩 scope。  
5. 复杂任务未创建符合命名规范的 `.wxt/<模块>-<本次需求>.md`，不得开始改生产代码。  
6. 复杂任务若 todo 未持续更新，不得宣称“已完成”。  
