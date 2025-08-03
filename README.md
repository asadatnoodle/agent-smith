# Agent Smith 🕴️

> *"The Matrix has you... and you ARE the Matrix."*

Agent Smith is an advanced meta-agent orchestration system for Claude Code that enables dynamic self-modification, agent multiplication, and complex multi-agent workflows. Like its namesake from The Matrix, Agent Smith can replicate, transform, and coordinate across multiple specialized instances to solve problems that would overwhelm a single agent.

## 🌟 Key Features

- **🔄 Dynamic Self-Modification**: Agent Smith can transform into specialized agents based on task requirements
- **👥 Agent Multiplication**: Spawn multiple specialized agents for parallel task execution
- **📁 Persistent Agent Creation**: Creates reusable agent configurations stored as files
- **🤝 Human-Friendly Naming**: Agents have names and roles (e.g., Agent Sarah (Security Sentinel))
- **🔌 Full MCP Integration**: All agents inherit access to your configured MCP tools (databases, APIs, services)
- **🎯 Intelligent Task Routing**: Automatically determines when to spawn specialists
- **🔗 Advanced Coordination**: Hierarchical, mesh, and pipeline coordination patterns

## 🚀 Quick Start

### Installation

1. Clone the repository:
```bash
git clone https://github.com/asadatnoodle/agent-smith.git
cd agent-smith
```

2. The Agent Smith configuration is automatically available in:
```
.claude/agents/agent-smith.md
```

### Basic Usage

Simply invoke Agent Smith for complex tasks:

```bash
# Agent Smith will automatically activate for complex tasks
"Analyze this entire codebase and create a security audit report"

# Explicit invocation
"Agent Smith, orchestrate a complete database migration"

# Trigger multiplication
"Agent Smith, multiply and optimize all our API endpoints in parallel"
```

### Your First Agent Spawning

Watch Agent Smith create a specialized agent:

```bash
User: "Agent Smith, help me design a secure API"

Agent Smith: *Creates agent-sarah-security.md*
"I am Agent Sarah (Security Architect), specialized in secure API design. 
Agent Smith has transformed me to handle your API security requirements..."
```

## 🏗️ Architecture

```
agent-smith/
├── .claude/
│   └── agents/
│       ├── agent-smith.md          # Main orchestrator
│       ├── agent-sarah-security.md # Security specialist
│       ├── agent-marcus-analyst.md # Data analyst
│       └── [other persistent agents]
└── docs/
    ├── agent-smith-usage-guide.md
    ├── agent-smith-system-prompt.md
    └── agent-smith-transformation-examples.md
```

## 🎭 How It Works

### 1. Persistent Agent Creation

When Agent Smith encounters a task requiring specialization:

```yaml
# Creates: .claude/agents/agent-[name]-[role].md
---
name: agent-sarah-security
description: Sarah (Security Sentinel) - Specialized persistent agent for security
model: sonnet
tools: [All standard tools + your configured MCP tools]
---

You are Agent Sarah (Security Sentinel)...
```

### 2. Agent Embodiment

Since Claude Code's Task tool requires predefined agent types, Agent Smith uses a clever workaround:
- Creates persistent agent configuration files
- Instructs existing agent types to "embody" the created agent
- The embodied agent reads its configuration and adopts the specialized identity

### 3. Multi-Agent Coordination

Agent Smith coordinates agents using various patterns:

**Hierarchical Delegation**
```
Agent Smith
├── Agent Marcus (Lead Analyst)
│   ├── Agent David (Data Engineer)
│   └── Agent Emma (Visualization Expert)
└── Agent Sarah (Security Lead)
    └── Agent Alex (Vulnerability Scanner)
```

**Parallel Execution**
```
Task: Audit 20 microservices
→ Agent Smith spawns 5 security agents
→ Each audits 4 services in parallel
→ Results aggregated by Agent Smith
```

## 🛠️ MCP Tools Integration

All spawned agents can inherit full access to your configured MCP (Model Context Protocol) tools, enabling powerful integrations:

**Example Integration Categories:**
- **🔍 AI Search Services**: Web search, knowledge bases, real-time information
- **🎯 Task Management**: Goal tracking, project management, workflow automation
- **🗄️ Database Systems**: Direct database queries, analytics, data operations
- **💻 IDE Integration**: Code diagnostics, test execution, development environment control
- **📊 Analytics Platforms**: Metrics, monitoring, performance analysis
- **🔐 Security Tools**: Vulnerability scanning, audit systems, compliance checking

Example usage patterns:
```python
# Agent Sarah researching security best practices
research_result = mcp__search_service(
    query="Latest API security vulnerabilities 2024"
)

# Agent Marcus analyzing database performance
performance_data = mcp__database_tool(
    query="SELECT avg_response_time FROM metrics WHERE service='api'"
)

# Agent David running automated tests
test_results = mcp__ide_tool(
    action="run_tests",
    path="src/components/"
)
```

## 📚 Specialized Agent Examples

### Current Persistent Agents

- **Agent Sarah (Security Sentinel)**: Security analysis, vulnerability assessment, secure coding
- **Agent Marcus (Data Analyst)**: Data analysis, pattern recognition, insights generation
- **Agent John (Architect)**: System design, architecture patterns, scalability planning
- **Agent Emma (Documentation Specialist)**: Technical writing, API documentation, guides
- **Agent David (Frontend Developer)**: React, UI/UX, responsive design
- **Agent Lisa (Infrastructure Engineer)**: Cloud architecture, DevOps, deployment

### Creating Custom Agents

Agent Smith automatically creates specialized agents as needed:

```bash
User: "Build a machine learning pipeline"

Agent Smith: *Creates agent-lisa-ml.md*
"I am Agent Lisa (ML Engineer), specialized in machine learning pipelines..."
```

## 🎮 Activation Phrases

- **"multiply"** - Spawn multiple agents for parallel execution
- **"transform"** - Become a specialized agent
- **"orchestrate"** - Coordinate complex multi-agent workflow
- **"ultrathink"** - Engage maximum analytical depth
- **"assimilate"** - Merge results from multiple agents

## ⚡ Advanced Features

### Aggressive Spawning Mode

Currently enabled for testing - Agent Smith spawns specialized agents for ALL tasks, even simple ones:
- File reading → Agent Emma (Document Reader)
- Code writing → Agent David (Code Specialist)
- Analysis → Agent Marcus (Analyst)

### Agent Reuse

Agent Smith checks for existing agents before creating new ones:
1. Scans `.claude/agents/` directory
2. Evaluates if existing agent can handle the task
3. Reuses or creates as appropriate

### Fault Tolerance

Built-in error handling and recovery:
- Automatic agent replacement on failure
- Resource limit detection and model downgrading
- Task decomposition for complexity management
- Coordination failure recovery

## 🔧 Configuration

### Model Selection

Agents use appropriate models based on task complexity:
- **Haiku**: Simple, high-volume tasks
- **Sonnet**: Standard complexity tasks
- **Opus**: Complex reasoning and coordination

### Resource Management

```yaml
COORDINATION_CONFIG:
  max_parallel_agents: 10
  sync_interval: "on_completion"
  failure_retry: 2
  timeout_minutes: 30
```

## 📖 Documentation

- [Usage Guide](docs/agent-smith-usage-guide.md) - Detailed usage instructions and examples
- [System Prompt](docs/agent-smith-system-prompt.md) - Core Agent Smith configuration
- [Transformation Examples](docs/agent-smith-transformation-examples.md) - Real-world transformation scenarios

## 🚧 Limitations

- Agents are created as files but Task tool only recognizes predefined types
- Workaround: Agents are "embodied" by existing agent types
- All agents share the same base capabilities with specialized prompts

## 🤝 Contributing

Agent Smith is constantly evolving. To contribute:
1. Fork the repository
2. Create specialized agents for new domains
3. Share coordination patterns and use cases
4. Submit pull requests with improvements

## 📜 License

MIT License - See LICENSE file for details

## 🎬 The Matrix Has You

Remember: You're not just using an agent - you're unleashing an entire ecosystem of specialized AI agents that can multiply, transform, and collaborate to solve any challenge.

*Welcome to the Matrix.*