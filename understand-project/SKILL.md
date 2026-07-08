---
name: understand-project
description: Use when starting work in an unfamiliar project, module, page, class, or interface and needing to identify what it does, where the real entry points are, which files matter, and what evidence supports the conclusion before proposing changes or answers.
---

# 看懂项目（先立事实）

用于把“这个项目/模块到底是干什么的”快速落到可验证结论，避免一上来就猜架构、猜职责、猜改法。

## 目标

1. 先建立事实，再给判断。  
2. 快速找出入口、主链路、关键文件和本次任务相关范围。  
3. 输出可引用的依据，区分“看到的事实”和“基于事实的推断”。  

## 适用场景

1. 刚接手陌生仓库或陌生模块。  
2. 用户在问“这个项目做什么”“这个页面/类/接口是干啥的”。  
3. 真正改代码前，需要先定位入口、上下游、依赖关系和改动切入点。  

## 执行流程

1. 读项目根信息  
   - 先看目录结构、README、package manager 文件、主要配置、启动入口。  
   - 不跳过能直接说明项目用途的文件。  
2. 找运行与入口  
   - 找主进程、服务入口、路由入口、页面入口、CLI 入口或核心模块入口。  
   - 记录“用户请求如何走到这里”。  
3. 缩到目标范围  
   - 从用户问题反推相关模块、类、页面、接口、脚本。  
   - 列出本次任务真正相关的文件，不做全仓漫游。  
4. 画最小链路  
   - 说明“谁触发谁、数据怎么流、结果落在哪里”。  
   - 只画本次问题需要的链路，不追求全量架构图。  
5. 输出事实与推断  
   - 事实必须附文件依据。  
   - 推断必须明确标注，不允许伪装成已确认事实。  

## 输出模板

1. 结论  
2. 关键依据  
3. 主要模块与职责  
4. 相关文件  
5. 当前问题的切入点  
6. 事实 / 推断 / 待确认项  

## 质量闸门

1. 没看入口文件，不下总体判断。  
2. 没有文件证据，不下职责结论。  
3. 结论和推断必须分栏，不能混写。  
4. 如果已经能明确需求边界，下一阶段切到 `define-requirement`；如果连目标都不清，先把事实补齐。  
