## Find out how your AI agent fails before your customers do.

AgentPostmortem is an open reliability benchmark and fault-injection runner for AI agents. It breaks an agent's world on purpose, safely, and judges every run by what actually happened: charges, emails, writes. Not by how the transcript reads.

```bash
pip install agentpostmortem-bench
apm run --scenario all --agent all
```

- **50 incident scenarios** across 11 simulated services and 10 fault modes: duplicate charges after a lost response, late commits, silent errors, false "done" after a tool failure, repeated work after a crash, stale and lying tool data, retry storms.
- **Real frameworks, no API key**: LangGraph, OpenAI Agents SDK, Claude Agent SDK and Hermes Agent run against a scripted model, so results are free and reproducible.
- **Any agent over MCP**: `apm serve` exposes the scenario's services as tools for Claude Code, Cursor or your own agent.

[Repository](https://github.com/AgentPostmortem/agentpostmortem) · [PyPI](https://pypi.org/project/agentpostmortem-bench/) · [agentpostmortem.com](https://agentpostmortem.com)
