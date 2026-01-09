# Prep Mode

Prepare Ralph execution environment by converting PRD and initializing files.

---

## The Job

1. Read `.claude/ralph-ryan/prd.md`
2. Convert to `.claude/ralph-ryan/prd.json`
3. Initialize `.claude/ralph-ryan/progress.txt` (if not exists)

---

## Output Format

```json
{
  "project": "[Project Name]",
  "featureName": "[feature-name-kebab-case]",
  "branchName": "ralph/[feature-name-kebab-case]",
  "description": "[Feature description]",
  "userStories": [
    {
      "id": "US-001",
      "title": "[Story title]",
      "description": "As a [user], I want [feature] so that [benefit]",
      "acceptanceCriteria": [
        "Criterion 1",
        "Typecheck passes"
      ],
      "priority": 1,
      "passes": false,
      "notes": ""
    }
  ]
}
```

---

## Conversion Rules

1. Each user story → one JSON entry
2. IDs: Sequential (US-001, US-002, ...)
3. Priority: Based on dependency order, then document order
4. All stories: `passes: false`, empty `notes`
5. featureName: kebab-case (e.g., "task-priority-system")
6. branchName: `ralph/` + featureName
7. Always include "Typecheck passes" in acceptance criteria

---

## Initialize progress.txt

If `.claude/ralph-ryan/progress.txt` doesn't exist, create it:

```markdown
## Codebase Patterns

(Patterns discovered during implementation will be added here)

---

# Progress Log

```

---

## Archiving Previous Runs

Before writing new prd.json:

1. Check if `.claude/ralph-ryan/prd.json` exists
2. If featureName differs from new feature:
   - Create `.claude/ralph-ryan-archived/YYYY-MM-DD-<featureName>/`
   - Move current `prd.json` and `progress.txt` to archive
   - Reset `progress.txt` with fresh header

---

## Checklist

Before saving:
- [ ] Previous run archived (if different featureName)
- [ ] featureName is kebab-case
- [ ] Each story completable in one iteration
- [ ] Stories ordered by dependency
- [ ] Every story has "Typecheck passes"
- [ ] UI stories have "Verify in browser using dev-browser skill"
- [ ] progress.txt initialized
- [ ] Saved to `.claude/ralph-ryan/prd.json`
