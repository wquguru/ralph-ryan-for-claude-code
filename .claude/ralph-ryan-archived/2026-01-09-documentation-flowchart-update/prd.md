# PRD: Ralph-Ryan for Claude Code - Documentation & Flowchart Update

# PRD: Ralph-Ryan for Claude Code - 文档与流程图更新

---

## 1. Introduction | 简介

### English
This project transforms the original Ralph pattern (designed for Amp) into a Claude Code skill that works seamlessly with the official `ralph-loop` plugin. The core innovation is combining the `ralph-ryan` skill (which provides structured PRD generation, preparation, and execution guidance) with Claude Code's official ralph-loop plugin for autonomous iteration.

The current documentation and flowchart still reflect the old Amp-based architecture. This PRD defines the work needed to update all materials to accurately represent the new Claude Code-native workflow.

### 中文
本项目将原始的 Ralph 模式（为 Amp 设计）改造为 Claude Code skill，与官方 `ralph-loop` 插件无缝协作。核心创新在于将 `ralph-ryan` skill（提供结构化的 PRD 生成、准备和执行指导）与 Claude Code 官方的 ralph-loop 插件结合，实现自主迭代开发。

当前文档和流程图仍反映旧的 Amp 架构。本 PRD 定义了更新所有材料以准确反映新的 Claude Code 原生工作流所需的工作。

---

## 2. Goals | 目标

### English
- Update the interactive flowchart to reflect the three-phase workflow: PRD → Prep → Run with ralph-loop
- Update README.md to target Claude Code users with clear setup and usage instructions
- Update AGENTS.md with Claude Code-specific patterns and commands
- Maintain bilingual (English/Chinese) content throughout all materials
- Preserve attribution to the original Ralph pattern by Geoffrey Huntley

### 中文
- 更新交互式流程图以反映三阶段工作流：PRD → Prep → Run with ralph-loop
- 更新 README.md，面向 Claude Code 用户提供清晰的设置和使用说明
- 更新 AGENTS.md，包含 Claude Code 特定的模式和命令
- 在所有材料中保持中英文双语内容
- 保留对 Geoffrey Huntley 原始 Ralph 模式的致谢

---

## 3. User Stories | 用户故事

### US-001: Update flowchart steps and labels
### US-001: 更新流程图步骤和标签

**Description | 描述:**
As a user viewing the flowchart, I want to see the correct Claude Code workflow so that I understand how ralph-ryan skill works with ralph-loop plugin.

作为查看流程图的用户，我希望看到正确的 Claude Code 工作流，以便理解 ralph-ryan skill 如何与 ralph-loop 插件协作。

**Acceptance Criteria | 验收标准:**
- [ ] Update `allSteps` array in `flowchart/src/App.tsx` to reflect new workflow:
  - Setup: "Write PRD with ralph-ryan skill" → "Prep: Convert to prd.json" → "Run ralph-loop command"
  - Loop: "Claude picks a story" → "Implements it" → "Commits changes" → "Updates prd.json" → "Logs to progress.txt" → "More stories?"
  - Exit: "Done!"
- [ ] Replace all "Amp" references with "Claude Code" or "Claude"
- [ ] Update header title from "How Ralph Works with Amp" to bilingual "How Ralph-Ryan Works with Claude Code | Ralph-Ryan 与 Claude Code 协作流程"
- [ ] Typecheck passes (`cd flowchart && npm run build`)

---

### US-002: Update flowchart notes content
### US-002: 更新流程图注释内容

**Description | 描述:**
As a user, I want the flowchart notes to show relevant Claude Code examples so that I understand the practical usage.

作为用户，我希望流程图注释显示相关的 Claude Code 示例，以便理解实际用法。

**Acceptance Criteria | 验收标准:**
- [ ] Update note-1 to show the three-phase command workflow:
  ```
  # Phase 1: PRD
  use ralph-ryan skill, write prd for [feature]

  # Phase 2: Prep
  use ralph-ryan skill, prepare files

  # Phase 3: Run
  /ralph-loop "Load skill ralph-ryan..."
  ```
- [ ] Update note-2 to mention skill-based learning persistence
- [ ] Ensure notes appear at appropriate steps
- [ ] Typecheck passes

---

### US-003: Add bilingual support to flowchart
### US-003: 为流程图添加双语支持

**Description | 描述:**
As a Chinese-speaking user, I want to see bilingual labels in the flowchart so that I can understand the workflow in my language.

作为中文用户，我希望在流程图中看到双语标签，以便用我的语言理解工作流。

**Acceptance Criteria | 验收标准:**
- [ ] Add Chinese translations to step labels (format: "English | 中文")
- [ ] Add Chinese translations to step descriptions
- [ ] Update subtitle to be bilingual
- [ ] Typecheck passes

---

### US-004: Update README.md structure and introduction
### US-004: 更新 README.md 结构和介绍

**Description | 描述:**
As a new user, I want the README to clearly explain what ralph-ryan is and how it enhances Claude Code so that I can quickly understand the value proposition.

作为新用户，我希望 README 清楚地解释 ralph-ryan 是什么以及它如何增强 Claude Code，以便快速理解其价值。

**Acceptance Criteria | 验收标准:**
- [ ] Replace header with bilingual title: "# Ralph-Ryan for Claude Code | Claude Code 版 Ralph-Ryan"
- [ ] Add bilingual introduction explaining:
  - What ralph-ryan skill is
  - How it works with official ralph-loop plugin
  - The three-phase workflow (PRD → Prep → Run)
- [ ] Remove all Amp-specific content (Prerequisites, Setup options for Amp)
- [ ] Keep attribution to Geoffrey Huntley's original Ralph pattern as "Acknowledgments" section

---

### US-005: Update README.md prerequisites and setup
### US-005: 更新 README.md 前置条件和设置

**Description | 描述:**
As a Claude Code user, I want clear setup instructions so that I can start using ralph-ryan quickly.

作为 Claude Code 用户，我希望有清晰的设置说明，以便快速开始使用 ralph-ryan。

**Acceptance Criteria | 验收标准:**
- [ ] Update Prerequisites section (bilingual):
  - Claude Code CLI installed
  - ralph-loop plugin installed (`/plugin install ralph-loop@claude-plugins-official`)
  - Git repository
- [ ] Update Setup section to show skill installation:
  ```bash
  # Copy skill to Claude Code skills directory
  cp -r skills/ralph-ryan ~/.claude/skills/
  ```
- [ ] Add Quick Start example showing the three commands

---

### US-006: Update README.md workflow section
### US-006: 更新 README.md 工作流部分

**Description | 描述:**
As a user, I want step-by-step workflow instructions so that I can follow the ralph-ryan process.

作为用户，我希望有分步工作流说明，以便遵循 ralph-ryan 流程。

**Acceptance Criteria | 验收标准:**
- [ ] Rewrite "Workflow" section with three phases:
  1. Create PRD: `use ralph-ryan skill, write prd for [feature]`
  2. Prepare: `use ralph-ryan skill, prepare files`
  3. Run: `/ralph-loop "Load skill ralph-ryan and execute run mode..." --max-iterations 10`
- [ ] Add bilingual explanations for each phase
- [ ] Include example output/expected behavior

---

### US-007: Update README.md key files and concepts
### US-007: 更新 README.md 关键文件和概念

**Description | 描述:**
As a user, I want to understand the file structure and core concepts so that I can work effectively with ralph-ryan.

作为用户，我希望理解文件结构和核心概念，以便有效地使用 ralph-ryan。

**Acceptance Criteria | 验收标准:**
- [ ] Update "Key Files" table to reflect new structure:
  - `.claude/ralph-ryan/prd.md` - PRD document
  - `.claude/ralph-ryan/prd.json` - Parsed user stories
  - `.claude/ralph-ryan/progress.txt` - Learning log
  - `skills/ralph-ryan/` - The skill files
- [ ] Update "Critical Concepts" section with Claude Code specific info
- [ ] Remove references to `ralph.sh` and `prompt.md`

---

### US-008: Update AGENTS.md for Claude Code
### US-008: 更新 AGENTS.md 适配 Claude Code

**Description | 描述:**
As Claude Code, I want accurate agent instructions so that I can execute ralph-ryan tasks correctly.

作为 Claude Code，我需要准确的 agent 指令，以便正确执行 ralph-ryan 任务。

**Acceptance Criteria | 验收标准:**
- [ ] Update Overview section to describe ralph-ryan skill + ralph-loop plugin architecture
- [ ] Update Commands section with Claude Code commands:
  - Skill invocation examples
  - ralph-loop command syntax
- [ ] Update Key Files to match new structure
- [ ] Update Patterns section for Claude Code context
- [ ] Add bilingual content throughout

---

## 4. Functional Requirements | 功能需求

- **FR-1:** All documentation must be bilingual (English/Chinese) with clear section headers
- **FR-2:** Flowchart must accurately represent the three-phase workflow
- **FR-3:** All code examples must use Claude Code syntax, not Amp
- **FR-4:** Installation instructions must reference official ralph-loop plugin
- **FR-5:** Original Ralph pattern attribution must be preserved

---

## 5. Non-Goals | 非目标

- Modifying the ralph-ryan skill implementation itself (only documentation)
- Supporting Amp CLI in any way
- Creating new features beyond documentation updates
- Changing the prd.json format or structure
- Adding new languages beyond English and Chinese

---

## 6. Technical Considerations | 技术考量

### Dependencies
- Flowchart uses React + @xyflow/react
- Build command: `cd flowchart && npm run build`
- Deployed via GitHub Pages

### File Locations
- Flowchart source: `flowchart/src/App.tsx`
- README: `README.md`
- AGENTS: `AGENTS.md`
- Skill files: `skills/ralph-ryan/`

### Validation
- Run `npm run build` in flowchart directory to verify TypeScript
- Visually verify flowchart renders correctly with `npm run dev`
