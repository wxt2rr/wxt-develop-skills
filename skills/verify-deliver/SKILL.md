---
name: verify-deliver
description: Use when code or configuration changes are complete or nearly complete and the work needs proof of completion through requirement mapping, executed verification, residual risk reporting, and a clear delivery conclusion.
---

# 验证交付（防伪完成）

用于判断“是否真的完成”，而不是凭感觉收尾。核心要求是：结论必须由真实验证证据支撑。

## 目标

1. 把需求、改动和验证结果一一对上。  
2. 区分“已验证通过”“未验证但推测没问题”“明确存在风险”。  
3. 给出可交付结论，而不是泛泛说“应该可以”。  

## 适用场景

1. 代码、配置、脚本或文档改动已完成，准备收尾。  
2. 需要回答“改好了没有”“还剩什么风险”。  
3. 需要输出测试结果、手验结论和残余风险说明。  

## 执行流程

1. 建需求映射  
   - 把“需求点 -> 改动点 -> 验证点”串起来。  
   - 缺任一环都要明确指出。  
2. 跑真实验证  
   - 优先执行测试、构建、lint、类型检查、脚本或手工行为检查。  
   - 不把“理论上会过”当成验证结果。  
3. 核对主路径与边界  
   - 不只看 happy path。  
   - 至少点名未覆盖的边界或失败路径。  
4. 归档风险  
   - 写明还没验证的部分、环境限制、潜在兼容风险。  
   - 不夸大完成度。  
5. 给结论  
   - `通过 / 有条件通过 / 不通过`。  
   - 结论要和证据一致。  

## 输出模板

1. 结论  
2. 验证依据  
3. 需求映射  
4. 执行过的验证  
5. 未覆盖项  
6. 残余风险  
7. 建议下一步  

## 质量闸门

1. 没有真实验证证据，不能宣布完成。  
2. 需求映射有缺项，不能判定通过。  
3. 有残余风险时，必须说清影响范围，不做模糊安慰。  
4. 如果验证暴露问题，回退到 `implement-change` 修正，而不是硬交付。  
