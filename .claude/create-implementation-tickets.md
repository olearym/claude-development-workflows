# create-implementation-tickets

Break down an epic into detailed implementation tickets following a consistent structure.

## Usage
```
/create-implementation-tickets <epic-number>
```

## Ticket Creation Process

### 1. Analyze the Epic
- Read the epic description and goals
- Identify logical work units
- Determine dependencies between tasks
- Plan for parallel work where possible

### 2. Break Down into Tickets
Each epic typically needs:
- **Setup/Configuration tickets** (environment, dependencies)
- **Core implementation tickets** (main functionality)
- **Integration tickets** (connecting components)
- **Testing tickets** (if not included in implementation)
- **Documentation tickets** (API docs, user guides)

### 3. Ticket Structure

Each ticket MUST include:

```markdown
## Overview
[1-2 sentences describing what this ticket accomplishes]

## Background
[Context about why this is needed, how it fits into the larger epic]

## Requirements
[Bullet list of specific requirements, numbered if sequential]

## Implementation Details
[Detailed technical approach with code examples]

## Testing Requirements
[Specific test cases or testing approach]

## Definition of Done
- [ ] [Specific, measurable completion criteria]
- [ ] [Each item should be verifiable]
- [ ] [Include testing and documentation]

Related to #[epic-number]
```

## Ticket Template

```markdown
## Overview
[Clear, concise description of the ticket's purpose]

## Background
[Why this work is needed and how it connects to the epic's goals]

## Requirements

### Functional Requirements
1. [Requirement 1]
2. [Requirement 2]
3. [Requirement 3]

### Non-Functional Requirements
- Performance: [Specific metrics]
- Security: [Specific considerations]
- Scalability: [Specific limits]

## Implementation Details

### Approach
[High-level approach in 2-3 sentences]

### File Structure
```
path/to/files/
├── new_file.py
├── modified_file.py
└── tests/
    └── test_new_feature.py
```

### Code Examples
```python
# Example implementation
def example_function():
    """Show key patterns or interfaces."""
    pass
```

### Integration Points
- Integrates with: [Component A]
- Depends on: [Component B]
- Used by: [Component C]

## Testing Requirements

### Unit Tests
```python
def test_example():
    """Test specific behavior."""
    # Test implementation
```

### Integration Tests
- Test with [Component X]
- Verify [Behavior Y]

### Edge Cases
1. [Edge case 1]
2. [Edge case 2]

## Definition of Done
- [ ] Implementation complete with all requirements met
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [ ] Code reviewed and approved
- [ ] Documentation updated
- [ ] No linting errors
- [ ] Performance requirements met

Related to #[epic-number]
```

## Best Practices

### 1. Ticket Sizing
- Each ticket should be completable in 1-3 days
- If larger, break into subtasks
- If smaller, consider combining

### 2. Ticket Titles
- Start with action verb (Implement, Create, Add, Fix, Update)
- Be specific: "Implement user authentication" not "Auth"
- Include component name if relevant

### 3. Code Examples
- Include actual code, not pseudocode
- Show the pattern, not the entire implementation
- Include imports and context
- Add comments explaining key decisions

### 4. Dependencies
- Explicitly state what must be done first
- Link to blocking tickets
- Note if work can be done in parallel

### 5. Testing Focus
- Every ticket needs testing criteria
- Include example test cases
- Specify coverage requirements
- Note performance benchmarks

## Common Ticket Types

### Setup Ticket
```
Title: "Setup [Component] project structure"
- Initialize project
- Configure dependencies
- Set up development environment
- Create initial tests
```

### Implementation Ticket
```
Title: "Implement [Feature] in [Component]"
- Core logic implementation
- Error handling
- Input validation
- Unit tests
```

### Integration Ticket
```
Title: "Integrate [Component A] with [Component B]"
- Define interfaces
- Implement adapters
- Handle errors across boundaries
- Integration tests
```

### API Endpoint Ticket
```
Title: "Create [HTTP Method] /api/[endpoint]"
- Request/response models
- Business logic
- Validation
- Error responses
- API documentation
- Tests
```

### UI Component Ticket
```
Title: "Create [Component] UI component"
- Component structure
- Props interface
- Event handlers
- Styling
- Accessibility
- Unit tests
- Storybook story
```

## Example Breakdown

For Epic: "User Authentication System"

1. **Setup ticket**: "Setup authentication service structure"
2. **Core tickets**:
   - "Implement user registration endpoint"
   - "Implement login endpoint"
   - "Create JWT token generation"
3. **Integration tickets**:
   - "Add authentication middleware"
   - "Integrate auth with user service"
4. **UI tickets**:
   - "Create login form component"
   - "Create registration form component"
5. **Documentation ticket**: "Document authentication API"

## GitHub Commands

Use these commands to create tickets efficiently:

```bash
# Create single ticket
gh issue create --title "Title" --body "$(cat <<'EOF'
[Ticket content]
EOF
)"

# Create multiple tickets in parallel
# Run multiple commands with different content
```

## Output

When complete:
1. List all created ticket numbers
2. Suggest priority order
3. Identify which can be done in parallel
4. Note any additional tickets that might be needed

## Success Criteria

Good implementation tickets:
- Can be understood by any developer
- Have clear acceptance criteria
- Include enough detail to start work immediately
- Don't duplicate information unnecessarily
- Link back to the epic for context