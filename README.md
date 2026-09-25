# SentinelAgents

**A multi-agent LLM system for Security Operations Center (SOC) automation.**

Graduation project, Computer Engineering (2026–2027), by Seyid Ali Ozan Karabayır.

> Status: proposal stage. Development starts in October 2026.

## Overview

SOC analysts face alert fatigue, slow manual investigation and a shortage of experienced staff.
SentinelAgents uses specialised LLM agents to automate repetitive investigation steps while the analyst keeps the final decision.

```
Security events ──► Guardrail layer ──► Orchestrator agent
                                            │
        ┌───────────────┬───────────────────┼────────────────────┐
        ▼               ▼                   ▼                    ▼
  Triage Agent   Incident Response    Phishing Agent    Vulnerability Agent
     (core)           (core)           (extension)         (extension)
        │               ▲
        └─ true positive┘      all agents ◄──► shared tools, memory, MITRE ATT&CK KB
                                            │
                                            ▼
                             Report generator ──► Analyst (human in the loop)
```

## Objectives

1. Design an orchestrator that routes security events to specialised agents.
2. Build Triage and Incident Response agents that use real security tools.
3. Map findings to MITRE ATT&CK in analyst-ready reports.
4. Evaluate accuracy, speed and resistance to prompt injection.

## Planned stack

- Python, LangGraph (agent orchestration)
- Commercial LLM API and local open models via Ollama
- Streamlit (analyst dashboard)
- Docker (isolated test lab)

## Datasets

- Splunk Boss of the SOC (BOTS v1–v3)
- CICIDS2017
- Own lab samples (phishing emails, scan results)

All testing uses public datasets or an isolated personal lab. No third-party systems are touched.

## Planned repository structure

```
src/sentinel_agents/   source code (agents, orchestrator, tools, guardrails)
tests/                 unit and integration tests
data/                  dataset notes and download scripts (raw data is not committed)
docs/                  proposal, reports, poster, architecture diagrams
notebooks/             experiments and evaluation analysis
```

## Roadmap

| Phase | Months | Focus |
|---|---|---|
| 1 · Foundation | Oct–Dec 2026 | Learning, literature review, architecture, Triage Agent MVP |
| 2 · Core system | Jan–Mar 2027 | Incident Response Agent, orchestrator, dashboard, interim report |
| 3 · Extend & test | Apr–May 2027 | Extension agents, guardrails, evaluation |
| 4 · Deliver | Jun 2027 | Final report, demo, defence |

## License

MIT
