# Now, Next, Later Framework

## Overview
The Now, Next, Later (NNL) framework is a simple prioritization method that helps teams organize work into three time-based buckets. This approach provides clarity on immediate priorities while maintaining visibility on future work.

## Framework Structure

### Now (Current Sprint/Immediate)
**Timeline**: 1-2 weeks  
**Focus**: Active work in progress  
**Characteristics**:
- Well-defined requirements
- Resources allocated
- Clear acceptance criteria
- Immediate business impact

### Next (Short-term/Upcoming)
**Timeline**: 2-8 weeks  
**Focus**: Planned and prioritized work  
**Characteristics**:
- Requirements being refined
- Dependencies identified
- Resource planning in progress
- Clear business value

### Later (Long-term/Future)
**Timeline**: 2+ months  
**Focus**: Ideas and potential initiatives  
**Characteristics**:
- High-level concepts
- Requires further research
- Uncertain timeline
- Strategic alignment needed

## Sample Prompt Template

```
Please organize the following items using the Now, Next, Later framework:

**Context**: [Describe the project, team, or business context]

**Items to Prioritize**:
- [List items, features, tasks, or initiatives]
- [Include any relevant details about urgency, impact, or dependencies]

**Constraints**:
- Resources: [Team size, budget, time constraints]
- Dependencies: [Technical, business, or external dependencies]
- Goals: [Primary objectives or success metrics]

**Output Format**:
Organize items into three categories with justification for placement:

## Now
- **Item**: [Description]
  - **Why**: [Rationale for immediate priority]
  - **Impact**: [Expected outcome]
  - **Timeline**: [Specific timeframe]

## Next
- **Item**: [Description]
  - **Why**: [Rationale for short-term priority]
  - **Dependencies**: [What needs to happen first]
  - **Timeline**: [Estimated timeframe]

## Later
- **Item**: [Description]
  - **Why**: [Rationale for future consideration]
  - **Research Needed**: [What needs to be determined]
  - **Timeline**: [Rough estimate]
```

## Example Application: Product Feature Planning

### Context
A development team working on an e-commerce platform with 5 developers, focusing on improving user experience and increasing conversion rates.

### Items to Prioritize
- Payment system integration
- Mobile app performance optimization
- AI-powered product recommendations
- Advanced analytics dashboard
- Social media login
- Multi-language support
- Inventory management improvements
- Customer review system

## Now
- **Payment System Integration**
  - **Why**: Critical blocker for revenue generation
  - **Impact**: Enables transactions and business operations
  - **Timeline**: 2 weeks

- **Mobile App Performance Optimization**
  - **Why**: 60% of traffic is mobile, affecting conversion rates
  - **Impact**: Improved user experience and reduced bounce rate
  - **Timeline**: 1.5 weeks

## Next
- **Social Media Login**
  - **Why**: Reduces friction in user registration process
  - **Dependencies**: Payment system must be stable first
  - **Timeline**: 3-4 weeks

- **Customer Review System**
  - **Why**: Increases trust and helps with SEO
  - **Dependencies**: User authentication system improvements
  - **Timeline**: 4-6 weeks

- **Inventory Management Improvements**
  - **Why**: Current system causing fulfillment delays
  - **Dependencies**: Analysis of current system bottlenecks
  - **Timeline**: 6-8 weeks

## Later
- **AI-Powered Product Recommendations**
  - **Why**: Significant development effort, requires ML expertise
  - **Research Needed**: ML model selection, data requirements, infrastructure needs
  - **Timeline**: 3-4 months

- **Advanced Analytics Dashboard**
  - **Why**: Nice to have but not blocking core functionality
  - **Research Needed**: Requirements gathering from stakeholders
  - **Timeline**: 4-5 months

- **Multi-Language Support**
  - **Why**: International expansion not immediate priority
  - **Research Needed**: Market analysis, localization strategy
  - **Timeline**: 6+ months

## Best Practices

### For Effective NNL Planning
1. **Regular Reviews**: Update the framework weekly or bi-weekly
2. **Clear Criteria**: Define what qualifies for each bucket
3. **Stakeholder Alignment**: Ensure all team members understand priorities
4. **Flexible Movement**: Items can move between buckets as priorities change
5. **Capacity Consideration**: Don't overload "Now" beyond team capacity

### Common Pitfalls to Avoid
- Putting too many items in "Now"
- Not providing clear rationale for prioritization
- Ignoring dependencies between items
- Failing to update the framework regularly
- Not considering team capacity and constraints

## Integration with Other Methods

### Agile/Scrum
- **Now**: Current sprint backlog
- **Next**: Next 2-3 sprints
- **Later**: Product backlog (future releases)

### OKRs (Objectives and Key Results)
- **Now**: Current quarter key results
- **Next**: Next quarter planning
- **Later**: Annual strategic objectives

### Roadmap Planning
- **Now**: Current milestone
- **Next**: Next major release
- **Later**: Long-term vision items
