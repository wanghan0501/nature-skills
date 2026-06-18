# nature-skills

大家好，我是 nature skills 的创立者袁一哲。感谢大家持续关注 `nature-skills`。我们在抖音更新了很多视频教程，大家可以根据名称检索查看，希望真心能够帮助到大家。

如果你有任何需求，欢迎提交 issue；如果我们认为该需求有意义且可行，会尽量推进实现。我们也欢迎 PR，但请按照本文后面的贡献格式提交，方便更高效地审核与合并。

<table>
  <tr>
    <td align="center">
      <b>视频教程请关注抖音</b><br>
      <img width="500" alt="视频教程请关注抖音" src="https://github.com/user-attachments/assets/1eefda21-86a4-4081-96e4-d40dea9e1e7b" />
    </td>
    <td align="center">
      <b>青春中国（袁一哲）</b><br>
      <img width="500" alt="青春中国（袁一哲）" src="assets/youth-china-yuan-yizhe.png" />
    </td>
  </tr>
</table>

---

## 安装

`nature-skills` 是一组围绕 `SKILL.md` 组织的可复用技能包。每个 `skills/nature-*` 目录都是一个可安装单元，部分技能还依赖 `skills/_shared/` 中的共享内容。

### Codex 推荐安装方式

最简单的方式是把仓库链接交给 Codex，并让它安装完整技能目录：

```text
https://github.com/Yuan1z0825/nature-skills.git
```

推荐提示词：

```text
请从这个仓库安装 Codex skills：
https://github.com/Yuan1z0825/nature-skills.git

请把 skills/ 下的完整技能文件夹安装到我的 Codex skills 目录中，包括 skills/_shared。
不要只复制 SKILL.md。
```

如果只安装单个技能，请明确说明技能名：

```text
只安装这个仓库里的 nature-reader：
https://github.com/Yuan1z0825/nature-skills.git

如果该技能需要共享文件，也请一并安装 skills/_shared。
```

关键规则：保留完整目录结构。请复制或引用整个技能文件夹，而不是只复制 `SKILL.md`，因为许多技能依赖 `references/`、`static/`、`manifest.yaml`、脚本、资产或共享文件。

### 手动安装

```bash
git clone https://github.com/Yuan1z0825/nature-skills.git
cd nature-skills
mkdir -p ~/.codex/skills
cp -R skills/_shared ~/.codex/skills/
for d in skills/nature-*; do
  cp -R "$d" ~/.codex/skills/
done
```

安装后，请开启一个新的 Codex 会话，然后自然描述任务，例如：

```text
把这篇论文做成中英文对照的完整 Markdown reader。
```

```text
把这篇论文做成中文 journal-club PPT。
```

更完整的安装说明和排错笔记见 [`install.md`](install.md)。

### 目录结构

```text
skills/
├── _shared/              # 当技能引用 ../_shared 时需要保留
└── nature-<topic>/
    ├── README.md
    ├── SKILL.md
    ├── manifest.yaml     # router-style 技能会包含
    ├── static/           # router-style 技能会包含
    └── references/...
```

### 非 Codex 场景

用于 Claude Code 或其他 agent 时，建议保留一个稳定的仓库 clone，再创建轻量 subagent、slash command 或 custom prompt wrapper，指向真实的 `skills/nature-*/SKILL.md`，并保留 `skills/_shared/`。

手动或非 Codex 使用时：

1. 将完整技能目录复制到你的 prompt library 或项目中。
2. 保留 `SKILL.md`、`manifest.yaml`、`static/`、`references/`、脚本、资产和需要的 `skills/_shared/` 文件。
3. 如目标 agent 有自己的格式要求，可调整 frontmatter 和正文结构。

## Star 历史

[![Star History Chart](https://api.star-history.com/svg?repos=Yuan1z0825/nature-skills&type=Date&cache_bust=2026-06-07T16)](https://star-history.com/#Yuan1z0825/nature-skills&Date)

## 技能索引

| 技能 | 状态 | 用途 | 触发词 |
|-------|--------|---------|-----------------|
| [`nature-figure`](skills/nature-figure/README.md) | Stable | 面向 Nature / 高影响力期刊的 Python 或 R 投稿级科研图工作流，内置 figures4papers demo | “Nature figure”, “投稿级图片”, “publication plot”, “scientific figure”, “figures4papers” |
| [`nature-polishing`](skills/nature-polishing/README.md) | Stable | 将学术文本润色、重构或翻译为 Nature 风格英文 | “Nature style”, “润色”, “academic writing”, “论文英文” |
| [`nature-writing`](skills/nature-writing/README.md) | Draft | 起草 Nature 风格手稿章节，并重建论文论证 | “Nature writing”, “写摘要”, “写引言”, “manuscript draft”, “论文写作” |
| [`nature-reviewer`](skills/nature-reviewer/README.md) | Draft | 从审稿人视角模拟 Nature 风格评审，输出三份 reviewer reports 和综合意见 | “Nature reviewer”, “预投稿评审”, “reviewer report”, “审稿人视角评估” |
| [`nature-citation`](skills/nature-citation/README.md) | Beta | 检索严格限定在 Nature / CNS 系列的支撑文献，并导出 ENW、RIS 或 Zotero RDF | “Nature citation”, “CNS citation”, “分段引用”, “支撑文献”, “Zotero RDF” |
| [`nature-data`](skills/nature-data/README.md) | Draft | 准备 Data Availability statement、数据仓储方案和 FAIR 检查 | “Data Availability”, “数据可用性”, “repository”, “FAIR metadata” |
| [`nature-reader`](skills/nature-reader/README.md) | Beta | 生成带来源锚点、图文对应和中英文对照的全文 Markdown reader | “nature reader”, “全文 Markdown”, “原文对照”, “图文对应”, “全文翻译” |
| [`nature-response`](skills/nature-response/README.md) | Beta | 起草、审查和修改逐点回复审稿人的 response letter | “response to reviewers”, “rebuttal letter”, “major revision”, “审稿意见回复” |
| [`nature-paper2ppt`](skills/nature-paper2ppt/README.md) | Beta | 从科研论文生成中文 PPTX 文献汇报 deck | “paper PPT”, “journal club”, “paper to slides”, “论文汇报” |
| [`nature-paper-to-patent`](skills/nature-paper-to-patent/README.md) | Beta | 从论文、技术报告或项目材料生成有证据约束的中国发明专利草稿 | “paper to patent”, “Chinese patent”, “论文转专利”, “权利要求书” |
| [`nature-academic-search`](skills/nature-academic-search/README.md) | Beta | 多源文献检索、引用核验和参考文献管理 | “search papers”, “find articles”, “literature search”, “查文献”, “verify DOI” |

> **想新增技能？** 请参考本文末尾的 [贡献指南](#新增技能)。

---

## 技能概览

### `nature-figure`

用于生成多面板 matplotlib / ggplot2 科研图，目标是满足 Nature 级视觉质量：正确字体、语义配色、可编辑 SVG 输出和非冗余 panel 信息架构。

示例图库与 chart atlas 见 [`nature-figure` README](skills/nature-figure/README.md)。内置图例覆盖材料机制、空间成像、体内疗效、单细胞系统和扰动验证等常见高影响力论文图件场景。

| ![Material design and physical validation](skills/nature-figure/assets/gallery/fig1-material-mechanism-rich.png) | ![Spatial imaging and uptake](skills/nature-figure/assets/gallery/fig2-spatial-imaging-rich.png) | ![In vivo efficacy and tolerability](skills/nature-figure/assets/gallery/fig3-in-vivo-efficacy-rich.png) | ![Single-cell systems figure](skills/nature-figure/assets/gallery/fig4-single-cell-systems-rich.png) | ![Perturbation validation](skills/nature-figure/assets/gallery/fig5-validation-perturbation-rich.png) |
|---|---|---|---|---|

关键规则：

- 绘图前先确认核心结论、证据层级、panel map、统计和 source-data 需求。
- Python 图件必须设置 `svg.fonttype = 'none'`，保证 SVG 中文字可编辑。
- 主输出优先为 `.svg`；`.png` 仅作为 300 dpi 预览或二级输出。
- 多面板图遵守“overview → deviation → relationship”的信息层级，避免两个 panel 回答同一个科学问题。

### `nature-polishing`

用于把学术草稿，尤其是中文到英文的论文文本，润色为更接近 Nature 风格的英文。它强调句长控制、章节时态、hedging、引用完整性、过度声称识别和英式英文风格。

核心流程：

```text
句子拆分 → 章节识别 → 沙漏结构检查 → 时态审查 → 句子修改 → 词汇升级
→ 模板检查 → 引用审查 → 期刊风格 → 过度声称检查 → 校对 → 纯文本输出
```

### `nature-writing`

用于根据作者提供的结果、图表、claims、笔记或中文草稿，起草或重建手稿章节。它处理的是论证构建，而不是只做句子润色。

覆盖摘要、引言、方法、结果叙事、讨论、结论、标题、实验设计描述和 reviewer-facing 自审。默认规则是不编造数据、机制、统计量、引用或创新性；中文笔记按意图与论证翻译，而不是按句序直译。

### `nature-reviewer`

用于从审稿人视角评估手稿，输出三份 reviewer reports 和一份 cross-review synthesis。它关注 novelty、significance、technical soundness、presentation 和 editorial risk。

该技能只基于用户提供的材料和本地 reviewer source basis，不虚构审稿人身份、专业背景或隐藏知识。

### `nature-citation`

用于把论文文本或独立 claim 转化为 Nature / CNS 系列引用候选，并导出一个可被文献管理器导入的 `ENW`、`RIS` 或 Zotero `RDF` 文件。它也可生成 HTML 审查页，支持按年份过滤、选择候选文献和下载指定格式。

关键能力包括分段、范围过滤、支撑等级判断、元数据完整性检查和长文批处理。

### `nature-data`

用于准备和审查 Data Availability statement、数据仓储方案、数据集引用和 FAIR 元数据。它适用于 Nature 系列和 Springer Nature 投稿，也支持把中文作者笔记转为英文投稿文本。

重点是为每个支撑论文结论的数据集提供清晰、持久、可审查的访问路径；不能编造 accession、许可证、限制条件或仓储元数据。

### `nature-reader`

用于把 PDF、DOI、arXiv 链接、出版社 HTML 或粘贴文本转为中英文对照的完整 Markdown reader。默认产物包括 `paper.md`、`source_map.json`、`translation_notes.md` 和 `assets/`。

该技能强调图文对应、source anchor、表格/图像贴近相关正文，并且不能退化成只给摘要。

### `nature-response`

用于起草、审查和修改逐点回复审稿人的 response letter。每条审稿意见会获得稳定 ID，并被分类、映射到行动、手稿位置、证据或缺失信息标记。

核心规则是不编造实验、分析、引用、行号、图版或编辑要求；回复信应是给编辑核查的验证文件，而不是泛泛的礼貌文本。

### `nature-paper2ppt`

用于把科研论文、预印本、PDF、图注或阅读笔记转换为中文 `.pptx`，适合 journal club、组会、实验室会议、论文分享和学位汇报。

它会识别论文类型，提取科学论证，选择真正支撑论证的图表，写中文 slide title、bullet、caption、takeaway 和 speaker notes，并生成实际 PPTX 文件。

### `nature-paper-to-patent`

用于把科研论文、学位论文、技术报告、源代码、图表或发明人笔记转换为有证据约束的中国发明专利草稿。

它会先建立 source ID 和 evidence ledger，再起草权利要求，并生成权利要求书、说明书、说明书摘要、摘要附图和完整审阅稿等中文 DOCX。输出是起草辅助材料，不构成专利性、新颖性、权属、侵权或可提交性法律意见。

### `nature-academic-search`

用于多源学术检索和参考文献管理。它通过本地 MCP server 并行检索 PubMed、CrossRef 和 arXiv，也可显式调用 Scopus / ScienceDirect；支持 DOI、PMID、arXiv ID 查询、引用格式化、MeSH 查询和 `.nbib`、`.ris`、`.bib`、`.enw` 文件工作流。

---

## 共享设计原则

所有技能都遵守以下原则：

1. **优先使用一手来源**：规则基于已发表 Nature 内容、官方期刊指南或明确的本地来源，而不是泛泛审美偏好。
2. **显式胜过隐式**：每条规则都应说明理由，而不是只给断言。
3. **感知章节与任务上下文**：学术写作、图件、引用和回复都依赖上下文；不同论文部分使用不同逻辑。
4. **输出优先**：每个技能都应返回能直接使用的产物，例如可粘贴文本、`.svg`、`.pptx`、`.docx` 或具体建议。
5. **可扩展**：每个技能自包含在自己的目录中，新增技能不应要求修改既有技能。

---

## 新增技能

向本仓库添加技能时，请按以下流程：

### 1. 创建目录

```text
skills/nature-<topic>/
```

### 2. 最低文件要求

| 文件 | 是否必需 | 用途 |
|------|----------|------|
| `SKILL.md` | 必需 | frontmatter（`name`、`description`）+ 规则 + 工作流；触发后由 agent 加载 |
| `README.md` | 必需 | 面向人的中文说明文档 |
| `references/*.md` | 复杂技能推荐 | 模块化规则文件，例如 API、设计理论、教程、图表类型等 |

### 3. `SKILL.md` frontmatter 模板

```yaml
---
name: nature-<topic>
description: >-
  用一句话说明这个技能做什么、什么时候触发、主要输出格式和核心使用场景。
---
```

### 4. 更新技能索引

在上方 [技能索引](#技能索引) 表格中添加一行：

```markdown
| [`nature-<topic>`](skills/nature-<topic>/README.md) | Draft / Stable | 一句话用途 | 触发词 |
```

### 5. 状态标签

| 标签 | 含义 |
|-------|------|
| `Draft` | 规则已定义，但尚未在真实案例上测试 |
| `Beta` | 已在示例上测试，仍可能存在边界问题 |
| `Stable` | 已在真实学术内容上验证，规则相对稳定 |

---

## 候选技能

以下是目前记录的缺口，欢迎贡献：

| 候选技能 | 范围 | 优先级 |
|-----------|-------|----------|
| `nature-stats` | Nature 统计报告规范，例如效应量、置信区间、p 值格式和样本量说明 | 高 |
| `nature-methods` | 深度 Methods 写作助手，包括可复现性清单、禁用表达、伦理审批模板和补充材料组织 | 中 |
| `nature-cover` | Cover letter 起草，包括 hook paragraph、意义 framing、期刊匹配理由和 500 词以内限制 | 中 |

## 如果内容对你有帮助，欢迎随缘支持一下

---

<div align="center">

| 微信赞赏 | 来自粉丝的小感动 |
| --- | --- |
| <img width="320" alt="微信赞赏" src="https://github.com/user-attachments/assets/83c101e7-2370-46e9-a840-cb506df98cf4" /> | <img width="320" alt="粉丝的鼓励" src="https://github.com/user-attachments/assets/0484300a-95e8-4cb3-ad73-478ba9bd19d6" /> |

</div>

### 想说的话

项目会长期免费维护，大家正常使用就好。很多朋友还是学生党，所以完全不需要有任何“必须打赏”的压力。

如果这些内容刚好帮你节省了一些时间、解决了一点问题，又恰好想请作者喝杯咖啡，那我会非常开心。

你的支持会用于：

- 持续更新内容
- 服务器与工具费用
- 熬夜写文档时的续命奶茶（认真）

无论是否赞赏，都非常感谢你的关注与支持。
