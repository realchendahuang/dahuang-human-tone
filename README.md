# Dahuang Human Tone

> 去除中文文本里的 AI 味——删模板壳、删路标词、删升华收尾、删假互动，把文本从"像模型在表演写作"拉回"像具体人在说话"。

## 它能做什么

这个 skill 给 AI 编码助手装上去 AI 味（把 AI 味清洗掉）的能力：

1. **去味**（主）——把一段中文文本里的 AI 味清洗掉。删的是模板句式、路标词、升华收尾、假互动——不是堆替换词。保的是信息、事实、立场、术语、作者锋利。
2. **诊断**（次）——只标问题不改。指出 AI 味在哪、是什么味、建议怎么改。

**姐妹 skill**：[`dahuang-ai-tone`](https://github.com/realchendahuang/dahuang-ai-tone)——把文本加成 GPT/Claude/Gemini/豆包的味，或者检测 AI 味在哪、像哪个风格。

## 看看效果

同一段 AI 味文本，去味前后：

> **改前**：在当今快速发展的 AI 时代，值得注意的是，这不仅仅是一次技术升级，更是创作范式的根本性转变。深入探讨这一问题，我们会发现，真正的挑战不在于模型的能力，而在于人对内容的判断力。综上所述，AI 不是取代创作者，而是赋能创作者。让我们一起拥抱这个充满无限可能的未来。未来可期。你觉得呢？

**改后**：AI 在改内容创作的方式，没什么悬念。有意思的是，挑战在人的判断力这边，不在模型能力——技术就是工具，工具会越来越好。AI 不会取代创作者，但会用 AI 的会取代不用的。具体怎么分，现在还说不好。

完整示范见 `examples/before-after.md`。

## 去味工作流

1. **判场景**——公开文/社媒/技术文/学术/小说/聊天，场景决定力度
2. **划保护线**——事实/数字/术语/引文/行话不动
3. **扫味**——五层（词汇/句式/结构/格式/交流）+ 深层句式 + 形状审计
4. **删壳保信息**——最小改写，能局部改就不整段重写，不做同义词替换
5. **两遍**——初稿 → 自审"哪里还像 AI" → 终稿
6. **注入人味**——仅公开文/社媒/小说，加观点/变节奏/承认复杂性
7. **出厂自检**——机械检查残留口癖和形状
8. **平庸化回滚**——去味过度就回滚，宁可保留锋利也不要无菌

## 资源结构

```
dahuang-human-tone/
├── SKILL.md                  # 入口：去味工作流（给模型读）
├── references/               # 按需加载的详细文档
│   ├── patterns.md           # AI 味完整清单（五层 45 项）
│   ├── deep-tells.md         # 深层句式破绽（中文长文/论说文）
│   ├── shape-audit.md        # 形状审计（可量化的结构信号）
│   ├── guardrails.md         # 误伤防护 + 宾语判别 + 人类特征保留
│   └── soul.md               # 注入人味（公开文/社媒/小说场景）
├── examples/                 # 改写示范、诊断示范
│   ├── before-after.md
│   └── audit.md
└── agents/openai.yaml        # Codex 专属 UI 元数据（可选）
```

## 安装

### 方式一：skills CLI（推荐）

```bash
npx skills add realchendahuang/dahuang-human-tone -g
```

`-g` 安装到全局（用户级），所有项目可用。去掉 `-g` 则只装到当前项目。安装后重启 Codex / Claude Code 即可生效。

### 方式二：手动复制

```bash
# Codex
cp -r dahuang-human-tone ~/.codex/skills/

# Claude Code
cp -r dahuang-human-tone ~/.claude/skills/
```

或者把本目录作为资源目录，在 system prompt 里引用 `SKILL.md` 路径。

## 使用

### 去味：把文本里的 AI 味清洗掉

```
Use $dahuang-human-tone 把下面这段的 AI 味去掉：

<贴文本>
```

```
Use $dahuang-human-tone 这段太像 AI 写的了，改自然点，是公号文所以要有作者声音：

<贴文本>
```

```
Use $dahuang-human-tone 这是技术文档，只删协作腔和路标词，别注入人味：

<贴文本>
```

### 诊断：只标问题不改

```
Use $dahuang-human-tone 先别改，先标出这段的 AI 味在哪：

<贴文本>
```

## 边界

- 这是去 AI 味，不是鉴定 AI 来源——不能说"这段一定是某模型生成的"
- 不承诺通过检测器——AI 检测工具本身不准，去味的目的是让文本读起来像人写的
- 不编造"人味"——不硬塞个人经历、轶事、笑话
- 不改变事实和立场——只改表达方式，不改观点、结论、数据
- 场景决定力度——技术文档不需要"人味"，中性就是对的

## 参考

本 skill 汲取了以下项目的精华：

- [blader/humanizer](https://github.com/blader/humanizer) — 英文 Humanizer 元老，两遍 draft→audit→final 工作流、误伤防护、集群原则
- [op7418/Humanizer-zh](https://github.com/op7418/Humanizer-zh) — 中文汉化版，个性与灵魂框架
- [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop) — 规则库三层拆分（词汇/结构/范例）
- [B1lli/remove-ai-flavor-writing-skill](https://github.com/B1lli/remove-ai-flavor-writing-skill) — 形状审计、段落同构检测、冒号模板量化
- [shyuan/writing-humanizer](https://github.com/shyuan/writing-humanizer) — 中文论说文专属破绽（升华训诫/金句叠句/路线回指）
- [shyuan/Humanizer-zh-TW](https://github.com/kevintsai1202/Humanizer-zh-TW) — 繁中版
- [OUBIGFA/De-AI-Prompt-Enhancer-Writer-Booster-SKILL](https://github.com/OUBIGFA/De-AI-Prompt-Enhancer-Writer-Booster-SKILL) — 深层句式破绽分析、保风格删路标、平庸化回滚
- [MrGeDiao/shuorenhua](https://github.com/MrGeDiao/shuorenhua) — 场景感知、宾语判别、变体归并
- [hylarucoder/ai-flavor-remover](https://github.com/hylarucoder/ai-flavor-remover) — 推理模型去味 prompt
- [Hello-SimpleAI/chatgpt-comparison-detection](https://github.com/Hello-SimpleAI/chatgpt-comparison-detection) — HC3 中文 AI 文本检测基准，经验信号
- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) — 所有去 AI 味 skill 的底层圣经
