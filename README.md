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

## Use Case Showcase

| Question | Output |
| --- | --- |
| What assets has this project issued (https://x.com/saturn_credit)? | Maps the project's issued assets, token roles, and official contract addresses. |
| Introduce the whole mint process of USDat (0x23238f20b894f29041f48D88eE91131C395Aaa71)? | Breaks down the USDat mint process from user action to contract execution. |
| Who controls the USDat whitelist? | Identifies the on-chain role and wallet that control USDat whitelist permissions. |
| Explain the money-flow of the mint of USDat. | Traces where user funds move and where USDat backing is finally held. |

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

## External MCP Dependencies

This skill may use external MCP tools for source-backed crypto research:

- **OpenTwitter MCP**: X/Twitter profiles, tweets, tweet search, follower events, and KOL context. It requires a configured OpenTwitter MCP server and a valid `TWITTER_TOKEN`. See: https://github.com/6551Team/opentwitter-mcp
- **Herd MCP**: contract metadata, source-code analysis, transaction decoding, wallet/token activity, and related on-chain research tools. It requires a configured Herd MCP server and completed Herd authentication. See: https://docs.herd.eco/herd-mcp/configuration

Credentials and authentication are managed by the host Codex/MCP environment, not by this skill repository. Do not commit tokens, cookies, API keys, or local MCP config files.

If a required MCP tool is unavailable, unauthenticated, or rate-limited, the skill should state the limitation clearly and avoid making tool-dependent claims.

## Current Status

This is the restored full-instruction version of the skill. It favors research completeness over a small initial context footprint.

Known packaging gap: this copy currently includes `agents/openai.yaml` but not `agents/interface.yaml`.
