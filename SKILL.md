---
name: session-learnings
description: Use at end of development session, after completing significant work, debugging, or encountering obstacles - extracts learnings and proposes skill improvements
---

# Session Learnings

## Overview

Extract actionable learnings from development sessions and propose improvements to existing skills.

**Core principle:** Failures teach more than successes. The most valuable learnings are discoveries that required investigation, not documentation lookups.

**Iron law:** NO CHANGES TO SKILLS WITHOUT HUMAN APPROVAL. This skill proposes - you decide.

## When to Use

- End of debugging session (especially after non-obvious fixes)
- After completing significant feature work
- When you discovered a workaround through trial-and-error
- After encountering repeated friction with a process
- Before ending a session where something unexpected happened

**Explicit invocation:** `/session-learnings` or "what did we learn from this session?"

## Workflow

```
┌─────────────────────────────────────────────────────────────────┐
│                    SESSION LEARNINGS WORKFLOW                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌──────────────┐                                                │
│  │ 1. EXTRACT   │◄── Review session for learning candidates      │
│  └──────┬───────┘                                                │
│         │                                                        │
│         ▼                                                        │
│  ┌──────────────┐                                                │
│  │ 2. FILTER    │◄── Apply quality criteria (non-obvious,        │
│  └──────┬───────┘    reusable, verified)                         │
│         │                                                        │
│         ▼                                                        │
│  ┌──────────────┐                                                │
│  │ 3. MAP       │◄── Match learnings to existing skills          │
│  └──────┬───────┘                                                │
│         │                                                        │
│         ▼                                                        │
│  ┌──────────────┐                                                │
│  │ 4. PROPOSE   │◄── Generate specific improvement suggestions   │
│  └──────┬───────┘                                                │
│         │                                                        │
│         ▼                                                        │
│  ┌──────────────┐                                                │
│  │ 5. CONSULT   │◄── Present to human for approval               │
│  └──────────────┘    STOP HERE - NO CHANGES WITHOUT APPROVAL     │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

## Phase 1: Extract Learning Candidates

Review the session for:

### Bug Patterns
- Root causes that weren't immediately obvious
- Error messages that were misleading
- Debugging techniques that worked (or didn't)
- Symptoms vs actual problems

### Testing Gaps
- Tests that should have caught the issue but didn't exist
- Test patterns that would have helped
- Assertions that were missing
- Edge cases discovered

### Process Friction
- Steps that felt awkward or error-prone
- Workflows that didn't match reality
- Instructions that were unclear or incomplete
- Rationalizations that led to violations

### Discoveries
- Workarounds found through investigation
- Non-obvious solutions
- Project-specific patterns worth documenting
- Tool behaviors that weren't documented

## Phase 2: Apply Quality Filter

Only keep learnings that pass ALL criteria:

| Criterion | Question | Skip If... |
|-----------|----------|------------|
| **Discovery** | Did this require actual investigation? | Just reading docs would have solved it |
| **Reusable** | Would this help in future similar situations? | One-off edge case unlikely to recur |
| **Verified** | Has the solution been tested and confirmed? | Still uncertain if this is correct |
| **Non-obvious** | Would a fresh Claude likely make the same mistake? | Standard practice any developer knows |

## Phase 3: Map to Existing Skills

For each filtered learning, identify:

1. **Which skill(s) could benefit?**
   - Is this a gap in `superpowers-debug`?
   - Should `superpowers-tdd` cover this test pattern?
   - Is this a new rationalization for an existing skill?
   - Does a domain skill need updating?

2. **What type of improvement?**
   - New section (technique/pattern not covered)
   - Rationalization counter (new excuse to address)
   - Red flag addition (symptom of violation)
   - Example enhancement (better illustration)
   - Common mistake (pitfall to document)

3. **Or is this a NEW skill candidate?**
   - Pattern applies broadly across projects
   - Doesn't fit in existing skills
   - Worth the context cost of a new skill

## Phase 4: Generate Proposals

For each proposed change, document:

```markdown
### Proposal: [Brief title]

**Learning:** [What was discovered]

**Evidence:** [Session context - what happened, what we tried, what worked]

**Target Skill:** [skill-name] OR "New skill candidate"

**Proposed Change:**
[Specific text/section to add or modify]

**Rationale:** [Why this improves the skill]
```

## Phase 5: Consult Human

**MANDATORY STOP POINT**

Present all proposals to the human with:

1. Summary of learnings extracted
2. List of proposed skill changes
3. For each proposal:
   - What would change
   - Why it matters
   - Any risks or concerns

**Then ask:**
- Which proposals should be implemented?
- Any modifications needed?
- Any proposals to skip?

**DO NOT proceed to implementation until human approves specific proposals.**

## Phase 6: Implement Approved Changes

When implementing approved skill edits, **always** update the target skill's changelog and version:

### Version (frontmatter)

- If the target skill has no `version` field, add `version: 1.0` to its YAML frontmatter
- If it already has one, bump the minor version (e.g. 1.1 → 1.2)

### Changelog (bottom of SKILL.md)

Append a row to the `## Changelog` table at the bottom of the target SKILL.md. If no changelog section exists, create it:

```markdown
## Changelog

| Date | Change | Source |
|------|--------|--------|
| 2026-03-23 | Added red flag for async race condition | session: debugging upload timeout |
```

**Format:** `| YYYY-MM-DD | Brief description of what changed | session: what triggered the learning |`

## Learning Categories

### High-Value Learnings (Always Capture)

- **Debugging dead-ends:** "I tried X because of Y, but actual cause was Z"
- **Misleading symptoms:** "Error said A, but problem was B"
- **Missing tests:** "This bug would have been caught by [specific test type]"
- **Process violations:** "I rationalized skipping [process] by thinking [excuse]"
- **Non-obvious solutions:** "The fix required [unexpected insight]"

### Medium-Value Learnings (Capture If Clear)

- Tool-specific behaviors not in docs
- Project patterns worth standardizing
- Efficiency improvements to workflows
- Better examples for existing content

### Low-Value (Usually Skip)

- Documentation lookups that solved the issue
- Standard practices everyone knows
- One-off quirks unlikely to recur
- Hypothetical improvements not validated

## Output Format

When presenting learnings:

```markdown
## Session Learnings Summary

**Session focus:** [What the session was about]

**Key discoveries:** [1-3 most significant learnings]

---

### Proposals for Skill Improvements

#### 1. [Title]
**Target:** [skill-name]
**Type:** [New section / Rationalization counter / Red flag / Example / etc.]
**Change:** [Specific proposed text]
**Why:** [Brief rationale]

#### 2. [Title]
...

---

### New Skill Candidates

#### [Title] (if any)
**Scope:** [What this skill would cover]
**Evidence:** [Why it's needed based on session]

---

**Awaiting your approval before making any changes.**

Which proposals would you like me to implement?
```

## Red Flags - Stop and Reconsider

- Proposing changes without evidence from session
- Suggesting changes to skills you haven't read
- Making changes before human approval
- Capturing learnings that are just documentation lookups
- Creating new skills for one-off situations

## Related Skills

- `superpowers-debug` - Often receives debugging pattern improvements
- `superpowers-tdd` - Often receives test pattern improvements
- `superpowers-verify` - May receive verification checklist additions
- `writing-skills` - For actually implementing approved skill changes

## Why Failures Matter Most

From continuous learning research:

> "The skills that get referenced most aren't the ones documenting clean successes. They're the ones documenting failures. 'I tried X and it broke because Y' turns out to be the most useful sentence in the whole system."

Success stories tell you one path that worked. Failure stories tell you which paths to skip entirely.

**Prioritize capturing:**
- What didn't work and why
- Misleading error messages
- Rationalizations that led astray
- Dead-ends that wasted time
