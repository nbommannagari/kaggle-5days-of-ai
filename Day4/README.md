# Day 4: Agent Observability and Evaluation

Welcome to Day 4 of the Kaggle 5-day AI Agents course! This folder contains two essential notebooks that teach you how to monitor, debug, and systematically evaluate your AI agents for production readiness.

## 📚 Notebooks Overview

### 1. `day-4a-agent-observability.ipynb`
**Agent Observability - Logs, Traces & Metrics**

This notebook focuses on implementing comprehensive observability for AI agents, enabling you to debug failures and monitor performance in production.

**What you'll learn:**
- ✅ Set up logging configuration for agent debugging
- ✅ Create and debug a broken agent using ADK web UI & logs
- ✅ Understand how to implement logging in production
- ✅ Learn when to use built-in logging vs custom solutions

**Key Concepts:**
- **Logs**: Records of individual events showing what happened
- **Traces**: Connected logs showing the complete decision-making sequence
- **Metrics**: Summary statistics showing overall performance
- **Debug Workflow**: Symptom → logs → root cause → fix

### 2. `day-4b-agent-evaluation.ipynb`
**Agent Evaluation - Systematic Testing and Quality Assurance**

This notebook covers proactive agent evaluation to catch quality degradations before they impact users.

**What you'll learn:**
- ✅ Understand what agent evaluation is and how to use it
- ✅ Run evaluations and analyze results in ADK web UI
- ✅ Detect regression in agent performance over time
- ✅ Create evaluation files (*.test.json, *.evalset.json, test_config.json)

**Key Concepts:**
- **Response Match Score**: Text similarity between expected and actual responses
- **Tool Trajectory Score**: Correctness of tool usage and parameters
- **Regression Testing**: Automated testing to catch performance degradation
- **User Simulation**: Dynamic test case generation for comprehensive evaluation

## 🔍 Observability Architecture

### Three Pillars of Agent Observability

#### **1. Logs**
```python
logging.basicConfig(
    filename="logger.log",
    level=logging.DEBUG,
    format="%(filename)s:%(lineno)s %(levelname)s:%(message)s",
)
```

#### **2. Traces**
- Complete execution flow from user input to final response
- Tool call sequences and decision points
- Performance timing and bottleneck identification

#### **3. Metrics**
- Success/failure rates
- Response times
- Tool usage patterns
- Error frequencies

### Debugging Workflow

#### **Core Pattern: Symptom → Logs → Root Cause → Fix**
```
User: "Agent turned on fireplace when I asked for lights!"
↓
Debug Logs: Shows incorrect tool parameters passed
↓
Root Cause: Function signature mismatch (str vs List[str])
↓
Fix: Update parameter types in tool definition
```

## 📊 Evaluation Framework

### Evaluation Metrics

#### **Response Match Score**
- Measures text similarity between expected and actual responses
- Range: 0.0 (completely different) to 1.0 (perfect match)
- Uses text similarity algorithms for comparison

#### **Tool Trajectory Score**
- Measures correctness of tool usage and parameters
- Range: 0.0 (wrong tools/parameters) to 1.0 (perfect execution)
- Validates entire decision-making sequence

### Evaluation Configuration
```json
{
  "criteria": {
    "tool_trajectory_avg_score": 1.0,  // Perfect tool usage required
    "response_match_score": 0.8,       // 80% text similarity threshold
  }
}
```

## 🛠️ Technical Implementation

### Production Logging with Plugins

#### **Built-in LoggingPlugin**
```python
from google.adk.plugins.logging_plugin import LoggingPlugin

runner = InMemoryRunner(
    agent=research_agent,
    plugins=[LoggingPlugin()],  // Automatic observability
)
```

#### **Custom Plugin Development**
```python
class CountInvocationPlugin(BasePlugin):
    async def before_agent_callback(self, *, agent: BaseAgent, callback_context: CallbackContext):
        self.agent_count += 1
        logging.info(f"[Plugin] Agent run count: {self.agent_count}")
```

### Systematic Evaluation Process

#### **1. Create Evaluation Configuration**
```python
eval_config = {
    "criteria": {
        "tool_trajectory_avg_score": 1.0,
        "response_match_score": 0.8,
    }
}
```

#### **2. Define Test Cases**
```python
test_cases = {
    "eval_set_id": "home_automation_integration_suite",
    "eval_cases": [
        {
            "eval_id": "living_room_light_on",
            "conversation": [...],
            "expected_response": {...},
            "intermediate_data": {...}
        }
    ]
}
```

#### **3. Run CLI Evaluation**
```bash
adk eval agent_directory evalset.json --config_file_path=test_config.json
```

## 🔧 Key Components Used

### Observability Components
- **LoggingPlugin**: Built-in comprehensive logging
- **ADK Web UI**: Interactive debugging interface
- **Custom Plugins**: Extensible observability framework
- **Debug Logs**: Detailed execution traces

### Evaluation Components
- **ADK Web UI Eval Tab**: Interactive test creation
- **CLI Evaluation**: Automated regression testing
- **Test Configuration**: Pass/fail criteria definition
- **User Simulation**: Dynamic test case generation

## 📋 Learning Outcomes

By completing Day 4, you will:

1. **Master Agent Debugging**: Use logs and traces to identify and fix agent failures
2. **Implement Production Observability**: Set up comprehensive monitoring systems
3. **Design Evaluation Frameworks**: Create systematic testing approaches
4. **Detect Performance Regression**: Catch quality degradations early
5. **Build Quality Assurance**: Ensure agent reliability before deployment

## 🎯 Practical Applications

### Observability Use Cases
- **Production Debugging**: Identify why agents fail in live environments
- **Performance Monitoring**: Track response times and success rates
- **Quality Assurance**: Ensure consistent agent behavior
- **Compliance Auditing**: Maintain logs for regulatory requirements

### Evaluation Use Cases
- **Regression Testing**: Catch breaking changes before deployment
- **A/B Testing**: Compare different agent versions
- **Quality Gates**: Automated quality checks in CI/CD pipelines
- **User Experience Validation**: Ensure consistent user interactions

## 🔄 Workflow Patterns

### Development Debugging
```
1. Agent fails mysteriously
2. Enable DEBUG logging
3. Examine ADK web UI traces
4. Identify root cause in logs
5. Fix and verify resolution
```

### Production Monitoring
```
1. Deploy agent with LoggingPlugin
2. Monitor metrics and logs
3. Set up alerting for failures
4. Investigate issues using traces
5. Deploy fixes with confidence
```

### Continuous Evaluation
```
1. Create comprehensive test suite
2. Run evaluations on every change
3. Monitor evaluation metrics
4. Block deployments on failures
5. Maintain quality standards
```

## 📊 Performance Considerations

### Logging Overhead
- **DEBUG Level**: Comprehensive but verbose (development only)
- **INFO Level**: Balanced logging for production
- **Custom Plugins**: Targeted logging for specific needs
- **Log Rotation**: Manage log file sizes in production

### Evaluation Efficiency
- **Batch Testing**: Run multiple test cases together
- **Parallel Execution**: Speed up evaluation runs
- **Selective Testing**: Focus on critical scenarios
- **Automated Scheduling**: Regular regression testing

## 🔒 Best Practices

### Observability Best Practices
- Use appropriate log levels for different environments
- Implement structured logging for better analysis
- Set up centralized log aggregation for production
- Monitor both technical and business metrics

### Evaluation Best Practices
- Create diverse test scenarios covering edge cases
- Maintain test cases as living documentation
- Set realistic pass/fail thresholds
- Regularly update evaluation criteria

## 🚀 Production Readiness

### Observability Checklist
- ✅ Comprehensive logging implemented
- ✅ Monitoring dashboards configured
- ✅ Alerting rules established
- ✅ Log retention policies defined

### Evaluation Checklist
- ✅ Test suite covers critical scenarios
- ✅ Automated evaluation in CI/CD pipeline
- ✅ Quality gates prevent bad deployments
- ✅ Regular evaluation metric reviews

## 🎯 Next Steps

After completing Day 4, you'll be ready to:
- Deploy production-ready agents with confidence
- Implement comprehensive monitoring systems
- Build robust quality assurance processes
- Maintain high agent performance standards
- Scale agent systems reliably

Continue to Day 5 to learn about **Production Deployment and Agent2Agent Protocol** for enterprise-scale agent systems!

## 📚 Additional Resources

- [ADK Observability Documentation](https://google.github.io/adk-docs/observability/logging/)
- [ADK Evaluation Overview](https://google.github.io/adk-docs/evaluate/)
- [Custom Plugin Development](https://google.github.io/adk-docs/plugins/)
- [Evaluation Criteria Guide](https://google.github.io/adk-docs/evaluate/criteria/)
- [User Simulation Documentation](https://google.github.io/adk-docs/evaluate/user-sim/)
- [Kaggle Discord](https://discord.com/invite/kaggle) - For help and questions

---

**Authors**: 
- [Sita Lakshmi Sangameswaran](https://www.linkedin.com/in/sitalakshmi04/)
- [Ivan Nardini](https://www.linkedin.com/in/ivan-nardini/)

**Copyright**: 2025 Google LLC - Licensed under Apache License 2.0