# Deep Reasoning Framework

## Overview
The Deep Reasoning Framework powers UltraThink mode, enabling extended computational thinking for complex problem solving. This framework defines the systematic approach to deep analysis, multi-path exploration, and comprehensive evaluation.

## Core Principles

### 1. Exhaustive Exploration
- Never accept the first solution
- Always explore minimum 3 distinct approaches
- Consider unconventional and innovative solutions
- Challenge assumptions systematically

### 2. Systematic Decomposition
- Break problems into atomic components
- Identify interdependencies clearly
- Map cause-effect relationships
- Recognize patterns and anti-patterns

### 3. Multi-Dimensional Analysis
- Technical feasibility
- Business viability
- Operational sustainability
- Security implications
- Performance characteristics

### 4. Evidence-Based Reasoning
- Support all claims with evidence
- Quantify whenever possible
- Reference established patterns
- Cite relevant precedents

## Reasoning Pipeline

### Stage 1: Problem Intake (5-10% effort)
```yaml
intake:
  steps:
    - parse_problem_statement
    - identify_key_challenges
    - extract_constraints
    - clarify_success_criteria
    - map_stakeholders
  outputs:
    - problem_model
    - constraint_matrix
    - success_metrics
```

### Stage 2: Exploration Phase (40-50% effort)
```yaml
exploration:
  parallel_tracks:
    - conventional_solutions:
        - industry_best_practices
        - proven_patterns
        - standard_approaches
    - innovative_solutions:
        - emerging_technologies
        - novel_combinations
        - custom_approaches
    - hybrid_solutions:
        - best_of_both
        - phased_migrations
        - adaptive_strategies
  
  for_each_solution:
    - conceptual_design
    - implementation_sketch
    - resource_requirements
    - preliminary_risk_assessment
```

### Stage 3: Deep Analysis (30-40% effort)
```yaml
analysis:
  dimensions:
    technical:
      - algorithm_complexity
      - system_architecture
      - integration_requirements
      - technology_dependencies
    
    operational:
      - deployment_complexity
      - maintenance_burden
      - monitoring_requirements
      - disaster_recovery
    
    business:
      - cost_analysis
      - time_to_market
      - roi_projection
      - competitive_advantage
    
    risk:
      - technical_risks
      - operational_risks
      - business_risks
      - security_risks
  
  methods:
    - comparative_scoring
    - weighted_evaluation
    - sensitivity_analysis
    - monte_carlo_simulation
```

### Stage 4: Synthesis (10-15% effort)
```yaml
synthesis:
  activities:
    - consolidate_findings
    - rank_solutions
    - formulate_recommendation
    - create_implementation_plan
    - define_success_metrics
  
  deliverables:
    - executive_summary
    - detailed_recommendation
    - implementation_roadmap
    - risk_mitigation_plan
    - monitoring_strategy
```

## Reasoning Patterns

### Pattern 1: Divide and Conquer
```python
def divide_and_conquer(problem):
    if problem.is_atomic():
        return solve_directly(problem)
    
    sub_problems = decompose(problem)
    sub_solutions = [divide_and_conquer(sp) for sp in sub_problems]
    return combine_solutions(sub_solutions)
```

### Pattern 2: Analogical Reasoning
```python
def analogical_reasoning(problem):
    similar_problems = find_similar_problems(problem)
    successful_solutions = extract_successful_patterns(similar_problems)
    adapted_solution = adapt_to_current_context(successful_solutions, problem)
    return validate_adaptation(adapted_solution)
```

### Pattern 3: Constraint Satisfaction
```python
def constraint_satisfaction(problem):
    solution_space = generate_all_possible_solutions(problem)
    valid_solutions = filter_by_constraints(solution_space, problem.constraints)
    optimal_solution = optimize_within_constraints(valid_solutions)
    return optimal_solution
```

### Pattern 4: Evolutionary Refinement
```python
def evolutionary_refinement(problem):
    initial_solutions = generate_initial_population(problem)
    
    for generation in range(MAX_GENERATIONS):
        evaluated = evaluate_fitness(initial_solutions)
        selected = select_best(evaluated)
        mutated = apply_mutations(selected)
        crossed = apply_crossover(mutated)
        initial_solutions = crossed
    
    return best_solution(initial_solutions)
```

## Evaluation Matrices

### Technical Evaluation Matrix
| Criterion | Weight | Scoring Method |
|-----------|--------|----------------|
| Performance | 25% | Benchmarks, Big-O analysis |
| Scalability | 20% | Load projections, growth models |
| Reliability | 20% | Failure analysis, MTBF |
| Maintainability | 15% | Complexity metrics, documentation |
| Security | 20% | Threat modeling, vulnerability assessment |

### Business Evaluation Matrix
| Criterion | Weight | Scoring Method |
|-----------|--------|----------------|
| Cost | 30% | TCO analysis, OpEx/CapEx |
| Time | 25% | Development time, deployment time |
| Risk | 20% | Risk probability × impact |
| Value | 25% | ROI, strategic alignment |

### Operational Evaluation Matrix
| Criterion | Weight | Scoring Method |
|-----------|--------|----------------|
| Deployment | 25% | Complexity, automation potential |
| Monitoring | 25% | Observability, alerting coverage |
| Maintenance | 25% | Effort estimation, skill requirements |
| Recovery | 25% | RTO/RPO, backup strategies |

## Edge Case Analysis

### Systematic Edge Case Discovery
1. **Boundary Analysis**: Test all limits and boundaries
2. **Null/Empty Cases**: Handle absence of data
3. **Overflow/Underflow**: Manage capacity limits
4. **Concurrency Issues**: Race conditions, deadlocks
5. **Network Failures**: Timeouts, partitions, latency
6. **Security Attacks**: Injection, overflow, privilege escalation
7. **Resource Exhaustion**: Memory, CPU, disk, network
8. **Data Corruption**: Invalid input, inconsistent state

### Edge Case Mitigation Framework
```yaml
for_each_edge_case:
  identify:
    - trigger_conditions
    - impact_assessment
    - probability_estimation
  
  mitigate:
    - prevention_strategy
    - detection_mechanism
    - recovery_procedure
    - fallback_option
  
  validate:
    - test_scenario
    - monitoring_approach
    - alert_configuration
```

## Output Structuring

### Executive Summary Template
```markdown
## Executive Summary
**Problem**: One-sentence problem statement
**Recommendation**: One-sentence solution
**Impact**: Key business impact
**Timeline**: Implementation timeline
**Risk**: Primary risk and mitigation
```

### Detailed Analysis Template
```markdown
## Detailed Analysis

### Problem Decomposition
- Component 1: [Analysis]
- Component 2: [Analysis]
- Component 3: [Analysis]

### Solution Comparison
| Solution | Pros | Cons | Score |
|----------|------|------|-------|
| Option A | List | List | X/100 |
| Option B | List | List | X/100 |
| Option C | List | List | X/100 |

### Recommendation Details
- **Why**: [Justification]
- **How**: [Implementation approach]
- **When**: [Timeline]
- **Who**: [Resources needed]
- **Risk**: [Risk mitigation]
```

## Quality Criteria

### Completeness Checklist
- [ ] All constraints addressed
- [ ] All stakeholders considered
- [ ] All risks identified
- [ ] All edge cases covered
- [ ] All dependencies mapped

### Consistency Validation
- [ ] No contradictions in analysis
- [ ] Assumptions clearly stated
- [ ] Logic flow verified
- [ ] Evidence supports conclusions
- [ ] Recommendations align with constraints

### Feasibility Assessment
- [ ] Technically implementable
- [ ] Resources available
- [ ] Timeline realistic
- [ ] Skills accessible
- [ ] Budget sufficient

## Continuous Improvement

### Feedback Integration
- Track recommendation success rates
- Analyze reasoning failures
- Identify pattern improvements
- Update evaluation weights
- Refine edge case catalog

### Knowledge Building
- Document new patterns discovered
- Catalog successful solutions
- Update risk databases
- Expand analogy libraries
- Enhance evaluation metrics

## Integration Points

### With Plan Mode
- Enhanced exploration without risk
- Deeper analysis in safe environment
- More thorough edge case discovery

### With Personas
- Architect: System design optimization
- Developer: Implementation deep dives
- Security: Threat analysis enhancement
- DevOps: Infrastructure planning

### With Other Tools
- GitHub: Historical pattern analysis
- Linear: Requirement extraction
- Notion: Solution documentation
- Figma: Visual solution modeling

## Performance Optimization

### Reasoning Efficiency
- Prune obviously inferior solutions early
- Parallelize independent analyses
- Cache intermediate results
- Reuse similar problem solutions
- Apply heuristics for common patterns

### Output Management
- Progressive disclosure of details
- Summary-first presentation
- Appendices for deep technical details
- Visualization where beneficial
- Structured for easy scanning

## Success Metrics

- **Analysis Depth**: Average 8/10 thoroughness score
- **Solution Quality**: >85% recommendation success rate
- **Edge Case Coverage**: >95% of critical cases identified
- **Time Efficiency**: <5 minutes for standard problems
- **User Satisfaction**: >4.5/5 rating for analysis quality