# Respond to PR Review

Systematically address feedback from a pull request review.

## Usage
Use this command when a PR has received review comments that need to be addressed.

## Process

1. **Read the Review**
   ```bash
   gh pr view <pr-number> --comments
   ```
   - Read through all comments carefully
   - Make notes of required changes vs suggestions
   - Identify any questions that need clarification

2. **Analyze and Plan**
   - Think step-by-step about what changes are needed
   - Categorize feedback:
     - Critical issues (must fix)
     - Good suggestions (should implement)
     - Optional improvements (consider for later)
   - Create a mental or written checklist

3. **Implement Changes**
   - Address critical issues first
   - For each change:
     - Make the modification
     - Run relevant tests to ensure nothing broke
     - Consider if the change affects other parts
   
4. **Common Review Items**
   - **"Binary file in PR"** → Add to .gitignore and remove from git
   - **"Missing type hints"** → Add type annotations to all functions
   - **"Error message could be clearer"** → Enhance with more context
   - **"Consider thread safety"** → Add documentation about limitations
   - **"Missing test coverage"** → Add tests if critical path

5. **Test Everything**
   ```bash
   # Run all tests to ensure changes didn't break anything
   python3 -m pytest -v
   
   # Check coverage if mentioned in review
   python3 -m pytest --cov=src --cov-report=term-missing
   ```

6. **Commit the Changes**
   ```bash
   git add -A
   git commit -m "chore: Address PR review feedback

   - <List each change made>
   - <Be specific about what was modified>
   
   All tests still passing with X% coverage.
   
   🤖 Generated with [Claude Code](https://claude.ai/code)
   
   Co-Authored-By: Claude <noreply@anthropic.com>"
   ```

7. **Push and Respond**
   ```bash
   git push
   ```
   
   Then post a summary comment:
   ```bash
   gh pr comment <pr-number> --body "## Updates Based on Review Feedback
   
   Thank you for the thorough review! I've addressed all the feedback in commit <sha>:
   
   ### ✅ Implemented Changes
   
   1. **<Issue 1>**
      - <What was done>
      - <Include code snippet if relevant>
   
   2. **<Issue 2>**
      - <What was done>
   
   ### 📊 Test Results
   
   All tests still passing with X% coverage:
   ```
   <Include test summary>
   ```
   
   ### Next Steps
   
   <Note any suggestions saved for future phases>
   
   Thanks again for the excellent review!"
   ```

8. **Follow Up**
   - Monitor for any additional comments
   - Be prepared to make further adjustments
   - Thank reviewers for their time

## Key Principles

- **Be Grateful**: Reviews improve code quality
- **Be Thorough**: Address all points raised
- **Be Clear**: Explain what was changed and why
- **Be Professional**: Keep responses positive and constructive

## Example Scenarios

### Scenario 1: Minor Issues
- Fix formatting/style issues
- Add missing documentation
- Simple one-line changes

### Scenario 2: Design Feedback
- May require more substantial changes
- Discuss trade-offs if needed
- Explain implementation decisions

### Scenario 3: Out of Scope
- Politely note items for future phases
- Create issues for tracking if needed
- Focus on current PR scope