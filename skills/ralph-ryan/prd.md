# PRD Generator Mode

Generate Product Requirements Documents suitable for Ralph autonomous execution.

---

## The Job

1. Receive feature description from user
2. Ask 3-5 clarifying questions (with lettered options)
3. Generate structured PRD
4. Save to `.claude/ralph-ryan/prd.md`

**Important:** Do NOT implement. Just create the PRD.

---

## Step 1: Clarifying Questions

Ask only critical questions. Format with lettered options:

```
1. What is the primary goal?
   A. Improve user experience
   B. Add new functionality
   C. Fix existing issues
   D. Other: [specify]

2. What is the scope?
   A. Minimal viable version
   B. Full-featured implementation
   C. Backend only
   D. Frontend only
```

Users can respond "1A, 2C" for quick iteration.

---

## Step 2: PRD Structure

### 1. Introduction
Brief description of feature and problem it solves.

### 2. Goals
Specific, measurable objectives (bullet list).

### 3. User Stories

**Critical: Size stories for ONE Ralph iteration (one context window).**

Format:
```markdown
### US-001: [Title]
**Description:** As a [user], I want [feature] so that [benefit].

**Acceptance Criteria:**
- [ ] Specific verifiable criterion
- [ ] Another criterion
- [ ] Typecheck passes
- [ ] [UI only] Verify in browser using dev-browser skill
```

**Right-sized stories:**
- Add a database column and migration
- Add a UI component to existing page
- Update a server action with new logic

**Too big (split these):**
- "Build entire dashboard" → Split into: schema, queries, components, filters
- "Add authentication" → Split into: schema, middleware, login UI, session

**Rule:** If you cannot describe change in 2-3 sentences, it's too big.

### 4. Functional Requirements
Numbered list: "FR-1: The system must..."

### 5. Non-Goals
What this feature will NOT include.

### 6. Technical Considerations (Optional)
Known constraints, dependencies, integrations.

---

## Story Ordering

Stories execute in priority order. Earlier stories must NOT depend on later ones.

**Correct order:**
1. Schema/database changes
2. Server actions / backend logic
3. UI components using the backend
4. Dashboard/summary views

---

## Acceptance Criteria Rules

Must be **verifiable**, not vague.

**Good:**
- "Add `status` column with default 'pending'"
- "Filter dropdown has options: All, Active, Completed"
- "Typecheck passes"

**Bad:**
- "Works correctly"
- "Good UX"
- "Handles edge cases"

**Always include:**
- `Typecheck passes` (every story)
- `Verify in browser using dev-browser skill` (UI stories)

---

## Output

Save to: `.claude/ralph-ryan/prd.md`

---

## Checklist

Before saving:
- [ ] Asked clarifying questions with lettered options
- [ ] Each story completable in one iteration
- [ ] Stories ordered by dependency
- [ ] Acceptance criteria are verifiable
- [ ] Saved to `.claude/ralph-ryan/prd.md`
