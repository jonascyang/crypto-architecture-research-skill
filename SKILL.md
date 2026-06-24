---
name: crypto-architecture-research
description: Use when source-backed crypto protocol research needs contract/module architecture, user flow, fund flow, state flow, permissions, upgradeability, or address-level due diligence. Prefer for full protocol maps, multi-product DeFi, stablecoins, vault/router/pool relationships, and verified on-chain architecture. Do not use for price, valuation, market commentary, news summaries, or one-off official-link checks without architecture analysis.
---

# Crypto Architecture Research

## Overview

Map crypto protocol architecture from official sources and verified on-chain evidence. Treat official provenance as a hard gate: only use official docs, official GitHub, official frontend resources, official announcements, and verified on-chain code that can be linked back to those official sources.

Do not force the project into a generic DeFi template too early. Read the relevant official documentation broadly first, identify the product's unique mechanisms and vocabulary, and then map the architecture around those project-specific behaviors.

## Research Modes

Choose the lightest mode that satisfies the request:

- `Provenance Check`: verify official resource or address provenance only when it supports later architecture, contract, user-flow, or fund-flow research.
- `Targeted Contract Review`: analyze one contract, function, user action, product path, or data path and only the dependencies needed to explain it.
- `Full Architecture Map`: map project-wide products, tokens, modules, contracts, user flows, fund flows, permissions, upgradeability, dependencies, and risks.

Default to `Targeted Contract Review` when the user names one contract, address, function, product path, or data source. Use `Full Architecture Map` only when the user asks for complete protocol architecture, full system mapping, all core contracts, project-wide due diligence, or when a targeted answer would be misleading without the wider map.

Ask at most two questions when project, network, or target action is unclear.

## Source Validation First

Read [references/source-validation.md](references/source-validation.md) before using any external resource.

Follow this evidence order:
- Identify the official website, docs, GitHub org or repo, and official X/Twitter account.
- Cross-validate those resources against each other before treating any of them as authoritative.
- Treat search results as discovery leads only, never as evidence.
- Use official X/Twitter only for ownership, links, address announcements, migrations, and launch timelines.
- Use verified contract source only after the address is corroborated by at least two official surfaces.
- If official GitHub does not expose the implementation, continue from official addresses into verified on-chain source, proxy metadata, and implementation contracts instead of stopping.

Use supporting tools with clear boundaries:
- Use current-session OpenTwitter/opentwitter tools, when available, to find or verify the official account, official links, address announcements, and migration notices.
- Use current-session Herd MCP tools as the primary path for contract metadata, source code, proxy and implementation resolution, events, transaction activity, wallet activity, and HAL simulation.
- In Codex, the callable namespace is usually `mcp__herd_mcp` and the configured server name is usually `herd_mcp`. Do not hardcode `herd-mcp` as the only usable name.
- Herd-backed evidence is required before making live chain-state, transaction-level, recent-activity, proxy-resolution, or HAL-simulation conclusions.
- Verified source-code reading may continue without Herd only as source-code analysis, clearly marked as not Herd-backed live chain analysis.
- Explorer pages, public RPC calls, verified source pages, and frontend constants may support the analysis, but they do not replace official source attribution or Herd-backed evidence where live chain conclusions are required.

If Herd MCP authentication or availability fails:
- retry the relevant MCP call once if the failure looks transient
- if the current session still cannot see Herd MCP tools, use Herd CLI as the fallback when it is installed, authenticated, and covers the requested chain
- if Herd CLI credentials are expired or revoked, run `herd login` or `/Users/jonas/.herd/bin/herd login` only with explicit user approval
- if neither Herd MCP nor Herd CLI is usable, stop before making Herd-backed chain conclusions
- continue only with official non-chain resource discovery or verified source-code analysis when useful, and clearly state that live Herd chain analysis was not completed

If a repo, domain, or address is not corroborated by at least two official sources, mark it as `Unverified` and keep it out of core conclusions.

## Herd CLI Fallback

- Prefer `herd` on PATH; otherwise try `/Users/jonas/.herd/bin/herd`.
- Current Herd CLI chain flags support `ethereum` and `base`; if the contract is on another chain, do not claim Herd-backed contract analysis unless Herd MCP directly supports that chain in the current session.
- Treat Herd CLI output as equivalent Herd evidence for supported surfaces, but state in the final report that Herd CLI was used because MCP was unavailable in the thread.
- Use `--format json` whenever possible so results can be cited and parsed.
- Tool mapping:
  - contract metadata, ABI, summaries: `herd contract metadata --blockchain <ethereum|base> --format json <address>`
  - implementation/version diffs: `herd contract diff --blockchain <ethereum|base> --all --format json <address>`
  - verified code search or source retrieval: `herd contract code --blockchain <ethereum|base> --contract-address <address> --include-proxies --return-all-code --format json`
  - transaction inspection: `herd tx query --blockchain <ethereum|base> --format json <txHash>`
  - latest function calls or events: `herd tx latest --type function|event --contractAddress <address> --blockchain <ethereum|base> --format json`
  - wallet or contract address overview: `herd wallet overview --blockchain <ethereum|base> --format json <address>`
  - Herd documentation: `herd docs read --format json`

## Research Workflow

Use the selected research mode. For `Full Architecture Map`, the default unit of analysis is the project, not a single token. For `Targeted Contract Review`, map only the context required to explain the requested contract, function, user action, or data path. Read [references/contract-mapping-checklist.md](references/contract-mapping-checklist.md) when mapping contracts, [references/user-flow-and-fund-flow.md](references/user-flow-and-fund-flow.md) when reconstructing flows, and [references/output-template.md](references/output-template.md) when drafting a full report.

### Phase 1: Define Scope

- State the exact project under research.
- State whether the user also cares about a specific product, token, module, or contract address inside that project.
- State the relevant network or networks.
- State the user action or product path to explain, if one is already known.
- List the official resources that will anchor the rest of the work.

### Phase 2: Discover Official Resources

- Confirm the official website and docs domain.
- Confirm the official GitHub org and repository or repositories.
- Confirm the official frontend entry point if the product is user-facing.
- Confirm the official X/Twitter account and use it only as a supporting source.
- Build a short provenance table for each official resource before citing it elsewhere.

### Phase 3: Read The Docs Broadly Before Abstracting

- Read the relevant product and protocol sections before building the contract map.
- Build a project inventory first: products, tokens, vaults, pools, markets, redemption paths, registries, and shared infrastructure.
- Extract the product's own terminology, constraints, lifecycle, and exceptional mechanisms.
- Record what is unusual about this project before applying standard labels such as vault, router, pool, or queue.
- Use the docs to identify product-specific behaviors that must appear in the final output, even if they do not map neatly to common DeFi patterns.
- If the docs define a special liquidity model, off-chain workflow, redemption rule, actuarial process, or accounting convention, preserve that language and explain how it changes the technical design.

### Phase 4: Enumerate Core Modules And Contracts

- Scan official docs, official GitHub, deployment files, address registries, frontend constants, and verified contracts to enumerate the system.
- Prefer completeness over speed. Find the whole system before deep-diving one function.
- Separate shared infrastructure from product-specific infrastructure.
- Record all major products and the contracts that belong to each product.
- Record all protocol-issued tokens and how each token maps to one or more modules.
- Group contracts by responsibility, not by filename alone.
- Record contract address, network, proxy or implementation status, source path, and why the contract matters.
- If the official repo is incomplete, use the officially published addresses to find verified source code, proxy admin data, implementation contracts, and emitted events.

### Phase 5: Resolve Address To Code

For every important address:
- start with Herd MCP tools to identify contract type, proxy pattern, implementation pointer, historical implementations, key functions, events, and recent execution activity
- if Herd MCP is unavailable, use authenticated Herd CLI when it covers the chain, or stop before producing Herd-backed live chain conclusions for that address
- determine whether it is a proxy, implementation, clone, EIP-1967 proxy, beacon proxy, or direct deployment
- locate the verified source code if available
- follow the implementation pointer if the published address is only a proxy
- record the exact verified code location and contract name that supports the analysis
- fall back to bytecode, ABI, events, and storage layout inspection only if verified source is unavailable

Do not treat "address found" as the end of the job. Address provenance is the start of code analysis, not the end of it.

### Phase 6: Classify Architecture

Classify the system into concrete roles such as:
- entrypoints and routers
- pools, vaults, and accounting layers
- token contracts and wrappers
- oracle and pricing modules
- liquidation, risk, or execution modules
- governance, admin, guardian, or pause control
- registries, factories, and deployment helpers

State how modules depend on each other and where the system's control points sit.

At minimum, identify:
- project-wide shared infrastructure
- each user-facing product line
- each protocol-issued token and its role
- the contracts that bridge products together

### Phase 7: Analyze Core Contracts

For each core contract:
- explain its responsibility in one sentence
- identify the key externally reachable functions
- identify the important internal accounting or state transition functions
- identify emitted events that matter for tracing flows
- identify authorization boundaries, upgrade hooks, and external dependencies

Do not stop at ABI labels. Prefer Herd MCP function, event, and recent-transaction views first, then read implementation logic and describe what the function essentially is doing.

### Phase 8: Reconstruct User Flow

Start from the user-facing action, not from the contract in isolation:
- identify the frontend action, route, widget, or button
- identify the wallet action and signed transaction
- identify the entry contract function and parameters
- follow the downstream contract calls and state updates
- explain what the user receives back: shares, debt, receipts, minted assets, or bookkeeping updates
- explain any product-specific branch conditions described in the docs, such as queues, windows, caps, custody handoffs, off-chain attestation, or regulatory gating

### Phase 9: Trace Fund Flow And State Flow

Separate asset movement from bookkeeping:
- state where tokens are transferred from and to
- state which contract actually custodies assets
- state which contract records balances, debt, collateral, shares, or claims
- state whether assets are routed through adapters, wrappers, bridges, or executors
- state where price checks, mint limits, or solvency checks occur

If assets do not move but state changes do, say that explicitly.

### Phase 10: Check Control, Upgradeability, And Risk

- Identify admins, guardians, timelocks, multisigs, or governors.
- Identify proxy patterns and implementation upgrade paths.
- Identify external trust assumptions such as oracles, keepers, issuers, bridges, off-chain signers, or whitelists.
- Identify brittle paths where a single dependency or privileged role can halt or distort the system.

## Output Requirements

Choose output shape by mode:

- `Provenance Check`: short table of resources, status, evidence, and unresolved items.
- `Targeted Contract Review`: scope, provenance, contract role, key functions, related contracts, user flow, fund flow, state flow, permissions, verified facts, inferences, and open questions.
- `Full Architecture Map`: structured report with these sections:

1. Research object and scope
2. Official resource validation
3. Project overview and product inventory
4. Project-specific mechanisms and terminology
5. System overview
6. Contract inventory and classification
7. Core contract responsibilities
8. Key functions and call relationships
9. User flow from frontend to chain
10. Fund flow and state flow
11. Permissions, upgradeability, dependencies, and risk
12. Verified facts, inferences, and open questions

For every important claim, attach the verifying source:
- official URL
- official GitHub path
- contract address and network
- function name or event name where relevant

Always separate:
- `Verified`: directly supported by official sources or corroborated verified source code
- `Inference`: reasoned from code and architecture, with the basis stated
- `Open question`: unresolved because official evidence is missing or contradictory

## Minimum Standards

- Do not rely on third-party blog posts, dashboards, or aggregators for core architecture claims.
- Do not trust a contract address unless its provenance is demonstrated.
- Do not skip Herd-backed evidence once an address is official and live chain conclusions are needed; if Herd is unavailable, pause those conclusions instead of substituting unrelated chain tools.
- Do not stop after proving an address is official; continue into verified code, implementation resolution, and function-level analysis.
- Do not describe the system as a list of contracts only; explain relationships and flows.
- Do not compress away project-specific mechanisms just because they do not match a common DeFi pattern.
- Do not describe user flow without tracing both contract calls and asset destinations.
- Do not describe fund flow without also stating who holds assets and who updates balances.
