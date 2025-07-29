# design-feature

Create a comprehensive design document for a new feature or system following a structured approach.

## Usage
```
/design-feature <feature-name>
```

## Design Document Structure

### 1. Executive Summary
- One paragraph overview
- Key value proposition
- Timeline estimate

### 2. Vision
- Clear, inspiring vision statement
- Analogy or comparison (e.g., "Platform X for Domain Y")
- What success looks like

### 3. Goals
- 3-5 specific, measurable goals
- Ordered by priority
- Each goal should be achievable and verifiable

### 4. Non-Goals
- Explicitly state what we're NOT doing
- Prevent scope creep
- Set clear boundaries
- Include "future enhancements" section

### 5. User Personas
Create 2-3 personas:
- Primary persona (main user)
- Secondary personas
- Include: name, background, needs, pain points
- How this feature helps them

### 6. Feature Set
Break down by phases:
- Phase naming (descriptive, not just numbers)
- Timeline for each phase
- Features grouped logically
- Dependencies between phases

### 7. Architecture
Include:
- High-level architecture diagram (ASCII art)
- Component breakdown
- Data flow
- Technology stack with justifications
- Integration points

### 8. User Interface Design
- Layout mockups (ASCII art)
- User flow
- Key interactions
- Responsive behavior
- Accessibility considerations

### 9. Implementation Plan
- Week-by-week breakdown
- Deliverables for each week
- Testing strategy
- Deployment approach

### 10. Success Metrics
- Technical metrics (performance, reliability)
- User metrics (adoption, satisfaction)
- Business metrics (if applicable)
- How we'll measure each

### 11. Risks & Mitigations
- Technical risks
- User experience risks
- Timeline risks
- Mitigation strategy for each

### 12. Future Enhancements
- Post-MVP ideas
- Long-term vision
- What we're deliberately postponing

## Example Template

```markdown
# [Feature Name] Design Document

## Executive Summary
[One paragraph describing the feature, its purpose, and expected timeline]

## Vision
[Inspiring vision - what are we building and why?]

## Goals
1. **[Primary Goal]**: [Description]
2. **[Secondary Goal]**: [Description]
3. **[Tertiary Goal]**: [Description]

## Non-Goals
1. **[Excluded Feature]**: [Why we're not doing this]
2. **[Out of Scope]**: [Deliberately postponed]

## User Personas

### Primary: [Persona Name]
- [Background]
- [Needs]
- [How this helps]

### Secondary: [Persona Name]
- [Background]
- [Needs]
- [How this helps]

## Feature Set

### Phase 1: [Phase Name] (Week 1)
- [Feature 1]
- [Feature 2]

### Phase 2: [Phase Name] (Week 2)
- [Feature 3]
- [Feature 4]

## Architecture

### High-Level Architecture
```
[ASCII diagram]
```

### Technology Stack
- **Frontend**: [Tech] - [Justification]
- **Backend**: [Tech] - [Justification]
- **Database**: [Tech] - [Justification]

## User Interface Design

### Layout
```
[ASCII mockup]
```

### User Flow
1. User does X
2. System responds with Y
3. User can then Z

## Implementation Plan

### Week 1: [Focus Area]
- [ ] Task 1
- [ ] Task 2
- [ ] Task 3

### Week 2: [Focus Area]
- [ ] Task 4
- [ ] Task 5

## Success Metrics

### Technical Metrics
- [Metric]: [Target]
- [Metric]: [Target]

### User Metrics
- [Metric]: [Target]
- [Metric]: [Target]

## Risks & Mitigations

### Technical Risks
1. **[Risk]**: [Description]
   - Mitigation: [Strategy]

### User Experience Risks
1. **[Risk]**: [Description]
   - Mitigation: [Strategy]

## Future Enhancements (Post-MVP)
1. [Enhancement 1]
2. [Enhancement 2]
3. [Enhancement 3]

## Conclusion
[Wrap up emphasizing the value and focus]
```

## Best Practices

1. **Start with Why**: Always explain the motivation
2. **Be Specific**: Use concrete examples, not abstract descriptions
3. **Set Boundaries**: Non-goals are as important as goals
4. **Think in Phases**: Break large features into achievable chunks
5. **Consider Users First**: Every technical decision should benefit users
6. **Plan for Success**: Include metrics from the start
7. **Acknowledge Risks**: Be honest about challenges
8. **Keep it Focused**: Better to do less, well

## Output

Save the design document as:
- `/docs/[feature-name]-design.md`
- Include in PR with descriptive commit message
- Link to relevant issues

## Example Usage

```
/design-feature notification-system
```

Would create a design document for a notification system, following all the above patterns.