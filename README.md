# Session Learnings

A [Claude Code](https://claude.com/claude-code) skill that extracts actionable learnings from development sessions and proposes improvements to your existing skills.

## Why

Failures teach more than successes. This skill captures non-obvious discoveries, debugging dead-ends, and process friction — then maps them to concrete skill improvements.

## Install

Copy `SKILL.md` into your project's `.claude/skills/session-learnings/` directory:

```bash
mkdir -p .claude/skills/session-learnings
cp SKILL.md .claude/skills/session-learnings/
```

## Usage

Invoke at the end of a development session:

```
/session-learnings
```

Or naturally: *"what did we learn from this session?"*

## How It Works

1. **Extract** — Reviews the session for learning candidates (bug patterns, testing gaps, process friction, discoveries)
2. **Filter** — Keeps only learnings that are non-obvious, reusable, and verified
3. **Map** — Matches learnings to existing skills, CLAUDE.md guidelines, or permissions that could benefit
4. **Propose** — Generates specific improvement suggestions with evidence
5. **Consult** — Presents proposals for human approval (no changes without your OK)
6. **Implement** — Applies approved changes with changelog entries and version tracking

## Beyond Skills

In addition to skill improvements, this skill also proposes:

- **CLAUDE.md improvements** — Missing guidelines, outdated instructions, or rules that would have prevented session issues
- **Permission improvements** — Tool permissions that should be pre-allowed, tightened, or added to reduce friction

## Changelog Tracking

When this skill edits a target skill, it automatically:
- Adds/bumps a `version` field in the target's YAML frontmatter
- Appends a changelog entry with date, description, and session context

## License

MIT
