# Implement GitHub Issue

Implement a GitHub issue following TDD principles and best practices.

## Usage
Use this command when you need to implement a GitHub issue that has clear requirements and/or test cases. Think step by step as you work through the process.

## Process

### 1. **Gather Context**
Before any implementation, understand the full context:

```bash
# Read the issue itself
gh issue view <number> --json title,body,labels

# Check if this is part of an epic
# Look for "Related to #X" or "Part of #X" in the issue body
# If found, read the epic:
gh issue view <epic-number>

# Check for design documents
# Look for references to design docs in issue or epic
# Common patterns:
# - "See design document at docs/..."
# - "Design: [link]"
# - "Implements <feature> from design doc"

# If design doc exists, read it thoroughly
cat docs/<feature>-design.md
```

**Key questions to answer:**
- What is the larger goal this contributes to?
- Are there architectural decisions already made?
- What are the explicit non-goals?
- Are there user personas to consider?
- What phase of implementation is this?

### 2. **Create Feature Branch**
Check Git status first. If clean, then switch back to main, make sure you're up to date, and make a feature branch.
```bash
git status
git checkout main
git pull
git checkout -b feature/<descriptive-name>
```

### 3. **Set Up Progress Tracking**
Use TodoWrite to create a task list that includes:
- Context gathering steps
- Requirements from the issue
- Any additional requirements from epic/design doc
- Testing requirements
- Documentation updates

Break down large tasks into smaller, concrete steps. Mark items as "in_progress" when starting, "completed" when done.

### 4. **Validate Understanding**
Before coding, ensure you understand:
- How this fits into the larger system
- What patterns are already established
- What the acceptance criteria are
- Whether there are existing similar implementations to follow

### 5. **Follow TDD Workflow**
- Find the relevant test file(s)
- Run specific failing test: `python3 -m pytest path/to/test.py::TestClass::test_method -xvs`
- Implement minimal code to make it pass
- Run all tests in the file to check for regressions
- Repeat for each failing test

### 6. **Implementation Guidelines**
- Follow patterns established in design docs
- Use abstractions defined in the epic
- Write the simplest code that makes tests pass
- Add type hints as you code
- Include inline comments only for non-obvious logic
- Follow existing code patterns in the codebase
- Respect the boundaries set in design doc's non-goals

### 7. **Cross-Reference Design**
As you implement, continuously check:
- Are you staying within scope defined in design doc?
- Are you using the technology choices specified?
- Are you following the architectural patterns?
- Are you considering the user personas?

### 8. **Commit Regularly**
- Make atomic commits for each logical change
- Use descriptive commit messages with conventional commits format
- Include test results in commit messages when significant
- Reference both the issue and epic in commit messages when relevant

### 9. **Create Pull Request**
```bash
git push -u origin <branch-name>
```

Then create the PR with a comprehensive description:
```bash
gh pr create --title "<Title matching issue>" --body "$(cat <<'EOF'
## Summary
<1-3 bullet points summarizing what was implemented>

## Context
- Implements: #<issue-number>
- Part of Epic: #<epic-number>
- Design Doc: [link if applicable]
- Phase: <which phase from design doc>

## Implementation Details
<Detailed breakdown of what was added/changed>

## Design Decisions
<Any decisions made during implementation>
<Why certain approaches were chosen>
<What alternatives were considered>

## Testing
- <Number> tests added/passing
- Coverage: <percentage>
- All tests passing ✅

## Verification Against Requirements
### From Issue:
- [x] Requirement 1
- [x] Requirement 2

### From Epic:
- [x] Fits within Phase X goals
- [x] Uses established patterns

### From Design Doc:
- [x] Follows architecture
- [x] Respects non-goals

## Files Changed
- `path/to/file.py` - Description of changes

Closes #<issue-number>

## Test Results
```
<paste key test results>
```

🤖 Generated with [Claude Code](https://claude.ai/code)
EOF
)"
```

### 10. **Final Checklist**
- [ ] All target tests passing
- [ ] Code coverage >90%
- [ ] No commented-out code
- [ ] Type hints added
- [ ] Follows patterns from design doc
- [ ] Within scope of epic
- [ ] PR created and linked to issue
- [ ] TodoWrite tasks all marked complete
- [ ] No features beyond specified scope

## Red Flags to Watch For

### Scope Creep
- Adding features not in the issue
- Implementing things listed as non-goals
- Building abstractions for single use

### Pattern Deviation
- Not using established patterns from codebase
- Ignoring architectural decisions from design doc
- Creating new patterns without justification

### Missing Context
- Implementing without reading the epic
- Ignoring design documents
- Not understanding how this fits the larger picture

## Example Context Gathering

```bash
# Issue says "Implement bar duration validator"
gh issue view 18

# Output shows "Related to #13"
gh issue view 13  # This is the Parser Completion epic

# Epic mentions "Part of Web UI Design (#12)"
gh issue view 12  # Find reference to design doc

# Found: "See design document at docs/web-ui-design.md"
cat docs/web-ui-design.md | grep -A 20 "Phase 3"

# Now you understand:
# - This is part of Phase 3.5 (Parser Completion)
# - It's needed for the Web UI
# - It should be minimal (not full validation)
# - It's week 1 of a 4-week plan
```

## Success Indicators

You know you've properly implemented an issue when:
- It solves exactly what was asked, no more, no less
- It fits cleanly into the existing architecture
- It advances the epic's goals
- It respects the design document's vision and constraints
- Other developers can understand how it fits the bigger picture
- The PR clearly shows the context and decisions made