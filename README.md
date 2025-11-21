# Kaggle 5 Days of AI Agents Intensive Course

A comprehensive 5-day journey through AI agent development using Google's Agent Development Kit (ADK), progressing from basic concepts to production-ready deployments.

## Course Overview

This intensive course teaches you to build, test, and deploy production-ready AI agents through hands-on notebooks and practical projects. Each day builds upon the previous, creating a complete learning path from fundamentals to enterprise deployment.

## Daily Breakdown

### 📚 [Day 1: AI Agents Fundamentals](./Day1/)
**Foundation: From Prompt to Action & Multi-Agent Systems**

Learn the core concepts of AI agents and build your first working systems. Understand the difference between LLMs and agents, explore agent architecture patterns, and create collaborative multi-agent workflows. Master the ADK fundamentals including tools integration, workflow orchestration, and the web interface for debugging. Build sequential, parallel, and loop-based agent patterns while learning when to use single vs multi-agent approaches.

### 🛠️ [Day 2: Agent Tools and Advanced Patterns](./Day2/)
**Tools: Custom Functions to Multi-Tool Systems & Best Practices**

Transform Python functions into powerful agent tools and build sophisticated multi-tool systems. Learn to create custom tools, integrate external services via MCP (Model Context Protocol), and implement long-running operations with human-in-the-loop workflows. Master tool architecture patterns, approval workflows, and resumable state management. Build production-ready currency converters and shipping coordinators with proper error handling and validation.

### 🧠 [Day 3: Memory Management and State Persistence](./Day3/)
**Memory: Sessions & Long-term Knowledge Storage**

Build stateful agents with persistent memory across conversations and sessions. Master session management with event tracking and state persistence, implement context compaction for efficient long conversations, and create memory systems that learn across multiple interactions. Learn automated memory operations using callbacks, semantic search for knowledge retrieval, and the difference between short-term session state and long-term memory consolidation.

### 🔍 [Day 4: Agent Observability and Evaluation](./Day4/)
**Quality: Monitoring, Debugging & Systematic Testing**

Implement comprehensive observability with logs, traces, and metrics for production debugging and monitoring. Build systematic evaluation frameworks to catch performance regressions and ensure consistent quality. Master the debug workflow from symptoms to root cause analysis, create automated testing suites with response matching and tool trajectory scoring, and implement quality gates for deployment pipelines.

### 🚀 [Day 5: Agent Communication & Production Deployment](./Day5/)
**Scale: A2A Protocol & Enterprise Deployment**

Deploy agents to production using Vertex AI Agent Engine and enable cross-organization communication via Agent2Agent (A2A) Protocol. Learn to expose agents as services with auto-generated agent cards, consume remote agents as local tools, and build microservices-based agent architectures. Master production deployment patterns, resource management, cost optimization, and enterprise integration scenarios with proper monitoring and cleanup practices.

## Key Technologies

- **Google Agent Development Kit (ADK)**: Primary framework for agent development
- **Gemini Models**: LLM backend (gemini-2.5-flash-lite for efficiency)
- **Vertex AI Agent Engine**: Production deployment platform
- **Agent2Agent (A2A) Protocol**: Cross-organization agent communication standard
- **Model Context Protocol (MCP)**: External service integration
- **Memory Bank**: Long-term knowledge storage and retrieval

## Learning Progression

```
Day 1: Basic Agents → Multi-Agent Systems
Day 2: Custom Tools → External Integrations → Long-Running Operations  
Day 3: Session State → Persistent Memory → Automated Memory Management
Day 4: Logging/Debugging → Systematic Evaluation → Quality Assurance
Day 5: A2A Communication → Production Deployment → Enterprise Scale
```

## Prerequisites

- **Verified Kaggle Account**: Phone number verification required
- **Gemini API Key**: Create at [Google AI Studio](https://aistudio.google.com/app/api-keys)
- **Google Cloud Account**: Required for Day 5 production deployment
- **Basic Python Knowledge**: Understanding of functions, classes, and async/await

## Getting Started

1. **Clone/Download**: Get the course materials from this repository
2. **Kaggle Setup**: Copy and edit notebooks in Kaggle environment
3. **API Configuration**: Add GOOGLE_API_KEY to Kaggle secrets
4. **Sequential Learning**: Complete days in order, running cells one by one
5. **Practice Projects**: Build the hands-on examples in each notebook

## Course Outcomes

By completing this course, you will:

- **Build Production Agents**: Create enterprise-ready AI agents with proper architecture
- **Master Tool Integration**: Connect agents to external services and APIs
- **Implement Memory Systems**: Build agents that learn and remember across conversations
- **Ensure Quality**: Monitor, debug, and systematically test agent performance
- **Deploy at Scale**: Launch agents to production with proper resource management
- **Enable Collaboration**: Connect agents across organizations using standard protocols

## Resources

- [ADK Documentation](https://google.github.io/adk-docs/)
- [A2A Protocol](https://a2a-protocol.org/)
- [Vertex AI Agent Engine](https://cloud.google.com/vertex-ai/generative-ai/docs/agent-engine/overview)
- [Kaggle Discord](https://discord.com/invite/kaggle) - For help and questions

## Authors

- **Day 1**: [Kristopher Overholt](http://linkedin.com/in/koverholt)
- **Day 2**: [Laxmi Harikumar](https://www.linkedin.com/in/laxmi-harikumar/)
- **Day 3**: [Sampath M](https://www.linkedin.com/in/msampathkumar/)
- **Day 4**: [Sita Lakshmi Sangameswaran](https://www.linkedin.com/in/sitalakshmi04/), [Ivan Nardini](https://www.linkedin.com/in/ivan-nardini/)
- **Day 5**: [Lavi Nigam](https://www.linkedin.com/in/lavinigam/)

**Copyright**: 2025 Google LLC - Licensed under Apache License 2.0