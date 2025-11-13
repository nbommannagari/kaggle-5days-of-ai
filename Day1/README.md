# Day 1: AI Agents Fundamentals

Welcome to Day 1 of the Kaggle 5-day AI Agents course! This folder contains two essential notebooks that introduce you to AI agent development using Google's Agent Development Kit (ADK).

## 📚 Notebooks Overview

### 1. `day-1a-from-prompt-to-action.ipynb`
**Your First AI Agent: From Prompt to Action**

This notebook introduces the fundamental concepts of AI agents and walks you through building your first agent.

**What you'll learn:**
- ✅ Install and configure Agent Development Kit (ADK)
- ✅ Set up Gemini API authentication
- ✅ Build your first simple agent
- ✅ Run your agent and watch it use tools (like Google Search)
- ✅ Explore the ADK Web Interface

**Key Concepts:**
- **AI Agent vs LLM**: Understanding the difference between simple prompt-response and agent reasoning
- **Agent Architecture**: `Prompt -> Agent -> Thought -> Action -> Observation -> Final Answer`
- **Tools Integration**: How agents can use external tools to gather information

### 2. `day-1b-agent-architectures.ipynb`
**Multi-Agent Systems & Workflow Patterns**

This notebook scales up from single agents to building collaborative agent teams.

**What you'll learn:**
- ✅ When to use multi-agent systems in ADK
- ✅ Build systems using an LLM as a "manager"
- ✅ Learn three core workflow patterns:
  - **Sequential**: Agents work one after another
  - **Parallel**: Agents work simultaneously
  - **Loop**: Agents work in iterative cycles

**Key Concepts:**
- **Multi-Agent Systems**: Creating specialized agents that collaborate
- **Workflow Orchestration**: Coordinating agent teams effectively
- **Agent Specialization**: Assigning specific roles to different agents

## 🛠️ Prerequisites

Before running these notebooks, ensure you have:

1. **Verified Kaggle Account**: Phone number verification required
2. **Gemini API Key**: Create one at [Google AI Studio](https://aistudio.google.com/app/api-keys)
3. **Kaggle Secrets Setup**: Add your `GOOGLE_API_KEY` to Kaggle secrets

## 🚀 Getting Started

### Installation
The notebooks use the pre-installed ADK library in Kaggle environment. For local development:

```bash
pip install google-adk
```

### Running the Notebooks
1. **Copy and Edit**: Click the "Copy and Edit" button in Kaggle
2. **Run Sequentially**: Execute cells one by one (avoid "Run All")
3. **Add API Key**: Configure your Gemini API key in Kaggle secrets

## 🔧 Key Components Used

### ADK Components
- **Agent**: Core agent class for building AI agents
- **Gemini**: Google's LLM model integration
- **InMemoryRunner**: Runtime orchestrator for agent execution
- **Tools**: External capabilities (google_search, custom functions)

### Multi-Agent Components
- **SequentialAgent**: For step-by-step workflows
- **ParallelAgent**: For concurrent processing
- **LoopAgent**: For iterative workflows
- **AgentTool**: For agent-to-agent communication

## 📋 Important Notes

- **No Submission Required**: These are practice notebooks only
- **Rate Limits**: Avoid "Run All" to prevent 429 errors
- **Web UI**: Explore the ADK web interface for debugging and testing
- **Security**: Never share proxy URLs (contain authentication tokens)

## 🎯 Learning Outcomes

By completing Day 1, you will:

1. **Understand Agent Fundamentals**: Grasp the difference between LLMs and agents
2. **Build Working Agents**: Create agents that can take actions and use tools
3. **Design Multi-Agent Systems**: Architect collaborative agent workflows
4. **Use ADK Effectively**: Navigate the development kit and web interface

## 🔗 Resources

- [ADK Documentation](https://google.github.io/adk-docs/)
- [ADK Python Quickstart](https://google.github.io/adk-docs/get-started/python/)
- [Agents Overview](https://google.github.io/adk-docs/agents/)
- [Tools Overview](https://google.github.io/adk-docs/tools/)
- [Kaggle Discord](https://discord.com/invite/kaggle) - For help and questions

## 🏗️ Project Structure

```
Day1/
├── day-1a-from-prompt-to-action.ipynb    # Single agent fundamentals
├── day-1b-agent-architectures.ipynb      # Multi-agent systems
└── README.md                             # This file
```

## 🎉 Next Steps

After completing Day 1, you'll be ready to:
- Build more complex agent workflows
- Implement advanced tool integrations
- Design production-ready agent systems
- Explore enterprise agent architectures

Continue to Day 2 to dive deeper into advanced agent patterns and real-world applications!

---

**Authors**: [Kristopher Overholt](http://linkedin.com/in/koverholt)

**Copyright**: 2025 Google LLC - Licensed under Apache License 2.0