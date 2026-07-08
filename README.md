# wxt-develop-skills

我把自己常见的需求开发过程拆成了一套 Codex Skills，用来约束 Agent 在真实项目里从“看懂现状”一路走到“验证交付”。

这套技能为了减少开发过程中几个反复出现的问题：没看懂项目就开始猜、需求边界没说清就设计、方案没锁契约就改代码、复杂任务没有计划就一路写到底、最后没有证据就说完成。

## 我的开发链路

我把完整需求开发拆成 5 个阶段：

1. `understand-project`：看懂项目  
   我先让 Agent 建立事实，找到项目入口、主链路、相关文件和当前问题的切入点，避免一上来凭经验猜。

2. `define-requirement`：明确需求  
   我要求 Agent 把目标、范围、非目标、约束和验收标准说清楚，尤其要把“用户真正要什么”和“顺手提出的实现方式”拆开。

3. `design-solution`：设计方案并锁契约  
   我希望 Agent 在动代码前给出唯一推荐方案，并锁定接口、参数、状态流转、兼容规则和验证矩阵。

4. `implement-change`：实现改动  
   我要求 Agent 按既定方案做最小闭环改动。复杂任务必须先在当前项目的 `.wxt/` 目录下写详细 todo，再完成一项更新一项。

5. `verify-deliver`：验证交付  
   我不接受“理论完成”。Agent 必须把需求、改动和验证证据对齐，再说明未覆盖项和残余风险。

## 目录

```text
wxt-develop-skills/
├── .codex-plugin/
│   └── plugin.json
└── skills/
    ├── understand-project/
    ├── define-requirement/
    ├── design-solution/
    ├── implement-change/
    └── verify-deliver/
```

我把这套仓库做成了带包级元数据的 Codex 插件结构。这样在 Codex 里展示时，可以按插件名作为前缀，而不是只显示裸 skill 名。

每个 skill 的核心说明都在 `skills/<skill-name>/SKILL.md` 里。

## 安装方式
### 默认
```bash
npx -y skills add wxt2rr/wxt-develop-skills
```

### Codex
```bash
npx -y skills add wxt2rr/wxt-develop-skills -a codex -g --all -y
```
