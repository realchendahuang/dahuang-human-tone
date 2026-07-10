# Dahuang Human Tone

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Skill Version](https://img.shields.io/badge/Skill-v3.0.0-111827.svg)](CHANGELOG.md)
[![Language](https://img.shields.io/badge/Language-中文写作-e11d48.svg)](skills/dahuang-human-tone/SKILL.md)

> 中文优先的 Humanizer Skill。先保护事实、论点和作者声音，再按体裁修结构、句式和模板痕迹。

```bash
npx skills add realchendahuang/dahuang-human-tone -g
```

## 3.0 解决什么问题

很多去 AI 味方案停在词表替换：删“值得注意的是”，把长句切短，再加一点口语和第一人称。这样通常只是把一种模板换成另一种模板，还可能改坏技术含义、学术限定、营销 CTA 或小说伏笔。

Dahuang Human Tone 3.0 把去味改成一套完整的编辑系统：

| 模块 | 作用 |
|---|---|
| 编辑合同 | 先确定模式、强度、体裁、声纹和不可改变项 |
| 内容账本 | 锁定事实、引用、术语、论点、因果、时间线与叙事功能 |
| 五遍引擎 | 依次处理宏观结构、模板外壳、句子连接、作者声纹和最终回滚 |
| 体裁路由 | 技术、学术、法律、营销、社媒、公开写作和叙事分别处理 |
| 声纹校准 | 有作者样本时恢复作者自己的节奏，不套统一“自然口吻” |
| 回归用例 | 同时测试“应该改”和“应该不改”，防止去味过度 |

核心判断很简单：结构先于词汇，内容保护先于风格修改，作者声纹先于通用人味，体裁规则先于通用规则。

## 一分钟上手

默认使用标准强度：

```text
Use $dahuang-human-tone 把下面这段的 AI 味去掉，保留事实、观点和原有语气：

<粘贴文本>
```

彻底重构表达，但不改变内容：

```text
Use $dahuang-human-tone 深改下面这篇文章。可以重排结构，但先建立内容账本，保留全部事实、引用、论点和限定条件：

<粘贴文本>
```

只诊断，不改写：

```text
Use $dahuang-human-tone 诊断这段文字最明显的 AI 写作痕迹，合并重叠问题，先不要改：

<粘贴文本>
```

匹配作者自己的声音：

```text
Use $dahuang-human-tone 参考这些已发表样本的节奏和措辞，把草稿改得更像我。只迁移风格，不复制样本内容：

<作者样本>
<待改草稿>
```

## 三档强度

| 强度 | 适合场景 | 允许的改动 |
|---|---|---|
| 轻改 | 技术文档、聊天、已经比较自然的文本 | 只清理明显模板壳和协作痕迹 |
| 标准 | 博客、社媒、一般正式文本；默认 | 调整结构、句式和节奏，保留论证顺序 |
| 深改 | 用户明确要求彻底重写 | 可重排段落和重建表达，但必须逐项对回内容账本 |

已经自然、准确且符合场景的文本可以不改。去味不以 diff 数量衡量。

## 五遍编辑引擎

1. **宏观结构**：先处理大纲骨架、同构段落、重复总结和信息埋藏。
2. **去壳与具体性**：删掉不承载信息的路标、升华和假互动；只使用原文已有事实。
3. **句子与连接**：修同义循环、机械衔接和制造式节奏，保留有功能的列表、被动语态与标点。
4. **作者声纹**：优先匹配用户样本，其次保留原稿已有声音，最后才使用克制的体裁默认。
5. **验证与回滚**：核对内容账本、体裁和声纹；没有实质改善就停止，不无限迭代。

## 体裁路由

| 体裁 | 默认策略 | 重点保护 |
|---|---|---|
| 技术与产品文档 | 轻改或标准 | 代码、命令、版本号、稳定术语和可检索结构 |
| 学术与研究写作 | 标准 | 引用、数据、hedging、被动语态和非母语作者表达 |
| 法律、政策与正式报告 | 轻改 | 定义、条件、例外、责任主体和编号结构 |
| 营销与品牌文案 | 标准 | 已证实卖点、品牌声纹、CTA 和渠道格式 |
| 社媒与聊天 | 轻改或标准 | 平台语感、关系距离、口头禅和回复长度 |
| 博客、评论与公开写作 | 标准 | 作者判断、第一人称、复杂情绪和个人节奏 |
| 小说与叙事 | 标准 | 视角、时间线、人物声口、伏笔、钩子和情绪承接 |

## 改写示例

**处理前**

> 在当今快速发展的 AI 时代，值得注意的是，这不仅仅是一次技术升级，更是创作范式的根本性转变。深入探讨这一问题，我们会发现，真正的挑战不在于模型的能力，而在于人对内容的判断力。综上所述，AI 不是取代创作者，而是赋能创作者。让我们一起拥抱这个充满无限可能的未来。未来可期。你觉得呢？

**处理后**

> AI 在改变内容创作。模型能力不是这里的主要难题，人的判断才是：要知道工具的边界，学会和它协作，同时保留独立思考。它能帮助创作者，但做什么、发什么，最后仍要由人判断。

改写删掉了背景壳、宣布式导读、二分模板、宣传词和假互动，没有新增数据、经历或结论。

更多示例：

- [完整改写示例](skills/dahuang-human-tone/examples/before-after.md)
- [诊断示例](skills/dahuang-human-tone/examples/audit.md)
- [回归用例](skills/dahuang-human-tone/examples/regression-cases.md)

## 安装

### Skills CLI

```bash
# 全局安装，所有项目可用
npx skills add realchendahuang/dahuang-human-tone -g

# 只安装到当前项目
npx skills add realchendahuang/dahuang-human-tone
```

安装后重启 Agent。

### 手动安装

```bash
git clone https://github.com/realchendahuang/dahuang-human-tone.git

# Codex
cp -r dahuang-human-tone/skills/dahuang-human-tone ~/.codex/skills/

# Claude Code
cp -r dahuang-human-tone/skills/dahuang-human-tone ~/.claude/skills/
```

真正的 Skill 包位于 [`skills/dahuang-human-tone/`](skills/dahuang-human-tone/)。仓库根目录的 README、CHANGELOG 和调研文档不会进入 Agent 上下文。

## 仓库结构

```text
.
├── README.md
├── CHANGELOG.md
├── LICENSE
├── docs/
│   └── humanizer-landscape-2026-07.md
└── skills/
    └── dahuang-human-tone/
        ├── SKILL.md
        ├── agents/openai.yaml
        ├── examples/
        │   ├── audit.md
        │   ├── before-after.md
        │   └── regression-cases.md
        └── references/
            ├── genre-routing.md
            ├── voice-calibration.md
            ├── patterns.md
            ├── deep-tells.md
            ├── shape-audit.md
            ├── guardrails.md
            ├── soul.md
            └── sources.md
```

## 核心文档

- [Skill 入口与五遍工作流](skills/dahuang-human-tone/SKILL.md)
- [体裁路由](skills/dahuang-human-tone/references/genre-routing.md)
- [作者声纹校准](skills/dahuang-human-tone/references/voice-calibration.md)
- [AI 写作模式清单](skills/dahuang-human-tone/references/patterns.md)
- [中文长文的深层句式破绽](skills/dahuang-human-tone/references/deep-tells.md)
- [事实、术语与作者风格保护](skills/dahuang-human-tone/references/guardrails.md)
- [2026 Humanizer 生态调研](docs/humanizer-landscape-2026-07.md)

## 使用边界

- 改善表达，不判断作者身份、生成模型或文本来源。
- 不承诺绕过 GPTZero、Turnitin 等检测器。
- 不使用 AI 概率、伪精确总分、固定句长或词频阈值决定改写。
- 不擅自修改事实、引用、数据、结论、专业含义或作者立场。
- 不为了“像人”编造经历、情绪、错别字、数据和来源。

## 生态调研

3.0 对 Humanizer-zh、Humanizer、stop-slop、story-deslop、学术与营销垂直方案做了逐项比较。吸收了作者样本校准、draft → 自审 → final、体裁路由、改写强度和叙事保护；拒绝检测器绕过、伪精确评分、固定删减比例、标点禁令和虚构具体性。

完整取舍见 [Humanizer Skill 生态调研](docs/humanizer-landscape-2026-07.md)，方法来源见 [sources.md](skills/dahuang-human-tone/references/sources.md)。

## 相关项目

- [`dahuang-ai-tone`](https://github.com/realchendahuang/dahuang-ai-tone)：识别或模拟 GPT、Claude、Gemini、豆包等模型常见的表达风格。

## License

[MIT](LICENSE) © 2026 realchendahuang
