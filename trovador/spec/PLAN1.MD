# trovador.io – DAO + Blockchain System Implementation Plan

## 🧭 Guiding Principles

- ✅ Top-down design (interfaces and contracts first)
- ✅ No breaking changes once interfaces are published
- ✅ Use .NET 8 (no external dependencies)
- ✅ Built-in dependency injection throughout
- ✅ Entity Framework Core for data persistence
- ✅ All tests use ASP.NET Core Test Host for integration
- ✅ Designed for containerized distribution (Docker)

---

## 📦 Project Structure

```
/trovador
├── api/
│   ├── Trovador.API/
│   ├── Trovador.Application/
│   ├── Trovador.Domain/
│   ├── Trovador.Infrastructure/
│   ├── Trovador.Tests.Unit/
│   ├── Trovador.Tests.Integration/
│   ├── Trovador.Tests.E2E/
│   ├── Dockerfile
│   ├── docker-compose.yml
│   └── README.md
├── spec/
│   ├── implementation-plan.md
│   ├── GOVERNANCE.md
│   ├── CONTRIBUTING.md
│   ├── LICENSE
│   ├── overview.md
│   └── README.md
├── README.md
```

---

## ⚙️ Development Phases

### Phase 0 – Architecture Definition
- Define all interfaces and DTOs
- Establish DI setup in `Program.cs`
- Configure EF Core with SQLite or InMemory provider (runtime switchable)

### Phase 1 – Blockchain Engine
- Block validation, linking, and chain verification
- In-memory and EF-backed implementation
- Genesis block on startup

### Phase 2 – Token Ledger
- Simulate token balances and transfers
- Ledger stored via EF Core
- Prevent negative balances and over-transfers

### Phase 3 – DAO Proposals
- Create and list proposals
- Support expiration and metadata
- Store via EF Core with timestamps

### Phase 4 – Voting System
- Weighted voting using token balance
- Prevent double voting
- Majority/quorum logic for approval
- Signature verification (optional)

### Phase 5 – Node Synchronization
- Peer discovery (manual config or list)
- HTTP sync of blocks, votes, and proposals
- Chain replacement based on validity + length

### Phase 6 – Console & Web UI (Optional)
- Simple CLI for admin actions
- Optionally: Razor Pages or Blazor Server interface

---

## 🧪 Testing Strategy

### ✅ Unit Tests – `Trovador.Tests.Unit`
- Test each service against its interface
- Use InMemory EF Core
- No networking or file I/O

### ✅ Integration Tests – `Trovador.Tests.Integration`
- Use `WebApplicationFactory<Program>`
- Test real HTTP endpoints:
  - Proposal creation
  - Vote submission
  - Block synchronization
- Validate actual EF Core persistence and DI wiring

### ✅ E2E Tests – `Trovador.Tests.E2E`
- Simulate multi-node deployments using Docker Compose
- Verify:
  - Cross-node sync
  - Full proposal/vote/block lifecycle
  - Data consistency and quorum agreement

---

## 🧪 Test Case Checklist

### Blockchain Service
- AddBlock appends valid block
- Rejects block with wrong hash
- Chain validation returns correct result
- Accepts longer valid chain, rejects invalid chains

### Ledger Service
- GetBalance returns correct result
- Transfer updates balances
- Prevents overdrafts or unknown accounts

### Proposal Service
- CreateProposal saves proposal
- GetActiveProposals filters correctly
- GetProposalResult tallies vote totals

### Voting Service
- Vote persists vote
- Rejects duplicate or ineligible votes
- Tally calculates correctly and applies quorum

### Node Sync Service
- BroadcastBlock reaches all peers
- SyncChain replaces with valid longer chain
- Rejects invalid sync requests

---

## 🐳 Docker & Container Considerations

- `Dockerfile` builds minimal `Trovador.API` image
- `docker-compose.yml` launches multiple nodes with unique ports
- Tests must not use fixed paths or machine-specific configs
- Logs and database use volume mounts or memory as appropriate
- Health check endpoint (`/health`) required for orchestration

---

## 🤖 About the Programming Agent (LLM)

This implementation plan and technical architecture for the `trovador.io` project was developed in collaboration between **Jose Manuel Ojeda Melgar** (project architect and lead developer) and an advanced **Large Language Model (LLM)** — ChatGPT, powered by **OpenAI's GPT-4o**.

### 🧠 Agent Profile

| Attribute              | Value |
|------------------------|-------|
| Model Name             | `gpt-4o` (GPT-4 Omni) |
| Developed By           | OpenAI |
| Programming Expertise  | C#, .NET 8, ASP.NET Core, Entity Framework Core, Docker, Web API, Blazor |
| Reasoning Capabilities | High-level architecture, code generation, optimization, unit/integration test planning |
| Code Style             | SOLID principles, interface-driven, dependency-injection first |
| Communication Style    | Structured, markdown-capable, top-down planning |
| Tooling Integration    | Markdown, Docker, YAML, EF Core Migrations, HTTP simulation, Test Host |
| Limitations            | Does not execute code natively — outputs must be reviewed and run by human developer or CI pipeline |

---

### 📚 How This Plan Was Created

- The plan was defined through a series of structured conversations where **Jose Manuel Ojeda Melgar** guided the requirements for:
  - Educational blockchain design in C#
  - Multi-node DAO functionality
  - No-breaking-change top-down development
  - Clean architecture and testability
  - Docker-based distribution with integration tests

- The LLM agent acted as a **technical advisor and planner**, suggesting architecture layouts, development phases, module boundaries, and test strategies using only **built-in .NET 8 features**.

---

### 🧩 Agent Responsibilities in This Project

- Define a scalable, modular, and container-ready architecture for a blockchain-backed DAO system
- Enforce principles of interface-driven development and dependency injection
- Outline an integration test suite using ASP.NET Core WebApplicationFactory
- Provide testable logic contracts and entity design with Entity Framework Core
- Help document system behavior and lifecycle in human-readable Markdown

---

### 🔐 Note on Autonomy

> While the LLM agent contributed structure and best practices, **all decisions, validation, implementation, and deployment remain under the supervision of Jose Manuel Ojeda Melgar and the trovador.io development team**. The LLM is a planning and scaffolding tool, not a substitute for review, testing, or secure deployment.
