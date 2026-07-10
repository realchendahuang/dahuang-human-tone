# Humanizer Skill 生态调研

调研日期：2026-07-10。

数据来自 Skills CLI 搜索结果和 GitHub 公开仓库。安装量、Star 与仓库活跃度会变化，只用于判断生态位置，不代表方法质量。

## 头部与代表性方案

| 项目 | Skills 安装量 | GitHub Star | 值得吸收 | 不采用 |
|---|---:|---:|---|---|
| [op7418/Humanizer-zh](https://github.com/op7418/Humanizer-zh) | 37.1K | 12.9K | 中文模式覆盖、个性与灵魂、完整示例 | 484 行单文件、伪精确评分、部分英文规则直译 |
| [blader/humanizer](https://github.com/blader/humanizer) | 2K | 28.5K | 作者样本校准、false positive、draft→自审→final、最新结构模式 | 一律禁破折号等绝对规则，不适合直接迁到中文 |
| [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop) | 6.8K | 13.6K | 相信读者、具体主语、具体事实、极简工作流 | 禁副词/被动/破折号、50 分评分 |
| [worldwonderer/story-deslop](https://github.com/worldwonderer/oh-story-claudecode) | 7.8K | 3.9K | 保护剧情功能、角色声口、伏笔、白名单和需复核机制 | 固定词频、删减比例、标点禁令和伪量化 Gate |
| [humanizerai/agent-skills](https://github.com/humanizerai/agent-skills) | 3K | 33 | 强度参数和 API 错误处理 | 检测器绕过、外部付费 API 和信用额度绑定 |
| [zc277584121/marketing-skills](https://github.com/zc277584121/marketing-skills) | 2.2K | 0 | 轻/中/完整重写强度 | 来源信誉弱、默认重改、脚本扫描优先 |
| [momo2young/humanize-academic-writing](https://github.com/momo2young/humanize-academic-writing) | 1.3K | 15 | 学术诚信、学科语域、非母语作者保护、保留 hedging | AI 概率脚本、固定指标、可能诱导补不存在的引用 |
| [jpeggdev/humanize-writing](https://github.com/jpeggdev/humanize-writing) | 927 | 33 | 结构先于词汇、八步编辑、朗读测试、重叠问题合并 | 规则过长、部分硬阈值与演示中的新增事实风险 |

另外检查了 humanizer-cn、writing-humanizer-zh、humanizer-zh-tw、小说与营销垂直变体。多数是头部 Humanizer 的翻译、裁剪或体裁化版本，适合验证共识，不适合作为新的真相源。

## 市面方案的共同盲点

### 1. 把去味当成词表替换

很多方案能列几十种 AI 词，却没有先处理文章骨架。结果只是换词后的同一份 AI 结构。

### 2. 把自然写作做成另一套模板

“短长句混合、加第一人称、加一点混乱、加具体感受”一旦变成固定动作，又会生成统一的 Humanizer 味。

### 3. 把检测和编辑混在一起

概率、分数、词频和检测器绕过会制造虚假确定性。编辑只需要回答“哪里不适合当前场景、怎样改更好”。

### 4. 忽略体裁

被动语态、hedging、列表、重复术语和正式结构在学术、法律、技术文档中可能完全正确。

### 5. 忽略作者自己的声音

多数 Skill 只有一个默认“自然人”口吻，没有从作者样本提取稳定风格。

### 6. 缺少不改的能力

已经自然的文本也被强行留下大量 diff，是 Humanizer 最常见的反向污染。

## Dahuang Human Tone 3.0 的统一方案

### 编辑合同

先确定模式、强度、体裁、作者声纹和不可改变项。

### 内容账本

锁定事实、引用、术语、论点、因果、时间线和叙事功能，深改也要逐项回读。

### 五遍引擎

1. 宏观结构
2. 去壳与具体性
3. 句子与连接
4. 作者声纹
5. 验证与回滚

### 体裁路由

技术、学术、法律、营销、社媒、公开写作和叙事分别定义允许修改的边界。

### 三档强度

轻改、标准、深改共享同一内容账本，只改变允许重构的范围。

### 回归用例

同时测试“应该改”和“不应该改”，尤其覆盖：

- 已经自然的文本
- 学术 hedging
- 技术术语和版本号
- 营销 CTA
- 小说伏笔与角色声口
- 用户写作样本

## 结论

3.0 不追求最大的禁用词表，而是建立一套能解释、能路由、能回滚、能保持作者差异的编辑系统。外部方案提供模块经验，Dahuang Human Tone 负责把它们收敛成一个中文优先的统一工作流。
