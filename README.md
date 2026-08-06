# task-dispatch · 任务分拣器 🧭

> 让 AI 助手知道任务的轻重缓急：小事直接做，大事按流程走，没想清楚的先聊明白。

用 AI 干活，最烦两种事：改个标题它问东问西 😤，做个网站它又闷头乱干 😵。task-dispatch 让助手自行判断——**你只管说要什么，它自己掂量该咋干。**

## ✨ 它解决什么

mattpocock/skills（GitHub 20 万 star）把工程流程拆成了模块化 skill：grill-with-docs 对齐需求、to-spec 落规格、to-tickets 拆任务。它很好，但有个门槛：**你得自己知道什么情况该调哪个 skill。**

task-dispatch 在它前面加了一层自动判断。底层流程是 Matt 那套，判档这一层是它没有的。

## 🎯 四档判断

| 任务 | 走法 |
|---|---|
| 🔧 改个小地方 | 直接做，一句复述确认，零流程语言 |
| 📄 写一份东西 | 意图层问题最多 3 个（建议+确认式问法），先出骨架再细化 |
| 🏗️ 建一整套 | 路径清晰走完整流程；路径模糊建地图；涉界面先出原型 |
| 💭 还没想清楚 | 纯对话模式，只聊不建物，方向出来再转正式规划 |

## 🧠 核心设计

- ⚖️ **意图层必问，实现层默认值**：方向、目标、硬约束一定对齐；风格、比例这些能改的细节自己定
- 🛡️ **事实绝不编造**：数据、名称、价格这类只有用户知道的信息，查不到就标"待补"，不编
- 🎮 **三句话逃生通道**：随时说"直接做 / 先拷问下我 / 走完整流程"，判档立即让位
- 🧩 **依赖自检**：没有安装任何 mattpocock skill 也能独立工作，有则用完整流程
- 📋 **任务档案**：完成的任务记入 tasks.md，跨会话可回溯，中断任务留痕

## 📦 安装

### Claude Code 等支持 skills 的 agent

```bash
npx skills@latest add mattpocock/skills   # 先装底层流程 skill（可选但推荐）
```

然后把 `skills/task-dispatch/` 复制到项目的 `.claude/skills/` 下。

### HanaAgent

用 install_skill 安装 `skills/task-dispatch` 目录，或让助手安装。

### 其他支持 skills 的 agent

把 `skills/task-dispatch/` 复制到对应 agent 的 skills 目录即可（安装方式与 Claude Code 类似，或直接用 `npx skills add` 安装）。

### 完整包

20 件套完整包（含全部依赖 skill）可在 [Releases](https://github.com/aizinan/task-dispatch/releases) 下载。

## 🚀 怎么用

你不需要记任何东西，正常说需求即可：

- 🔤 "帮我把这篇文案的标题改一下" → 直接改
- 📝 "帮我写一份工作总结" → 先问一两个关键问题，出骨架再填充
- 🏢 "帮我们公司搭建一个客户管理系统" → 拆成小任务一步步来
- 💡 "我想做个 AI 相关的东西，还没想清楚" → 先聊，把方向聊出来

判断错了也不怕：一句"直接做"或"走完整流程"，它马上听你的。

## 🔗 依赖与来源

底层流程基于 [mattpocock/skills](https://github.com/mattpocock/skills)（MIT License）。本仓库只包含 task-dispatch 本体，判档层为原创。

## 🧪 测试

判档逻辑经过三轮测试迭代：10 个模拟用户、50 个单轮回归用例（正例 30 / 反例 12 / 交互 8）、4 个多轮完整执行链场景，全部有独立评审。测试集与结果见 [docs/](https://github.com/aizinan/task-dispatch/tree/master/docs)。

## 📄 License

MIT
