# Day 2: Agent Tools and Advanced Patterns

Welcome to Day 2 of the Kaggle 5-day AI Agents course! This folder contains two comprehensive notebooks that teach you how to build powerful, production-ready agent tools and implement advanced workflow patterns.

## 📚 Notebooks Overview

### 1. `day-2a-agent-tools.ipynb`
**Agent Tools: From Custom Functions to Multi-Tool Systems**

This notebook teaches you how to transform Python functions into agent tools and build sophisticated multi-tool agents.

**What you'll learn:**
- ✅ Turn Python functions into Agent tools
- ✅ Build an Agent and use it as a tool in another agent
- ✅ Build your first multi-tool agent
- ✅ Explore different tool types in ADK
- ✅ Implement code execution for reliable calculations

**Key Projects:**
- **Currency Converter Agent**: Multi-tool system with fee lookup and exchange rates
- **Enhanced Currency Agent**: Delegates calculations to specialist code execution agent
- **Tool Architecture**: Function Tools + Agent Tools + Built-in Code Executor

### 2. `day-2b-agent-tools-best-practices.ipynb`
**Agent Tool Patterns and Best Practices**

This notebook covers advanced patterns for connecting to external systems and handling long-running operations.

**What you'll learn:**
- ✅ Connect to external MCP (Model Context Protocol) servers
- ✅ Implement long-running operations with human-in-the-loop
- ✅ Build resumable workflows that maintain state
- ✅ Handle approval workflows and compliance checkpoints

**Key Projects:**
- **MCP Integration**: Connect to external services using standardized protocols
- **Shipping Coordinator**: Long-running operations with approval workflows
- **Resumable Workflows**: State management across conversation breaks

## 🛠️ Core Concepts Covered

### Custom Tools Architecture

#### **Function Tools**
```python
def get_exchange_rate(base_currency: str, target_currency: str) -> dict:
    """Converts Python functions into agent tools"""
    # Business logic with structured returns
    return {"status": "success", "rate": 0.93}
```

#### **Agent Tools**
```python
AgentTool(agent=calculation_agent)  # Use agents as tools
```

#### **Built-in Tools**
- **Code Executor**: Reliable mathematical calculations
- **Google Search**: Real-time information access
- **MCP Tools**: External service integration

### Advanced Patterns

#### **Model Context Protocol (MCP)**
- Connect to external systems without custom integration
- Standardized interface for community-built tools
- Examples: GitHub, Slack, databases, file systems

#### **Long-Running Operations (LRO)**
- Human-in-the-loop approval workflows
- Pausable and resumable agent execution
- State persistence across conversation breaks

## 🏗️ Technical Implementation

### Tool Development Best Practices

1. **Dictionary Returns**: Structured responses with status indicators
2. **Clear Docstrings**: LLM-friendly documentation
3. **Type Hints**: Enable proper schema generation
4. **Error Handling**: Graceful failure management

### Workflow Patterns

#### **Sequential Workflow**
```
User Request → Tool 1 → Tool 2 → Agent Response
```

#### **Approval Workflow**
```
User Request → Tool Pause → Human Decision → Tool Resume → Agent Response
```

#### **MCP Integration**
```
Agent → MCP Toolset → External Server → Response → Agent
```

## 🔧 Key Components Used

### ADK Components
- **LlmAgent**: Core agent with tool capabilities
- **FunctionTool**: Wrapper for Python functions
- **AgentTool**: Use agents as tools
- **McpToolset**: External service integration
- **BuiltInCodeExecutor**: Reliable code execution

### Advanced Components
- **App**: Resumable agent wrapper
- **ResumabilityConfig**: State persistence configuration
- **ToolContext**: Long-running operation context
- **Runner**: Execution orchestrator with session management

## 📋 Prerequisites

Before running these notebooks, ensure you have:

1. **Completed Day 1**: Understanding of basic agent concepts
2. **Gemini API Key**: Configured in Kaggle secrets
3. **Node.js Environment**: For MCP server examples (handled automatically in Kaggle)

## 🚀 Getting Started

### Installation
```bash
pip install google-adk
```

### Running the Notebooks
1. **Copy and Edit**: Create your own copy in Kaggle
2. **Sequential Execution**: Run cells one by one to avoid rate limits
3. **API Configuration**: Ensure GOOGLE_API_KEY is set in secrets

## 🎯 Learning Outcomes

By completing Day 2, you will:

1. **Master Tool Development**: Create custom tools following ADK best practices
2. **Implement Multi-Tool Systems**: Build agents that coordinate multiple tools
3. **Connect External Services**: Integrate with MCP servers and external APIs
4. **Handle Complex Workflows**: Implement approval processes and long-running operations
5. **Manage State**: Build resumable workflows that persist across interruptions

## 🔗 Tool Types Reference

### Custom Tools
| Type | Use Case | Example |
|------|----------|---------|
| **Function Tools** | Business logic | Currency conversion, fee calculation |
| **Agent Tools** | Specialist delegation | Code execution, data analysis |
| **MCP Tools** | External integration | GitHub, Slack, databases |
| **OpenAPI Tools** | REST API access | Automated API client generation |

### Built-in Tools
| Type | Use Case | Example |
|------|----------|---------|
| **Gemini Tools** | Core capabilities | Google Search, Code Execution |
| **Google Cloud Tools** | Enterprise integration | BigQuery, Spanner, API Hub |
| **Third-party Tools** | Ecosystem integration | Hugging Face, Firecrawl |

## 🎬 Demo Scenarios

### Currency Converter Demo
- Multi-tool coordination (fees + rates + calculation)
- Error handling and validation
- Code execution for reliable math

### Shipping Coordinator Demo
- Approval workflow implementation
- State persistence and resumption
- Human-in-the-loop decision making

### MCP Integration Demo
- External service connection
- Standardized tool interface
- Community tool leverage

## 📊 Production Patterns

### When to Use Each Pattern

| Pattern | Use Case | Key Benefits |
|---------|----------|--------------|
| **MCP Integration** | External services | No custom integration code |
| **Long-Running Operations** | Approval workflows | Human oversight, compliance |
| **Multi-Tool Agents** | Complex tasks | Specialized tool coordination |
| **Code Execution** | Calculations | Reliability over LLM math |

## 🔒 Security and Compliance

- **Approval Checkpoints**: Human oversight for critical operations
- **State Validation**: Secure resumption mechanisms
- **Error Boundaries**: Graceful failure handling
- **Access Control**: Tool-level permission management

## 🎯 Next Steps

After completing Day 2, you'll be ready to:
- Build production-ready agent systems
- Implement complex business workflows
- Integrate with external services and APIs
- Handle enterprise-grade approval processes
- Design scalable multi-agent architectures

Continue to Day 3 to learn about **State and Memory Management** for even more sophisticated agent systems!

## 📚 Additional Resources

- [ADK Documentation](https://google.github.io/adk-docs/)
- [ADK Tools Documentation](https://google.github.io/adk-docs/tools/)
- [MCP Specification](https://spec.modelcontextprotocol.io/)
- [Function Tools Guide](https://google.github.io/adk-docs/tools/function-tools/)
- [Kaggle Discord](https://discord.com/invite/kaggle) - For help and questions

---

**Authors**: [Laxmi Harikumar](https://www.linkedin.com/in/laxmi-harikumar/)

**Copyright**: 2025 Google LLC - Licensed under Apache License 2.0