# review-pr

Review a pull request with focus on LLM-specific code quality issues and acceptance criteria validation.

## Usage
```
/review-pr <pr-number>
```

## Review Process

### 1. Pre-Review Validation
- Fetch PR details and linked issue
- Verify all CI checks are passing
- Check test coverage meets threshold (>90%)
- Ensure no merge conflicts exist

### 2. Acceptance Criteria Audit
- Extract acceptance criteria from linked issue
- Create a mapping table: Criterion ’ Implementation ’ Test
- Flag any unimplemented criteria
- Flag any features beyond specified scope
- Verify each criterion has corresponding tests

### 3. LLM Anti-Pattern Detection

#### Placeholder Syndrome
- Search for TODO/FIXME comments
- Check for `pass` statements in non-test code
- Look for "would normally" or "in production" comments
- Verify all error messages are user-friendly, not placeholders

#### Over-Engineering
- Check if abstractions are used more than once
- Verify no unnecessary configuration files
- Ensure complexity matches problem scope
- Flag any features not in acceptance criteria

#### Context Blindness
- Compare naming conventions with existing code
- Verify error handling matches codebase patterns
- Check import organization consistency
- Ensure testing patterns match existing tests

#### Test Theater
- Verify each test has meaningful assertions
- Check for actual functionality testing, not just "runs without error"
- Ensure edge cases are covered
- Look for copy-pasted tests without adaptation

### 4. Code Quality Criteria

#### Structure
- Functions/methods under 50 lines
- Clear separation of concerns
- Appropriate use of existing utilities
- No code duplication

#### Error Handling
- All user inputs validated
- Error messages provide actionable guidance
- Consistent with existing error patterns
- No generic catch-all exceptions

#### Documentation
- Minimal but sufficient comments
- No over-explanation of obvious code
- Type hints on all public functions
- Updated relevant documentation if behavior changes

### 5. Test Quality Review
- Each test tests ONE specific behavior
- Test names clearly describe what they test
- Both happy path and error cases covered
- No hard-coded test data that could become stale

### 6. Integration Check
- Changes work with existing features
- No breaking changes unless specified
- Performance impact considered
- Database migrations if needed

## Output Format

Generate a structured review comment with:

```markdown
## PR Review: [Title]

###  Acceptance Criteria Coverage
- [x] Criterion 1: Implemented in `file.py:45-67`, tested in `test_file.py:23`
- [ ] Criterion 2: Not implemented
- [!] Additional feature in `extra.py:12` not in original scope

### =¨ LLM Anti-Patterns Detected
- **Placeholder Syndrome**: TODO comment in `module.py:34`
- **Over-Engineering**: Single-use abstraction in `utils.py:89`

### =Ê Code Quality
- Test Coverage: 92% ( meets threshold)
- Functions over 50 lines: 2 (L needs refactoring)
- Error handling: Consistent ()

### = Specific Issues

1. **Critical**: Missing validation in `handler.py:45`
   ```python
   # Current
   def process(data):
       return data['key']  # KeyError not handled
   
   # Suggested
   def process(data):
       if 'key' not in data:
           raise ValueError("Missing required field 'key'")
       return data['key']
   ```

2. **Minor**: Inconsistent naming in `models.py:23`
   - Codebase uses `snake_case`, but `userId` found

### =Ý Required Changes
1. Implement missing Criterion 2
2. Fix validation issue in `handler.py:45`
3. Remove TODO or implement in `module.py:34`
4. Refactor functions over 50 lines

###  Strengths
- Comprehensive test coverage for implemented features
- Good error messages follow project patterns
- Clean commit history

### Decision: L Changes Requested
```

## Implementation Notes

1. Use `gh pr view` to get PR details
2. Use `gh pr checks` to verify CI status
3. Read linked issue for acceptance criteria
4. Use grep/ripgrep for pattern detection
5. Generate actionable feedback with code examples
6. Be specific about line numbers and files
7. Post the review comment to the PR using `gh pr comment`

## Final Step

After generating the review, post it to the PR:
```bash
gh pr comment <pr-number> --body "$(cat <<'EOF'
[Generated review content]
EOF
)"
```