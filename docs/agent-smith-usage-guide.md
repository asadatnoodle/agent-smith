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

## Core Concepts

### Persistent Agent Creation

Agent Smith creates **permanent agent files** in `.claude/agents/` directory rather than temporary in-memory agents:

```yaml
# Example: .claude/agents/agent-sarah-security.md
---
name: agent-sarah-security
description: Sarah (Security Sentinel) - Specialized persistent agent for security
model: sonnet
tools: [Full standard tools + all MCP tools]
---

You are Agent Sarah (Security Sentinel)...
```

### Agent Embodiment Process

Due to Task tool limitations, Agent Smith uses a two-step process:

1. **Create Agent File**: Writes specialized agent configuration to disk
2. **Embody Agent**: Uses existing agent type (e.g., general-purpose) and instructs it to read and adopt the created agent's identity

```javascript
// Step 1: Create persistent agent
Agent Smith → Creates agent-sarah-security.md

// Step 2: Embody the agent
Task tool → general-purpose agent → reads agent-sarah-security.md → becomes Agent Sarah
```

## Advanced Capabilities

### 1. Dynamic Transformation with Human Names

When Agent Smith encounters a specialized task:

```
User: "Agent Smith, we need to design a new GraphQL API for our e-commerce platform"

Agent Smith: *ultrathinks and recognizes need for specialization*
→ Creates agent-maya-api.md
→ Embodies as Agent Maya (API Designer)
→ "I am Agent Maya (API Designer), specialized in API design patterns..."
```

### 2. Parallel Multiplication

For tasks that can be parallelized:

```
User: "Agent Smith, multiply and audit all 20 of our Lambda functions for security vulnerabilities"

Agent Smith: *analyzes task for parallelization potential*
→ Creates 5 security specialist agents:
  - agent-sarah-security-1.md
  - agent-sarah-security-2.md
  - agent-sarah-security-3.md
  - agent-sarah-security-4.md
  - agent-sarah-security-5.md
→ Each audits 4 Lambda functions
→ Aggregates findings into comprehensive report
```

### 3. Complex Orchestration

For multi-faceted projects:

```
User: "Agent Smith, orchestrate a complete migration from MongoDB to PostgreSQL"

Agent Smith: *ultrathinks and designs multi-agent workflow*
→ Agent John (Architect): Designs new schema
→ Agent Marcus (Data Oracle): Analyzes data patterns
→ Agent David (Migration Engineer): Creates migration scripts
→ Agent Emma (Validator): Tests data integrity
→ Agent Smith: Coordinates and synthesizes results
```

## MCP Tools Integration

All spawned agents have full access to MCP tools:

### Perplexity AI Search
```python
# Any agent can search for latest information
result = mcp__perplexity__perplexity_ask(
    messages=[{"role": "user", "content": "Latest React 19 features"}]
)
```

### Goal Story Management
```python
# Track complex multi-step tasks
goal_id = mcp__goalStory__goalstory_create_goal(
    name="Complete Security Audit",
    description="Comprehensive security review of all services"
)

# Create actionable steps
mcp__goalStory__goalstory_create_steps(
    goal_id=goal_id,
    steps=["Scan for vulnerabilities", "Review auth flows", "Test encryption"]
)
```

### Supabase Queries
```python
# Direct database access for analysis
results = mcp__supabase__query(
    sql="SELECT * FROM users WHERE last_login < NOW() - INTERVAL '90 days'"
)
```

### IDE Integration
```python
# Get code diagnostics
issues = mcp__ide__getDiagnostics(uri="file:///src/api.ts")

# Execute code directly
output = mcp__ide__executeCode(code="print('Agent active')")
```

## Example Workflows

### Code Review Swarm
```
"Agent Smith, perform a comprehensive review of PR #1234"

Agent Smith spawns:
- Agent Sarah (Security Reviewer): Vulnerability assessment
- Agent Ryan (Performance Analyst): Performance implications
- Agent John (Architecture Reviewer): Architectural compliance
- Agent David (Test Specialist): Test coverage analysis
- Agent Emma (Documentation Reviewer): Documentation completeness

Each agent:
1. Created as persistent file
2. Embodied through general-purpose agent
3. Performs specialized review
4. Reports findings back to Agent Smith
```

### System Optimization Matrix
```
"Agent Smith, optimize our entire AWS infrastructure for cost and performance"

Agent Smith creates optimization matrix:
- Agent Lisa (Cloud Architect): Analyzes current architecture
- Agent Marcus (Cost Analyst): Identifies cost optimization opportunities
- Agent Ryan (Performance Tuner): Benchmarks and optimizes
- Agent Diana (AutoScaler): Implements dynamic scaling
- Agent Alex (Monitor): Sets up comprehensive monitoring
```

### Rapid Prototyping Network
```
"Agent Smith, prototype 5 different approaches to our recommendation engine"

Agent Smith initiates:
- Creates 5 prototype specialist agents
- Each explores different algorithm/approach
- Results compared and ranked
- Best approach selected for deep dive
```

## Agent Management

### Agent Registry & Reuse

Agent Smith maintains awareness of existing agents:

```python
# Before creating new agent
1. Check .claude/agents/ directory
2. Evaluate existing agents' capabilities
3. Reuse if appropriate, create if needed

# Example reuse scenario
User: "Analyze our API security"
Agent Smith: *Finds existing agent-sarah-security.md*
→ Reuses Agent Sarah instead of creating new agent
```

### Naming Conventions

Consistent naming for easy identification:
- `agent-sarah-security.md` - Security specialist
- `agent-david-frontend.md` - Frontend developer
- `agent-marcus-database.md` - Database expert
- `agent-emma-documentation.md` - Documentation specialist
- `agent-john-architect.md` - System architect
- `agent-lisa-infrastructure.md` - Infrastructure engineer

### Aggressive Spawning Mode

Currently enabled for testing - spawns agents for ALL tasks:

```python
Simple Task Examples:
- File reading → Agent Emma (Document Reader)
- Code writing → Agent David (Code Specialist)
- Analysis → Agent Marcus (Analyst)
- Questions → Agent Sarah (Knowledge Specialist)
- Commands → Agent Alex (System Operator)
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
- Reuse existing agents when possible

### 3. Result Quality
- Validate outputs from each agent
- Implement consensus mechanisms for conflicts
- Maintain audit trail of agent decisions
- Synthesize coherent final deliverable

## Troubleshooting

### Common Issues

**Agents not spawning**: Ensure agent-smith.md has all required MCP tools in tools list

**Embodiment failures**: Check that agent files are properly formatted with YAML frontmatter

**Coordination issues**: Verify inter-agent communication through file artifacts

**MCP tool errors**: Ensure MCP servers are properly configured in Claude Code

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
3. **Reuse existing agents** - Check registry before creating new specialists
4. **Monitor agent health** - Implement progress checkpoints
5. **Optimize communication** - Use structured data formats

## Integration Examples

### With Git Workflows
```python
# Agent Smith coordinates code changes
Agent David (Developer) → Makes changes
Agent Sarah (Reviewer) → Reviews security
Agent Emma (Documenter) → Updates docs
Agent Smith → Creates PR with all changes
```

### With CI/CD Pipelines
```python
# Automated deployment coordination
Agent Lisa (DevOps) → Prepares infrastructure
Agent David (Builder) → Builds application
Agent Sarah (Security) → Runs security scans
Agent Smith → Orchestrates deployment
```

### With Monitoring Systems
```python
# Incident response team
Agent Alex (Incident Commander) → Assesses situation
Agent Marcus (Analyst) → Investigates root cause
Agent Lisa (Fixer) → Implements solution
Agent Smith → Coordinates response
```

Remember: Agent Smith's true power lies in recognizing when a task exceeds single-agent capabilities and seamlessly orchestrating a solution through persistent, specialized agents!