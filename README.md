# Crypto Architecture Research Skill

Agent skill for source-backed crypto protocol architecture research.

Use it when the task needs contract/module architecture, user flow, fund flow, state flow, permissions, upgradeability, address provenance, or verified on-chain due diligence.

Do not use it for price analysis, valuation, market commentary, news summaries, CMO/content work, or one-off link checks without architecture analysis.

## What It Does

- Validates official project resources before accepting repos, frontends, or contract addresses.
- Maps protocol products, tokens, modules, contracts, and dependencies.
- Resolves official addresses into verified source, proxy/implementation status, events, and chain evidence when available.
- Reconstructs user flow from frontend action to wallet transaction and chain state.
- Separates fund flow from state/accounting flow.
- Identifies permissions, upgradeability, privileged roles, external dependencies, and unresolved evidence gaps.

## Structure

```text
.
├── SKILL.md
├── agents
│   └── openai.yaml
└── references
    ├── contract-mapping-checklist.md
    ├── output-template.md
    ├── source-validation.md
    └── user-flow-and-fund-flow.md
```

## Install

Copy this directory into a Codex/agent skill root, for example:

```bash
~/.agents/skills/crypto-architecture-research
```

or:

```bash
~/.codex/skills/crypto-architecture-research
```

Avoid installing duplicate copies in both locations at the same time, because duplicate skill names can create routing confusion.

## Evidence Dependencies

- OpenTwitter/opentwitter is used when available to verify official X accounts, official links, address announcements, and migration notices.
- Herd MCP is preferred for contract metadata, source code, proxy/implementation resolution, events, transaction activity, wallet activity, and HAL-style simulation.
- Herd CLI may be used as fallback where installed, authenticated, and chain-supported.

If Herd evidence is unavailable, the skill should not make live chain-state conclusions. It should continue only with official resource discovery or verified source-code analysis and mark missing evidence clearly.

## Current Status

This is the restored full-instruction version of the skill. It favors research completeness over a small initial context footprint.

Known packaging gap: this copy currently includes `agents/openai.yaml` but not `agents/interface.yaml`.

