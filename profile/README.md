<p align="center">
</p>

<h1 align="center">AgentPostmortem</h1>

<p align="center">Every AI agent failure, documented. Plus the verification, eval, and security tooling built from it.</p>

AgentPostmortem is a public registry of documented AI-agent failures at [agentpostmortem.com](https://www.agentpostmortem.com/). The rest of this org is the tooling that comes out of reading those cases: scanners that catch unsafe agent and MCP configurations before install, regression harnesses that fail the build when a prompt gets worse, context and token profilers, and reference agent implementations.

## Registry

| Repo | What it is |
| --- | --- |
| [agent-postmortem](https://github.com/AgentPostmortem/agent-postmortem) | The public case registry itself, [www.agentpostmortem.com](https://www.agentpostmortem.com/) |
| [Casebook-MCP](https://github.com/AgentPostmortem/Casebook-MCP) | Remote MCP server exposing the registry as tools any agent can query, plus an investigator agent that drafts postmortems from real precedents |
| [Casebook-Chat](https://github.com/AgentPostmortem/Casebook-Chat) | Streaming chat UI that searches the live registry over MCP and answers with cited case IDs |

## Security and verification

| Repo | What it is |
| --- | --- |
| [MCP-audit](https://github.com/AgentPostmortem/MCP-audit) | Security scanner and linter for MCP servers, 18 rules, SARIF output |
| [Skill-audit](https://github.com/AgentPostmortem/Skill-audit) | Scans agent skills for prompt injection, dangerous shell, secret access, and exfiltration before you install them, 31 rules |
| [Injection-arena](https://github.com/AgentPostmortem/Injection-arena) | Self-hostable prompt-injection challenge game with a leaderboard |
| [Answerproof](https://github.com/AgentPostmortem/Answerproof) | Tamper-evident receipts for RAG answers, Merkle inclusion proofs and Ed25519 signatures |
| [VaultRAG](https://github.com/AgentPostmortem/VaultRAG) | Permission-aware RAG with access control enforced inside the retrieval query, with a gold-set eval that fails CI on any leak |

## Eval and CI

| Repo | What it is |
| --- | --- |
| [Evalgate](https://github.com/AgentPostmortem/Evalgate) | Prompt and agent regression CI, a GitHub Action that fails the build when a prompt gets dumber |
| [Tracecase](https://github.com/AgentPostmortem/Tracecase) | Record agent runs and replay them against prompt and model changes to catch regressions and unsafe tool calls |
| [Voiceeval](https://github.com/AgentPostmortem/Voiceeval) | Evaluation for voice agents: mis-hearing, missing confirmation, latency, barge-in |
| [Agentrace](https://github.com/AgentPostmortem/Agentrace) | Observability for Claude Code subagents, reads session transcripts and flags results you should not trust |

## Context and cost

| Repo | What it is |
| --- | --- |
| [Ctxlens](https://github.com/AgentPostmortem/Ctxlens) | Context-window profiler for AI agents, shows what is eating your tokens |
| [Ctxtrim](https://github.com/AgentPostmortem/Ctxtrim) | Finds the files ballooning your coding-agent context and writes ignore files to cut it |
| [tokencut](https://github.com/AgentPostmortem/tokencut) | Measures and cuts the token cost of LLM and agent message payloads, no model calls |

## Agents and infrastructure

| Repo | What it is |
| --- | --- |
| [Bridgekit](https://github.com/AgentPostmortem/Bridgekit) | Scoped MCP server exposing company tools with per-client permission boundaries and an append-only audit log |
| [Webhands](https://github.com/AgentPostmortem/Webhands) | Computer-use agent for tools with no usable API, refuses write actions without explicit confirmation |
| [Greenlite](https://github.com/AgentPostmortem/Greenlite) | Mobile approval cockpit for AI agents, one-tap approve or deny routed back to the agent |
| [Resolvd](https://github.com/AgentPostmortem/Resolvd) | End-to-end inbox operator that triages, drafts, and acts within policy on inbound support messages |
| [RelayG](https://github.com/AgentPostmortem/RelayG) | Support ticket triage agent as a LangGraph state machine with a human-in-the-loop interrupt and SQLite checkpointing |
| [Tenantq](https://github.com/AgentPostmortem/Tenantq) | Multi-tenant hybrid-search reference on Qdrant, dense plus sparse RRF fusion with Recall@K and p95 benchmarks |

## Good first issue

Browse every repo at [github.com/orgs/AgentPostmortem/repositories](https://github.com/orgs/AgentPostmortem/repositories) and filter a repo's issues by the `good first issue` label.

Two contributions are always welcome. First, a new documented case in [agent-postmortem](https://github.com/AgentPostmortem/agent-postmortem): a real, sourced agent failure written up in the registry format. Second, a new detection rule for [MCP-audit](https://github.com/AgentPostmortem/MCP-audit) or [Skill-audit](https://github.com/AgentPostmortem/Skill-audit), ideally with a fixture that fails before the rule and passes after.

Read the `CONTRIBUTING.md` in the repo you are changing (for example [MCP-audit/CONTRIBUTING.md](https://github.com/AgentPostmortem/MCP-audit/blob/main/CONTRIBUTING.md)) before opening a pull request.
