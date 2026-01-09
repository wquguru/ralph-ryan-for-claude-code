# PRD: README.md 优化

## 1. Introduction | 简介

优化 README.md 文档，使其更简洁易读，并添加对原项目作者 Ryan Carson 的鸣谢。

---

## 2. Goals | 目标

- 简化 README.md 内容，提升可读性
- 保持中英双语结构
- 添加 Ryan Carson 鸣谢，解释项目命名由来
- 移除 Geoffrey Huntley 鸣谢（因本项目直接 fork 自 Ryan 的仓库）

---

## 3. User Stories | 用户故事

### US-001: 简化文档结构

**Description:** 作为用户，我希望 README 更精简，能快速理解项目用途和使用方法。

**Acceptance Criteria:**
- [ ] 精简 Introduction 部分，去除重复描述
- [ ] 合并 Quick Start 和 Workflow Details，避免内容重复
- [ ] 删除冗余的 Debugging 部分（非核心功能）
- [ ] 保持中英双语格式
- [ ] 总行数减少 30% 以上

### US-002: 添加鸣谢与命名说明

**Description:** 作为用户，我希望了解项目来源和命名原因。

**Acceptance Criteria:**
- [ ] 添加 Ryan Carson 鸣谢（项目 fork 自 https://github.com/snarktank/ralph）
- [ ] 说明 "ralph-ryan" 命名由来（Ralph 模式 + Ryan 作者名）
- [ ] 介绍 Ryan 是 https://ampcode.com/ 创始人
- [ ] 鼓励用户尝试 Amp
- [ ] 移除 Geoffrey Huntley 鸣谢
- [ ] 鸣谢部分简洁，不超过 5 行

---

## 4. Functional Requirements | 功能需求

- FR-1: README.md 必须保持中英双语
- FR-2: 必须包含 Quick Start 快速开始指南
- FR-3: 必须包含 Setup 安装指南
- FR-4: 必须包含致谢部分

---

## 5. Non-Goals | 非目标

- 不修改技能文件本身
- 不修改流程图相关内容
- 不添加新功能文档

---

## 6. Technical Considerations | 技术考虑

- 保持现有 markdown 格式规范
- 保留 ralph.webp 图片引用
- 保留流程图链接
