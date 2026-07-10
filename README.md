# Dahuang Human Tone

> 一个面向中文写作的 AI Skill：清理模板腔、路标词、升华收尾和假互动，让文字更自然，同时保留事实、观点、术语和作者原有的表达力度。

## 这个项目解决什么问题

很多 AI 文本的问题不在信息错误，而在表达方式过于规律：开头先铺背景，中间不断使用“值得注意的是”“深入探讨”，结尾再升华一次，最后补一句“你觉得呢？”。

Dahuang Human Tone 会先判断文本场景，再以最小改写方式清理这些痕迹。它不会机械替换同义词，也不会为了追求所谓“人味”擅自编造经历、情绪或观点。

它支持两类任务：

- **去味**：直接把中文文本改得更自然。
- **诊断**：只指出 AI 味出现在哪里，以及为什么有问题，暂不改写。

## 效果示例

**处理前**

> 在当今快速发展的 AI 时代，值得注意的是，这不仅仅是一次技术升级，更是创作范式的根本性转变。深入探讨这一问题，我们会发现，真正的挑战不在于模型的能力，而在于人对内容的判断力。综上所述，AI 不是取代创作者，而是赋能创作者。让我们一起拥抱这个充满无限可能的未来。未来可期。你觉得呢？

**处理后**

> AI 在改内容创作的方式，没什么悬念。有意思的是，挑战在人的判断力这边，不在模型能力——技术就是工具，工具会越来越好。AI 不会取代创作者，但会用 AI 的会取代不用的。具体怎么分，现在还说不好。

更多示例：

- [完整改写示例](skills/dahuang-human-tone/examples/before-after.md)
- [AI 味诊断示例](skills/dahuang-human-tone/examples/audit.md)

## 安装

### 使用 skills CLI

```bash
npx skills add realchendahuang/dahuang-human-tone -g
```

`-g` 表示安装到用户级目录，所有项目均可使用。去掉 `-g` 则只安装到当前项目。

安装完成后，重启 Codex、Claude Code 或其他支持 Skills 的 Agent。

### 手动安装

克隆仓库后，复制真正的 skill 目录：

```bash
git clone https://github.com/realchendahuang/dahuang-human-tone.git

# Codex
cp -r dahuang-human-tone/skills/dahuang-human-tone ~/.codex/skills/

# Claude Code
cp -r dahuang-human-tone/skills/dahuang-human-tone ~/.claude/skills/
```

## 使用方式

### 直接去除 AI 味

```text
Use $dahuang-human-tone 把下面这段的 AI 味去掉：

<粘贴文本>
```

### 保留特定场景风格

```text
Use $dahuang-human-tone 这是技术文档，只删协作腔和路标词，不要注入个人化表达：

<粘贴文本>
```

### 只诊断，暂不改写

```text
Use $dahuang-human-tone 先别改，标出这段文字里的 AI 味，并解释原因：

<粘贴文本>
```

## 工作方式

这个 skill 会依次完成：

1. 判断文本属于社媒、技术文档、文章、学术文本、小说还是聊天。
2. 保护事实、数字、术语、引用和作者明确表达的立场。
3. 检查词汇、句式、结构、格式和交流方式中的 AI 痕迹。
4. 优先局部修改，避免无必要的整段重写。
5. 自审一次残留的模板痕迹和段落同构。
6. 检查是否因“去味”过度而把文字改得平庸。

## 仓库结构

```text
.
├── README.md
└── skills/
    └── dahuang-human-tone/
        ├── SKILL.md
        ├── README.md
        ├── agents/
        │   └── openai.yaml
        ├── examples/
        │   ├── audit.md
        │   └── before-after.md
        └── references/
            ├── deep-tells.md
            ├── guardrails.md
            ├── patterns.md
            ├── shape-audit.md
            └── soul.md
```

Skill 放在 `skills/dahuang-human-tone/` 下是有意设计。当前 `skills CLI` 在处理仓库根目录中的单个 `SKILL.md` 时，可能只安装入口文件，遗漏 `references` 和 `examples`。使用子目录结构可以确保整个 skill 被完整复制。

## 文档入口

- [Skill 主文件](skills/dahuang-human-tone/SKILL.md)
- [AI 味模式清单](skills/dahuang-human-tone/references/patterns.md)
- [深层句式破绽](skills/dahuang-human-tone/references/deep-tells.md)
- [结构与形状审计](skills/dahuang-human-tone/references/shape-audit.md)
- [误伤防护](skills/dahuang-human-tone/references/guardrails.md)
- [公开写作中的人味注入](skills/dahuang-human-tone/references/soul.md)

## 使用边界

- 它用于改善表达，不用于断言一段文字由哪个模型生成。
- 它不承诺绕过 AI 检测器。
- 它不会擅自改动事实、数据、结论或作者立场。
- 它不会凭空添加个人经历、情绪、笑话或故事。
- 技术文档等中性场景不会被强行改成口语或社媒风格。

## 相关项目

- [`dahuang-ai-tone`](https://github.com/realchendahuang/dahuang-ai-tone)：添加或识别 GPT、Claude、Gemini、豆包等模型常见的表达风格。

## 致谢

本项目参考了 Humanizer、Humanizer-zh、stop-slop、writing-humanizer、shuorenhua 等项目的公开方法和经验。完整来源说明见 [skill 内 README](skills/dahuang-human-tone/README.md#参考)。
