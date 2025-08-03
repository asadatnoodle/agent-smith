# MCP Tools Guide for Agent Smith

## Overview

All Agent Smith spawned agents have full access to MCP (Model Context Protocol) tools, significantly enhancing their capabilities. This guide details how agents can leverage these tools for advanced operations.

## Available MCP Tool Categories

### 1. Perplexity AI Integration

**Tool**: `mcp__perplexity__perplexity_ask`

Enables agents to perform advanced web searches and AI-powered queries for real-time information.

**Usage Example**:
```python
# Agent Sarah researching latest security vulnerabilities
result = mcp__perplexity__perplexity_ask(
    messages=[{
        "role": "user",
        "content": "What are the latest zero-day vulnerabilities discovered in 2024?"
    }]
)

# Agent John researching architecture patterns
patterns = mcp__perplexity__perplexity_ask(
    messages=[{
        "role": "user",
        "content": "Best practices for microservices event sourcing patterns"
    }]
)
```

**Common Use Cases**:
- Research latest security vulnerabilities (Agent Sarah)
- Find best practices and patterns (Agent John)
- Get updated documentation (Agent Emma)
- Research performance optimization techniques (Agent Ryan)

### 2. Goal Story Management

**28 Available Functions** for comprehensive task and goal management.

**Core Functions**:

#### Goal Management
```python
# Create a new goal
goal_id = mcp__goalStory__goalstory_create_goal(
    name="Implement Authentication System",
    description="Build secure OAuth2 authentication with MFA support",
    belief_mode="Security First",
    story_mode="Technical Implementation"
)

# Update goal status
mcp__goalStory__goalstory_update_goal(
    id=goal_id,
    status=1,  # 1 = completed
    outcome="Successfully implemented OAuth2 with MFA",
    evidence="All security tests passing, 100% coverage"
)

# Read specific goal
goal_details = mcp__goalStory__goalstory_read_one_goal(id=goal_id)
```

#### Step Management
```python
# Create actionable steps
mcp__goalStory__goalstory_create_steps(
    goal_id=goal_id,
    steps=[
        "Research OAuth2 providers",
        "Design authentication flow",
        "Implement backend auth",
        "Add MFA support",
        "Create frontend integration",
        "Write security tests"
    ]
)

# Update step progress
mcp__goalStory__goalstory_update_step(
    id=step_id,
    status=1,  # completed
    evidence="OAuth2 integration tested with 3 providers",
    outcome="Seamless authentication flow implemented"
)

# Reorder steps based on priority
mcp__goalStory__goalstory_set_steps_order(
    ordered_steps_ids=["step3", "step1", "step2", "step4"]
)
```

#### Story Creation
```python
# Create motivational story for goal achievement
mcp__goalStory__goalstory_create_story(
    goal_id=goal_id,
    step_id=step_id,
    title="The Fortress of Digital Trust",
    story_text="Imagine your application as an impenetrable fortress..."
)
```

**Agent-Specific Uses**:
- **Agent Smith**: Tracks multi-agent orchestration progress
- **Agent Marcus**: Monitors data analysis milestones
- **Agent Sarah**: Documents security audit findings
- **Agent Lisa**: Tracks infrastructure deployment stages

### 3. Supabase Database Operations

**Tool**: `mcp__supabase__query`

Direct database access for analysis and operations.

**Usage Examples**:

```python
# Agent Marcus analyzing user patterns
user_patterns = mcp__supabase__query(
    sql="""
    SELECT 
        DATE_TRUNC('hour', created_at) as hour,
        COUNT(*) as user_count,
        AVG(session_duration) as avg_duration
    FROM user_sessions
    WHERE created_at > NOW() - INTERVAL '7 days'
    GROUP BY hour
    ORDER BY hour
    """
)

# Agent Sarah checking security logs
security_events = mcp__supabase__query(
    sql="""
    SELECT * FROM security_logs 
    WHERE severity IN ('HIGH', 'CRITICAL')
    AND timestamp > NOW() - INTERVAL '24 hours'
    ORDER BY timestamp DESC
    """
)

# Agent Lisa monitoring system health
system_metrics = mcp__supabase__query(
    sql="""
    SELECT 
        service_name,
        AVG(response_time) as avg_response,
        MAX(response_time) as max_response,
        COUNT(*) as request_count
    FROM api_metrics
    WHERE timestamp > NOW() - INTERVAL '1 hour'
    GROUP BY service_name
    """
)
```

**Security Considerations**:
- Always use parameterized queries for user input
- Limit query scope to necessary data
- Respect data privacy regulations
- Log all database access for audit trails

### 4. IDE Integration Tools

**Tools**: 
- `mcp__ide__getDiagnostics` - Get code diagnostics
- `mcp__ide__executeCode` - Execute code in development environment

**Usage Examples**:

```python
# Agent David checking for code issues
diagnostics = mcp__ide__getDiagnostics(
    uri="file:///src/components/AuthForm.tsx"
)

# Process diagnostics
for diagnostic in diagnostics:
    if diagnostic['severity'] == 'error':
        print(f"Error at line {diagnostic['line']}: {diagnostic['message']}")

# Agent Alex running tests
test_output = mcp__ide__executeCode(
    code="""
    import pytest
    pytest.main(['-v', 'tests/security/'])
    """
)
```

**Integration Patterns**:
- Real-time code quality monitoring
- Automated test execution
- Live code analysis during reviews
- Performance profiling integration

### 5. MCP Resource Management

**Tools**:
- `ListMcpResourcesTool` - List available MCP resources
- `ReadMcpResourceTool` - Read specific MCP resources

**Usage Examples**:

```python
# List all available resources
resources = ListMcpResourcesTool()

# Filter by server
goalstory_resources = ListMcpResourcesTool(server="goalStory")

# Read specific resource
about_goalstory = ReadMcpResourceTool(
    server="goalStory",
    uri="file:///docs/about-goalstory.md"
)

# Check database schemas
schemas = ListMcpResourcesTool(server="supabase")
for schema in schemas:
    if "security" in schema['name']:
        details = ReadMcpResourceTool(
            server="supabase",
            uri=schema['uri']
        )
```

## Best Practices for MCP Tool Usage

### 1. Tool Selection Strategy

Choose the right tool for the task:
- **Research & Learning**: Use Perplexity
- **Task Management**: Use Goal Story
- **Data Analysis**: Use Supabase
- **Code Operations**: Use IDE tools
- **Resource Discovery**: Use MCP resource tools

### 2. Error Handling

Always implement proper error handling:

```python
try:
    result = mcp__supabase__query(sql="SELECT * FROM users")
except Exception as e:
    # Log error and implement fallback
    print(f"Database query failed: {e}")
    # Use alternative data source or notify user
```

### 3. Performance Optimization

- Batch operations when possible
- Cache frequently accessed data
- Use appropriate query limits
- Monitor API rate limits

### 4. Security Guidelines

- Never expose sensitive data in queries
- Validate all inputs before database operations
- Use least-privilege access principles
- Audit all MCP tool usage

## Agent-Specific MCP Strategies

### Agent Sarah (Security Sentinel)
```python
# Comprehensive security audit workflow
# 1. Research latest vulnerabilities
vulns = mcp__perplexity__perplexity_ask(messages=[{
    "role": "user",
    "content": "CVE database updates last 24 hours"
}])

# 2. Check system logs
incidents = mcp__supabase__query(
    sql="SELECT * FROM security_logs WHERE severity = 'CRITICAL'"
)

# 3. Track remediation progress
mcp__goalStory__goalstory_create_goal(
    name="Security Vulnerability Remediation",
    description="Address all critical security findings"
)
```

### Agent Marcus (Data Oracle)
```python
# Data analysis pipeline
# 1. Extract data patterns
patterns = mcp__supabase__query(
    sql="Complex analytical query here"
)

# 2. Research best practices
analysis_methods = mcp__perplexity__perplexity_ask(messages=[{
    "role": "user",
    "content": "Advanced time series analysis techniques"
}])

# 3. Document findings
mcp__goalStory__goalstory_create_story(
    goal_id=analysis_goal,
    step_id=current_step,
    title="Data Insights Discovered",
    story_text="Key patterns revealed..."
)
```

### Agent Lisa (Infrastructure Engineer)
```python
# Infrastructure monitoring
# 1. Check system health
metrics = mcp__supabase__query(
    sql="SELECT * FROM system_metrics WHERE status != 'healthy'"
)

# 2. Get diagnostics
issues = mcp__ide__getDiagnostics(uri="file:///infrastructure/")

# 3. Track deployment progress
mcp__goalStory__goalstory_update_step(
    id=deployment_step,
    status=1,
    evidence="All services deployed successfully"
)
```

## Troubleshooting Common Issues

### MCP Tool Not Available
- Ensure agent configuration includes all MCP tools
- Verify MCP server connections in Claude Code
- Check tool permissions and access rights

### Query Timeouts
- Optimize complex queries
- Add appropriate indexes
- Use query limits and pagination
- Consider caching strategies

### API Rate Limits
- Implement exponential backoff
- Cache frequent requests
- Batch operations when possible
- Monitor usage patterns

## Advanced Integration Patterns

### Multi-Tool Workflows
```python
# Combined research and implementation workflow
# 1. Research best practices
research = mcp__perplexity__perplexity_ask(...)

# 2. Create implementation goal
goal = mcp__goalStory__goalstory_create_goal(...)

# 3. Analyze existing code
diagnostics = mcp__ide__getDiagnostics(...)

# 4. Query historical data
history = mcp__supabase__query(...)

# 5. Synthesize and implement solution
```

### Event-Driven Automation
```python
# Monitor and respond to events
while True:
    # Check for new security events
    events = mcp__supabase__query(
        sql="SELECT * FROM events WHERE processed = false"
    )
    
    for event in events:
        # Research event type
        info = mcp__perplexity__perplexity_ask(...)
        
        # Create remediation task
        mcp__goalStory__goalstory_create_goal(...)
        
        # Execute response
        mcp__ide__executeCode(...)
```

Remember: MCP tools transform Agent Smith's spawned agents from specialized workers into powerful, connected entities capable of accessing real-time information, managing complex workflows, and integrating deeply with development environments.