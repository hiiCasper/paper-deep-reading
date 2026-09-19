# Paper Deep Reading

**Language:** [English](#english) | [中文](#中文)

---

## English

[中文](#中文)

Paper Deep Reading is a Codex skill for deep-reading academic papers and producing structured Chinese research notes with critical analysis. It is designed for workflows where a paper should become a reusable research artifact rather than a loose summary.

### What It Does

- Finds or reads a paper from a title, DOI, arXiv link, publisher page, GitHub/project page, PDF URL, or local PDF.
- Reads the paper in three passes: motivation and claims, method and mechanism, then evaluation and limitations.
- Extracts key evidence from figures, tables, formulas, algorithms, and definitions.
- Positions the paper against prior work and distinguishes novelty in method, setting, data, and findings.
- Produces a structured Chinese note with TL;DR, motivation, method, evaluation, strengths, limitations, takeaways, open questions, and a short critical comment section.
- Optionally supports syncing finished notes and PDFs into a Git-managed paper-reading repository when explicitly requested.

### When to Use

Use this skill when you ask Codex to:

- Deep-read an academic paper.
- Summarize, organize, or analyze an academic paper.
- Work from a paper title, DOI, arXiv link, publisher link, GitHub/project link, PDF URL, or local PDF.
- Maintain a structured paper-reading repository.

### Output Style

The final note is written in Chinese, with precise terminology and English terms preserved in parentheses when translation may lose meaning. The note follows the schema in [`references/output-schema.md`](references/output-schema.md).

### Installation

Install this skill from GitHub with the Codex skill installer:

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo hiiCasper/paper-deep-reading \
  --path . \
  --name paper-deep-reading
```

The skill will be installed to:

```text
~/.codex/skills/paper-deep-reading
```

It becomes available in Codex on the next turn or after restarting the session.

### Verify Installation

Run:

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py \
  ~/.codex/skills/paper-deep-reading
```

Expected output:

```text
Skill is valid!
```

### Example Prompts

```text
Use paper-deep-reading to deep-read this paper and write a Chinese research note.
```

```text
精读这篇论文，做批判性分析，并整理成中文研究笔记。
```

```text
Read this arXiv paper and connect it to my paper-reading repository.
```

### Repository Structure

```text
paper-deep-reading/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── output-schema.md
```

---

## 中文

[English](#english)

Paper Deep Reading 是一个用于精读学术论文的 Codex skill。它的目标不是生成松散摘要，而是把一篇论文转化为可长期保存、可复用、带有批判性分析的中文研究笔记。

### 它能做什么

- 从论文标题、DOI、arXiv 链接、出版方页面、GitHub/项目页面、PDF 链接或本地 PDF 获取并阅读论文。
- 分三遍阅读论文：先看动机和主张，再看方法和机制，最后看实验、局限和相关工作。
- 提取关键图、表、公式、算法和定义，并说明它们支撑了哪些结论。
- 将论文和已有工作进行定位比较，区分方法、设定、数据和发现层面的新意。
- 输出结构化中文笔记，包括 TL;DR、研究问题、动机与基本想法、方法、实验、优势、局限、个人启发、开放问题，以及一段简短的“毒舌评论”。
- 在用户明确要求时，可以把完成后的笔记和 PDF 同步到 Git 管理的论文阅读仓库。

### 什么时候使用

当你希望 Codex 完成以下任务时，可以使用这个 skill：

- 精读一篇学术论文。
- 总结、整理或分析一篇学术论文。
- 根据论文标题、DOI、arXiv 链接、出版方链接、GitHub/项目链接、PDF 链接或本地 PDF 工作。
- 维护结构化论文阅读仓库。

### 输出风格

最终笔记使用中文撰写，并尽量保持论文术语精确。当翻译可能损失含义时，保留关键英文术语的括号标注。笔记结构见 [`references/output-schema.md`](references/output-schema.md)。

### 安装方式

使用 Codex skill installer 从 GitHub 安装：

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo hiiCasper/paper-deep-reading \
  --path . \
  --name paper-deep-reading
```

安装位置：

```text
~/.codex/skills/paper-deep-reading
```

安装后，它会在下一轮对话或重启会话后出现在 Codex 可用 skill 列表中。

### 验证安装

运行：

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py \
  ~/.codex/skills/paper-deep-reading
```

期望输出：

```text
Skill is valid!
```

### 示例提示词

```text
Use paper-deep-reading to deep-read this paper and write a Chinese research note.
```

```text
精读这篇论文，做批判性分析，并整理成中文研究笔记。
```

```text
Read this arXiv paper and connect it to my paper-reading repository.
```

### 仓库结构

```text
paper-deep-reading/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── output-schema.md
```
