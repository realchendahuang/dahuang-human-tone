# Dahuang Human Tone

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Skill Version](https://img.shields.io/badge/Skill-v2.0.0-111827.svg)](CHANGELOG.md)
[![Language](https://img.shields.io/badge/Language-中文写作-e11d48.svg)](skills/dahuang-human-tone/SKILL.md)

> 中文去 AI 味 Skill。清理模板腔、路标词、升华收尾、假互动和段落同构，同时保留事实、观点、术语与作者原有的表达力度。

```bash
npx skills add realchendahuang/dahuang-human-tone -g
```

## 为什么做这个 Skill

很多中文 AI 文本的信息没有问题，读起来却很像模型在执行一套固定写作流程：先铺背景，再分点解释，接着拔高意义，最后补一句互动。

Dahuang Human Tone 会先判断文本场景，再做最小范围的改写。它优先调整信息的组织方式，减少机械同义词替换，也不会凭空编造经历、情绪和立场。

它只做写作诊断，不判断文本是否由 AI 或某个模型生成；段落长度、句式和词频只作为复查线索，不作为检测结论。

## 一分钟上手

安装后，在 Codex、Claude Code 或其他支持 Skills 的 Agent 中直接调用：

```text
Use $dahuang-human-tone 把下面这段的 AI 味去掉，保留原有观点和语气：

<粘贴文本>
```

只做诊断，暂时不修改：

```text
Use $dahuang-human-tone 先标出这段文字里的 AI 味，说明问题和修改方向，先不要改写：

<粘贴文本>
```

## 它会处理什么

| 常见问题 | 处理方式 |
|---|---|
| “值得注意的是”“深入探讨”等路标词 | 删除无信息量的引导，直接进入内容 |
| “不是 A，而是 B”等高频模板句式 | 拆掉模板外壳，保留真正有用的信息 |
| 段落长度、句式和标题高度同构 | 调整节奏，让结构贴合内容 |
| 结尾突然升华、喊口号、假互动 | 收在具体事实、判断或自然余味上 |
| 技术文档被强行改成口语 | 根据场景控制力度，中性表达保持中性 |
| 为了“人味”添加虚构经历 | 禁止编造，作者没有说过的内容不补 |

## 改写示例

**处理前**

> 在当今快速发展的 AI 时代，值得注意的是，这不仅仅是一次技术升级，更是创作范式的根本性转变。深入探讨这一问题，我们会发现，真正的挑战不在于模型的能力，而在于人对内容的判断力。综上所述，AI 不是取代创作者，而是赋能创作者。让我们一起拥抱这个充满无限可能的未来。未来可期。你觉得呢？

**处理后**

> AI 在改内容创作的方式，没什么悬念。有意思的是，挑战在人的判断力这边，不在模型能力——技术就是工具，工具会越来越好。AI 不会取代创作者，但会用 AI 的会取代不用的。具体怎么分，现在还说不好。

更多示例：

- [完整改写示例](skills/dahuang-human-tone/examples/before-after.md)
- [AI 味诊断示例](skills/dahuang-human-tone/examples/audit.md)

## 两种工作模式

### 去味模式

直接修改文本。默认保护事实、数字、术语、引用、代码、观点和作者有意保留的表达。

### 诊断模式

只标出问题，说明属于哪一类 AI 痕迹，并给出修改方向。适合在正式改稿前做审计。

## 场景感知

同一个表达，在不同场景里的处理力度不同：

| 场景 | 默认策略 |
|---|---|
| 公众号、博客、专栏 | 保留作者声音，调整结构和节奏 |
| 小红书、微博、朋友圈 | 更短、更直接，避免改成说明书 |
| 技术文档、教程 | 最小改写，只清理协作腔和路标词 |
| 学术文本、正式报告 | 保持严谨，清理宣传腔和假互动 |
| 小说、故事 | 保留画面、语气和叙事节奏 |
| 聊天回复 | 删除谄媚腔、复述和多余收尾 |

## 工作原则

1. **先判场景**：表达是否自然，要结合它出现的位置判断。
2. **先划保护线**：事实、数字、日期、引用、术语、代码和明确立场不动。
3. **优先局部修改**：能改一句就不重写一段，能删掉外壳就不扩写内容。
4. **检查结构痕迹**：同时检查词汇、句式、段落形状、格式和交流方式。
5. **做第二遍自审**：检查残留模板和去味过度，避免把文字磨平。

## 安装

### skills CLI

```bash
# 全局安装，所有项目可用
npx skills add realchendahuang/dahuang-human-tone -g

# 只安装到当前项目
npx skills add realchendahuang/dahuang-human-tone
```

安装完成后重启 Agent。

### 手动安装

```bash
git clone https://github.com/realchendahuang/dahuang-human-tone.git

# Codex
cp -r dahuang-human-tone/skills/dahuang-human-tone ~/.codex/skills/

# Claude Code
cp -r dahuang-human-tone/skills/dahuang-human-tone ~/.claude/skills/
```

真正的 Skill 包位于 [`skills/dahuang-human-tone/`](skills/dahuang-human-tone/)。使用子目录结构可以让 skills CLI 连同 `references`、`examples` 和 Agent 元数据一起完整安装。

## 仓库结构

```text
.
├── README.md
├── LICENSE
├── CHANGELOG.md
└── skills/
    └── dahuang-human-tone/
        ├── SKILL.md
        ├── agents/openai.yaml
        ├── examples/
        │   ├── audit.md
        │   └── before-after.md
        └── references/
            ├── patterns.md
            ├── deep-tells.md
            ├── shape-audit.md
            ├── guardrails.md
            ├── soul.md
            └── sources.md
```

## 核心文档

- [Skill 入口与完整工作流](skills/dahuang-human-tone/SKILL.md)
- [AI 味模式清单](skills/dahuang-human-tone/references/patterns.md)
- [中文长文的深层句式破绽](skills/dahuang-human-tone/references/deep-tells.md)
- [段落同构与结构形状审计](skills/dahuang-human-tone/references/shape-audit.md)
- [事实、术语与作者风格保护](skills/dahuang-human-tone/references/guardrails.md)
- [公开写作中的作者声音](skills/dahuang-human-tone/references/soul.md)

## 使用边界

- 用于改善表达，不用于断言文字由哪个模型生成。
- 不承诺绕过 AI 检测器。
- 不擅自修改事实、数据、结论和作者立场。
- 不凭空添加个人经历、情绪、笑话和故事。
- 技术文档等中性场景不会被强行改成口语风格。

## 相关项目

- [`dahuang-ai-tone`](https://github.com/realchendahuang/dahuang-ai-tone)：识别或模拟 GPT、Claude、Gemini、豆包等模型常见的表达风格。

## License

[MIT](LICENSE) © 2026 realchendahuang

## 致谢

本项目吸收了 Humanizer、Humanizer-zh、stop-slop、writing-humanizer、shuorenhua 等开源项目的公开方法和经验。完整来源见 [方法来源](skills/dahuang-human-tone/references/sources.md)。
