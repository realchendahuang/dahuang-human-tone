# Dahuang Human Tone Skill Package

> 中文文本去 AI 味与诊断 Skill。清理模板腔、路标词、升华收尾、假互动和段落同构，同时保护事实、术语、观点与作者风格。

[返回仓库首页](../../README.md)

## 能力

- **去味**：直接修改中文文本，优先调整组织方式和句式结构。
- **诊断**：只标出问题、归类 AI 痕迹并给出修改方向。
- **场景感知**：根据社媒、技术文档、正式报告、文章、小说或聊天控制改写力度。
- **误伤保护**：保留事实、数字、日期、引用、专有名词、术语、代码与明确立场。

## Skill 包结构

```text
dahuang-human-tone/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
├── examples/
│   ├── audit.md
│   └── before-after.md
└── references/
    ├── patterns.md
    ├── deep-tells.md
    ├── shape-audit.md
    ├── guardrails.md
    └── soul.md
```

`SKILL.md` 是模型入口。其余文档按任务需要加载，避免每次调用都塞入全部规则。

## 安装

### skills CLI

```bash
npx skills add realchendahuang/dahuang-human-tone -g
```

去掉 `-g` 可安装到当前项目。

### 手动安装

从仓库根目录执行：

```bash
# Codex
cp -r skills/dahuang-human-tone ~/.codex/skills/

# Claude Code
cp -r skills/dahuang-human-tone ~/.claude/skills/
```

## 使用

### 去味

```text
Use $dahuang-human-tone 把下面这段的 AI 味去掉，保留事实、观点和原有语气：

<粘贴文本>
```

### 只诊断

```text
Use $dahuang-human-tone 先标出这段文字里的 AI 味，说明原因和修改方向，暂时不要改写：

<粘贴文本>
```

### 控制场景

```text
Use $dahuang-human-tone 这是技术文档，只清理协作腔、路标词和结构重复，保持中性表达：

<粘贴文本>
```

## 文档导航

| 文档 | 用途 |
|---|---|
| [`SKILL.md`](SKILL.md) | 入口、触发场景与完整工作流 |
| [`references/patterns.md`](references/patterns.md) | 词汇、句式、结构、格式和交流层问题 |
| [`references/deep-tells.md`](references/deep-tells.md) | 中文长文和论说文中的深层句式破绽 |
| [`references/shape-audit.md`](references/shape-audit.md) | 段落同构、节奏和格式密度检查 |
| [`references/guardrails.md`](references/guardrails.md) | 误伤防护与应保留内容 |
| [`references/soul.md`](references/soul.md) | 公开写作中的作者声音与节奏 |
| [`examples/before-after.md`](examples/before-after.md) | 完整改写示例 |
| [`examples/audit.md`](examples/audit.md) | 诊断模式示例 |

## 边界

- 改善文字的阅读感，不鉴定内容来源。
- 不承诺通过任何 AI 检测器。
- 不编造个人经历、故事、情绪和观点。
- 不擅自改变事实、数据、结论和术语。
- 中性文本保持中性，不强行口语化。

## 参考来源

本 Skill 吸收并重新整理了以下项目中的公开方法和经验：

- [blader/humanizer](https://github.com/blader/humanizer)
- [op7418/Humanizer-zh](https://github.com/op7418/Humanizer-zh)
- [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop)
- [B1lli/remove-ai-flavor-writing-skill](https://github.com/B1lli/remove-ai-flavor-writing-skill)
- [shyuan/writing-humanizer](https://github.com/shyuan/writing-humanizer)
- [kevintsai1202/Humanizer-zh-TW](https://github.com/kevintsai1202/Humanizer-zh-TW)
- [OUBIGFA/De-AI-Prompt-Enhancer-Writer-Booster-SKILL](https://github.com/OUBIGFA/De-AI-Prompt-Enhancer-Writer-Booster-SKILL)
- [MrGeDiao/shuorenhua](https://github.com/MrGeDiao/shuorenhua)
- [hylarucoder/ai-flavor-remover](https://github.com/hylarucoder/ai-flavor-remover)
- [Hello-SimpleAI/chatgpt-comparison-detection](https://github.com/Hello-SimpleAI/chatgpt-comparison-detection)
- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)

## License

MIT