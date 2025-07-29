# Resume Work

Resume implementation work after a context switch or break, quickly understanding current state and next steps.

## Usage
Use this command when returning to an in-progress implementation to quickly regain context and continue work efficiently.

## Process

### 1. Assess Current State (5 mins)
```bash
# Check git status and current branch
git status
git branch --show-current
git log --oneline -5

# Review any active todo list
# The TodoWrite tool will show current tasks and their status
```

### 2. Understand Test Status
```bash
# Run tests to see current pass/fail state
python3 -m pytest tests/ -v --tb=short | grep -E "(PASSED|FAILED|ERROR)"

# If specific test file is being worked on, run it
python3 -m pytest tests/test_*.py -v --tb=short
```

### 3. Identify Current Blocker
- Look for the last failing test in the output
- Check any debug scripts in the root directory (test_*.py)
- Review the last few commits to understand what was implemented

### 4. Review Implementation Context
```bash
# Check CLAUDE.md for project-specific guidelines
cat CLAUDE.md | grep -A 10 -B 10 "Development Process"

# Check the issue being worked on (if known)
gh issue view <number>

# Review any design documents or issue descriptions
ls -la *.md | grep -E "(design|phase|plan)"
```

### 5. Analyze Current Error
If there's a specific test failure:
1. Run the failing test in verbose mode
2. Add debug output if needed
3. Check the parse tree or intermediate representations
4. Verify the implementation matches the expected behavior

### 6. Create Recovery Plan
Based on the assessment, create a focused plan:
1. Fix the immediate blocker
2. Run the specific failing test
3. Run the full test suite for the module
4. Move to the next failing test

## Recovery Patterns

### Pattern 1: Mid-Test-Fix
If stopped while fixing a specific test:
```bash
# Re-run the specific test that was being fixed
python3 -m pytest path/to/test.py::TestClass::test_method -xvs

# Check any debug output
python3 test_debug.py  # if exists
```

### Pattern 2: Multi-File Changes
If changes span multiple files:
```bash
# See what files were modified
git diff --name-only

# Review changes in each file
git diff <filename>
```

### Pattern 3: Narrow Issues
If working on narrow, focused issues:
```bash
# Test parsing with a minimal example
python3 -c "
from myproject.parser import parse
result = parse('test input here')
print(result)
"
```

### Pattern 4: Environment/State Issues
If dealing with environment or state propagation:
- Check environment.py for current implementation
- Verify directives are being processed in correct order
- Add debug prints to trace environment changes

## Quick Checklist
- [ ] Git status checked
- [ ] Current branch confirmed
- [ ] Test status understood
- [ ] Current blocker identified
- [ ] Next steps clear
- [ ] TodoWrite updated with current progress

## Example Recovery

```bash
# 1. Check where we are
git status
git log --oneline -3

# 2. Check test status
python3 -m pytest tests/test_pitch_representation.py -v --tb=short | grep -E "(PASSED|FAILED)"

# 3. If there's a failing test, run it specifically
python3 -m pytest tests/test_pitch_representation.py::TestPitchRepresentation::test_mode_switching -xvs

# 4. Check for debug scripts
ls test_*.py

# 5. Update todo list and continue
# Use TodoWrite to mark completed items and see what's next
```

## Key Questions to Answer
1. What feature/phase am I implementing?
2. What tests are currently failing?
3. What was the last thing I successfully fixed?
4. What's the immediate next step?
5. Are there any architectural decisions I need to remember?

## Common Issues and Solutions

### Issue: "I don't know which test to run"
→ Run all tests and look for the first failure

### Issue: "The error doesn't make sense"
→ Create a minimal reproduction script

### Issue: "I've lost track of what's implemented"
→ Check the git diff and test coverage

### Issue: "The design has gotten complex"
→ Re-read the issue description and simplify

Remember: The goal is to quickly get back to productive work, not to understand every detail. Focus on the immediate blocker and trust the tests to guide you.