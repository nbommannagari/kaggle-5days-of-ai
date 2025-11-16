# Day 3: Memory Management and State Persistence

Welcome to Day 3 of the Kaggle 5-day AI Agents course! This folder contains two essential notebooks that teach you how to build stateful agents with persistent memory and sophisticated state management capabilities.

## 📚 Notebooks Overview

### 1. `day-3a-agent-sessions.ipynb`
**Memory Management - Part 1: Sessions**

This notebook introduces session management and stateful agent development, covering short-term memory and conversation persistence.

**What you'll learn:**
- ✅ What sessions are and how to use them in your agent
- ✅ How to build stateful agents with sessions and events
- ✅ How to persist sessions in a database
- ✅ Context management practices such as context compaction
- ✅ Best practices for sharing session state

**Key Concepts:**
- **Sessions**: Containers for conversations with events and state
- **Events**: Building blocks of conversations (user input, agent responses, tool calls)
- **State**: Agent's scratchpad for dynamic information storage
- **Context Compaction**: Automatic summarization to manage long conversations

### 2. `day-3b-agent-memory.ipynb`
**Memory Management - Part 2: Memory**

This notebook covers long-term memory systems that persist across multiple conversations and sessions.

**What you'll learn:**
- ✅ Initialize MemoryService and integrate with your agent
- ✅ Transfer session data to memory storage
- ✅ Search and retrieve memories
- ✅ Automate memory storage and retrieval
- ✅ Understand memory consolidation concepts

**Key Concepts:**
- **Memory vs Sessions**: Long-term knowledge vs short-term conversation
- **Memory Consolidation**: Extracting key facts from raw conversations
- **Semantic Search**: Meaning-based retrieval across conversations
- **Automated Memory**: Callbacks for hands-free memory management

## 🧠 Core Architecture

### Session Management

#### **Session Components**
```python
Session = {
    "events": [user_input, agent_response, tool_calls],
    "state": {"user:name": "Sam", "user:country": "Poland"}
}
```

#### **Session Services**
| Service | Persistence | Use Case |
|---------|-------------|----------|
| **InMemorySessionService** | ❌ Lost on restart | Development & Testing |
| **DatabaseSessionService** | ✅ Survives restarts | Production Applications |

### Memory Management

#### **Memory vs Sessions**
| Aspect | Sessions | Memory |
|--------|----------|---------|
| **Scope** | Single conversation | Cross-conversation knowledge |
| **Duration** | Temporary | Persistent |
| **Purpose** | Context within chat | Long-term learning |
| **Search** | Sequential access | Semantic/keyword search |

#### **Memory Services**
- **InMemoryMemoryService**: Keyword matching, no persistence (learning)
- **VertexAiMemoryBankService**: LLM-powered consolidation, semantic search (production)

## 🛠️ Technical Implementation

### Session State Management

#### **Custom State Tools**
```python
def save_userinfo(tool_context: ToolContext, user_name: str, country: str):
    tool_context.state["user:name"] = user_name
    tool_context.state["user:country"] = country
    return {"status": "success"}

def retrieve_userinfo(tool_context: ToolContext):
    user_name = tool_context.state.get("user:name", "Not found")
    return {"status": "success", "user_name": user_name}
```

### Context Compaction

#### **Automatic Summarization**
```python
research_app = App(
    name="research_app",
    root_agent=chatbot_agent,
    events_compaction_config=EventsCompactionConfig(
        compaction_interval=3,  # Compact every 3 turns
        overlap_size=1,         # Keep 1 turn for context
    ),
)
```

### Memory Integration

#### **Three-Step Memory Workflow**
1. **Initialize**: Create MemoryService and provide to Runner
2. **Ingest**: Transfer session data using `add_session_to_memory()`
3. **Retrieve**: Search memories using `search_memory()` or agent tools

#### **Memory Tools**
- **`load_memory`** (Reactive): Agent decides when to search
- **`preload_memory`** (Proactive): Automatically loads before every turn

### Automated Memory Management

#### **Callback-Based Automation**
```python
async def auto_save_to_memory(callback_context):
    await callback_context._invocation_context.memory_service.add_session_to_memory(
        callback_context._invocation_context.session
    )

agent = LlmAgent(
    tools=[preload_memory],
    after_agent_callback=auto_save_to_memory,  # Auto-save after each turn
)
```

## 🔧 Key Components Used

### Session Management
- **InMemorySessionService**: Temporary session storage
- **DatabaseSessionService**: Persistent SQLite-based storage
- **EventsCompactionConfig**: Automatic context summarization
- **ToolContext**: Access to session state in tools

### Memory Management
- **InMemoryMemoryService**: Development memory service
- **load_memory / preload_memory**: Built-in memory retrieval tools
- **Callbacks**: Automated memory storage triggers
- **SearchMemoryResponse**: Memory search results

## 📋 Learning Outcomes

By completing Day 3, you will:

1. **Master Session Management**: Build stateful agents that remember conversation context
2. **Implement Persistent Storage**: Use databases to survive application restarts
3. **Optimize Context**: Use compaction to manage long conversations efficiently
4. **Build Memory Systems**: Create agents that learn across multiple conversations
5. **Automate Memory Operations**: Use callbacks for hands-free memory management
6. **Design State Architecture**: Structure session state for scalable applications

## 🎯 Practical Applications

### Session State Use Cases
- **User Preferences**: Remember settings across conversation turns
- **Workflow State**: Track multi-step process progress
- **Context Variables**: Store temporary calculation results
- **User Authentication**: Maintain login state during chat

### Memory Use Cases
- **Personal Assistants**: Remember user preferences across sessions
- **Customer Support**: Access previous interaction history
- **Learning Systems**: Build knowledge from past conversations
- **Recommendation Engines**: Learn user patterns over time

## 🔄 Workflow Patterns

### Manual Memory Management
```python
# 1. Have conversation
await run_session(runner, "My favorite color is blue", "session-01")

# 2. Save to memory
session = await session_service.get_session(app_name, user_id, "session-01")
await memory_service.add_session_to_memory(session)

# 3. Retrieve in new session
await run_session(runner, "What's my favorite color?", "session-02")
```

### Automated Memory Management
```python
# Agent with callback automatically saves after each turn
agent = LlmAgent(
    tools=[preload_memory],
    after_agent_callback=auto_save_to_memory,
)
# No manual memory calls needed!
```

## 📊 Performance Considerations

### Context Compaction Benefits
- **Reduced Token Usage**: Summarized history vs full conversation
- **Faster Processing**: Less context to process
- **Cost Optimization**: Lower API costs with managed context
- **Improved Focus**: Agent focuses on relevant information

### Memory Search Efficiency
| Service | Search Method | Performance | Accuracy |
|---------|---------------|-------------|----------|
| **InMemory** | Keyword matching | Fast | Limited |
| **VertexAI** | Semantic search | Moderate | High |

## 🔒 Best Practices

### Session State Management
- Use descriptive key prefixes (`user:`, `app:`, `temp:`)
- Keep state minimal and focused
- Validate state data before storage
- Handle missing state gracefully

### Memory Management
- Choose appropriate memory service for your needs
- Implement proper error handling for memory operations
- Consider memory consolidation for production systems
- Monitor memory usage and search performance

## 🚀 Production Readiness

### Scalability Considerations
- **Database Sessions**: Use proper database for production
- **Memory Consolidation**: Implement intelligent fact extraction
- **Callback Optimization**: Balance frequency vs performance
- **State Cleanup**: Implement retention policies

### Monitoring and Observability
- Track session creation and lifecycle
- Monitor memory storage and retrieval patterns
- Log context compaction effectiveness
- Measure search accuracy and performance

## 🎯 Next Steps

After completing Day 3, you'll be ready to:
- Build production-grade stateful agents
- Implement sophisticated memory systems
- Design scalable conversation architectures
- Optimize context management for performance
- Create personalized user experiences

Continue to Day 4 to learn about **Observability and Agent Evaluation** for monitoring and improving your agent systems!

## 📚 Additional Resources

- [ADK Sessions Documentation](https://google.github.io/adk-docs/sessions/)
- [ADK Memory Documentation](https://google.github.io/adk-docs/sessions/memory/)
- [Context Compaction Guide](https://google.github.io/adk-docs/context/compaction/)
- [Vertex AI Memory Bank](https://cloud.google.com/vertex-ai/generative-ai/docs/agent-engine/memory-bank/overview)
- [ADK Callbacks Documentation](https://google.github.io/adk-docs/agents/callbacks/)
- [Kaggle Discord](https://discord.com/invite/kaggle) - For help and questions

---

**Authors**: [Sampath M](https://www.linkedin.com/in/msampathkumar/)

**Copyright**: 2025 Google LLC - Licensed under Apache License 2.0