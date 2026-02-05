---
name: skill-integration
description: Create and integrate custom Cursor skills from conversations or documentation. Use when the user wants to create a skill, save a workflow as a skill, integrate skills into Cursor, or link skills from a repository.
---

# Skill Integration

## Overview

This skill helps create custom skills from chat conversations and integrate them into Cursor via directory junctions.

## Skill File Format

Every skill needs a `SKILL.md` with YAML frontmatter:

```markdown
---
name: skill-name
description: What the skill does and when to use it
---

# Skill Title

## Overview
Brief description...

## Instructions
Step-by-step guidance...
```

### Frontmatter Fields

| Field | Requirements |
|-------|--------------|
| `name` | Lowercase, hyphens, max 64 chars |
| `description` | Include WHAT it does and WHEN to use it |

## Storage Locations

| Location | Path | Scope |
|----------|------|-------|
| Project skills | `libs/skills/skill-name/` | Shared via repository |
| System skills | `~/.cursor/skills-cursor/` | Active in Cursor |

**Note:** Skills in project folders need to be linked to work in Cursor.

## Integration Workflow

### Step 1: Create skill directory and SKILL.md

```bash
mkdir libs/skills/new-skill-name
# Create SKILL.md with proper frontmatter
```

### Step 2: Create junction to system folder

On Windows (no admin rights needed):

```bash
cd ~/.cursor/skills-cursor
cmd //c "mklink /J skill-name C:\full\path\to\libs\skills\skill-name"
```

### Step 3: Verify junction works

```bash
powershell -Command "Get-ChildItem ~/.cursor/skills-cursor/skill-name"
```

### Step 4: Commit changes

```bash
git add -A
git commit -m "Add skill-name skill"
git push
```

## Creating Skills from Chats

When asked to create a skill from a conversation:

1. **Identify key knowledge** - Extract workflows, commands, patterns
2. **Structure as instructions** - Write clear, actionable steps
3. **Keep it concise** - Under 500 lines, focus on what the agent doesn't know
4. **Include examples** - Concrete examples improve quality

### Prompt template

> "Create a skill named [name] from this chat that covers [topic]"

## Submodule Workflow

If skills are in a git submodule:

```bash
# After modifying skills in submodule
cd libs/skills
git add -A
git commit -m "Add/update skill-name"
git push

# Update parent repo reference
cd ../..
git add libs/skills
git commit -m "Update skills submodule"
git push
```

## Best Practices

- **One skill per concern** - Split large skills into focused pieces
- **Third-person descriptions** - "Processes X" not "I help with X"
- **Include trigger terms** - Help agent know when to use the skill
- **Test after creation** - Ask a question that should trigger the skill
