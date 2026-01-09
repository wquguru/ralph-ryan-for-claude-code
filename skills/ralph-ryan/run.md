# Run Mode

Execute Ralph to implement user stories from prd.json.

---

## The Job

1. Read `.claude/ralph-ryan/prd.json` and `.claude/ralph-ryan/progress.txt`
2. Check Codebase Patterns section first
3. Ensure on correct branch from `branchName`
4. Pick highest priority story where `passes: false`
5. Implement that single story
6. Run quality checks, commit, update PRD and progress

---

## Branch Setup

- Check current branch matches PRD `branchName`
- If not, checkout or create from main

---

## Implementation Rules

- **ONE story per iteration** - Ralph spawns fresh each time
- **Keep changes minimal** - Only what the story requires
- **Follow existing patterns** - Match codebase conventions
- **ALL commits must pass** - typecheck, lint, test

---

## After Implementation

### Update prd.json
Set `passes: true` for completed story.

### Append to progress.txt
```
## [Date/Time] - [Story ID]
- What was implemented
- Files changed
- **Learnings:**
  - Patterns discovered
  - Gotchas encountered
---
```

### Commit Message
```
feat: [Story ID] - [Story Title]
```

---

## Codebase Patterns

If you discover **reusable patterns**, add to `## Codebase Patterns` section at TOP of progress.txt:

```
## Codebase Patterns
- Use `sql<number>` template for aggregations
- Always use `IF NOT EXISTS` for migrations
```

Only add patterns that are **general and reusable**.

---

## Update AGENTS.md

Before committing, check if edited directories have learnings worth preserving:

**Add:**
- API patterns or conventions
- Gotchas or non-obvious requirements
- Dependencies between files

**Don't add:**
- Story-specific details
- Temporary debugging notes

---

## Browser Testing (Frontend Stories)

For UI changes, MUST verify in browser:

1. Load the `dev-browser` skill
2. Navigate to relevant page
3. Verify UI changes work
4. Screenshot if helpful

**Frontend stories NOT complete until browser verified.**

---

## Stop Condition

After completing a story:

- If ALL stories have `passes: true`:
  1. **Archive completed work:**
     ```bash
     FEATURE=$(jq -r '.featureName' .claude/ralph-ryan/prd.json)
     mv .claude/ralph-ryan ".claude/ralph-ryan-archived/$(date +%Y-%m-%d)-${FEATURE}"
     ```
  2. **Output:**
     ```
     <promise>COMPLETE</promise>
     Archived to: .claude/ralph-ryan-archived/YYYY-MM-DD-<featureName>/
     ```

- If stories remain with `passes: false`:
  End normally (next iteration continues)
