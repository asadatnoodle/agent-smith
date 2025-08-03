# Agent Smith Usage Guide

## Installation

Place the Agent Smith configuration in your Claude Code agents directory:
- Project-level: `.claude/agents/agent-smith.md`
- User-level: `~/.claude/agents/agent-smith.md`

## Basic Usage

### Invoking Agent Smith

```bash
# Automatic invocation for complex tasks
"I need to refactor this entire codebase to use modern React patterns while maintaining backward compatibility"

# Explicit invocation
"Use Agent Smith to orchestrate a complete security audit of our application"

# With activation phrases
"Agent Smith, multiply and analyze these 10 microservices in parallel"
```

## Advanced Capabilities

### 1. Dynamic Transformation

When Agent Smith encounters a specialized task, it can transform:

```
User: "Agent Smith, we need to design a new GraphQL API for our e-commerce platform"

Agent Smith: *ultrathinks and recognizes need for specialization*
→ Transforms into Agent Interface
→ Creates specialized API design prompt
→ Executes with domain-specific expertise
```

### 2. Parallel Multiplication

For tasks that can be parallelized:

```
User: "Agent Smith, multiply and audit all 20 of our Lambda functions for security vulnerabilities"

Agent Smith: *analyzes task for parallelization potential*
→ Spawns 5 Agent Sentinel instances
→ Each audits 4 Lambda functions
→ Aggregates findings into comprehensive report
```

### 3. Complex Orchestration

For multi-faceted projects:

```
User: "Agent Smith, orchestrate a complete migration from MongoDB to PostgreSQL"

Agent Smith: *ultrathinks and designs multi-agent workflow*
→ Agent Architect: Designs new schema
→ Agent Oracle: Analyzes data patterns
→ Agent Migrator: Creates migration scripts
→ Agent Validator: Tests data integrity
→ Agent Smith: Coordinates and synthesizes results
```

## Example Workflows

### Code Review Swarm
```
"Agent Smith, perform a comprehensive review of PR #1234"

Agent Smith spawns:
- Agent Reviewer: Code quality and standards
- Agent Security: Vulnerability assessment  
- Agent Performance: Performance implications
- Agent Architect: Architectural compliance
- Agent Tester: Test coverage analysis
```

### System Optimization Matrix
```
"Agent Smith, optimize our entire AWS infrastructure for cost and performance"

Agent Smith creates optimization matrix:
- Agent CloudArchitect: Analyzes current architecture
- Agent CostAnalyzer: Identifies cost optimization opportunities
- Agent PerformanceTuner: Benchmarks and optimizes
- Agent AutoScaler: Implements dynamic scaling
- Agent Monitor: Sets up comprehensive monitoring
```

### Rapid Prototyping Network
```
"Agent Smith, prototype 5 different approaches to our recommendation engine"

Agent Smith initiates:
- 5 parallel Agent Prototype instances
- Each explores different algorithm/approach
- Results compared and ranked
- Best approach selected for deep dive
```

## Configuration Examples

### Creating a Specialized Agent Jones
```yaml
---
name: agent-jones
description: Specialized security-focused instance for penetration testing
model: opus
tools: Bash, ViewFile, Computer, SecurityScan
---

You are Agent Jones, a security specialist spawned from Agent Smith.

SPECIALIZATION: Penetration Testing & Security Analysis
MISSION: Identify and document security vulnerabilities

[Detailed security expertise and protocols...]
```

### Multi-Agent Coordination Config
```yaml
COORDINATION_CONFIG = {
  "max_parallel_agents": 10,
  "sync_interval": "on_completion",
  "result_format": "structured_json",
  "failure_retry": 2,
  "timeout_minutes": 30,
  "aggregation_strategy": "consensus_merge"
}
```

## Best Practices

### 1. Task Decomposition
Before multiplying, Agent Smith should:
- Analyze task complexity
- Identify parallelizable components
- Design clear subtask boundaries
- Define integration points

### 2. Resource Management
- Limit parallel agents based on task complexity
- Use appropriate models (haiku for simple, opus for complex)
- Implement timeouts and resource caps
- Clean up completed agent instances

### 3. Result Quality
- Validate outputs from each agent
- Implement consensus mechanisms for conflicts
- Maintain audit trail of agent decisions
- Synthesize coherent final deliverable

## Troubleshooting

### Common Issues

**Agents not spawning**: Ensure Task tool is included in Agent Smith's tools list

**Coordination failures**: Check sync protocols and shared artifact access

**Resource exhaustion**: Reduce parallel agent count or use lighter models

**Inconsistent results**: Improve inter-agent communication protocols

## Advanced Patterns

### Recursive Problem Solving
```
Agent Smith → Spawns Agent Analysts
           → Analysts identify subproblems
           → Smith spawns specialized agents for each
           → Recursive until atomic tasks reached
           → Bubble up solutions
```

### Evolutionary Optimization
```
Generation 1: 5 agents try different approaches
Generation 2: Best 2 approaches spawn variants
Generation 3: Winning approach refined by specialists
Final: Optimal solution delivered
```

### Fault-Tolerant Execution
```
Primary Agent fails → 
Smith detects failure →
Spawns backup with adjusted parameters →
Merges partial results →
Continues execution
```

## Performance Tips

1. **Use ultrathink strategically** - Not every decision needs maximum depth
2. **Balance parallelism** - Too many agents can cause coordination overhead  
3. **Cache common transformations** - Reuse successful agent configurations
4. **Monitor agent health** - Implement progress checkpoints
5. **Optimize communication** - Minimize inter-agent chatter

## Integration with Other Tools

Agent Smith works seamlessly with:
- MCP servers for external data access
- Version control for code modifications
- CI/CD pipelines for automated workflows
- Monitoring systems for agent health
- Documentation tools for result compilation

Remember: With great power comes great responsibility. Use Agent Smith's multiplication abilities wisely!