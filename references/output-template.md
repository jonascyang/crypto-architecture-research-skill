# Output Template

Use this structure for the final report.

## 1. Research Object And Scope

- project name
- network
- product, token, module, or address under special focus if any
- official resources used

## 2. Official Resource Validation

| Resource | URL or path | Why it is official | Status |
| --- | --- | --- | --- |

## 3. Project Overview And Product Inventory

- project summary
- full product list
- protocol-issued token list
- shared infrastructure vs product-specific infrastructure

## 4. Project-Specific Mechanisms And Terminology

- concepts that are unique to the protocol
- special liquidity, redemption, attestation, compliance, or accounting rules
- how those mechanisms change the architecture

## 5. System Overview

- summary of the architecture
- main modules
- where entrypoints, asset custody, and accounting live

## 6. Contract Inventory And Classification

| Contract | Address | Network | Role | Proxy or impl | Source |
| --- | --- | --- | --- | --- | --- |

Add columns when helpful:
- Product
- Scope (`shared` or product-specific)

## 7. Core Contract Responsibilities

For each core contract:
- purpose
- key state
- why it matters in the user flow

## 8. Key Functions And Call Relationships

| Contract | Function | Purpose | Calls into | Notes |
| --- | --- | --- | --- | --- |

## 9. User Flow From Frontend To Chain

Use ordered steps from user click to final state change.

If the project has multiple products, give one short path per major product before deep-diving the requested path.

## 10. Fund Flow And State Flow

Use ordered steps and distinguish:
- asset movement
- accounting movement

## 11. Permissions, Upgradeability, Dependencies, And Risk

- admin roles
- upgrade paths
- oracle or external service dependencies
- operational or architectural weak points

## 12. Verified Facts, Inferences, And Open Questions

### Verified

List only directly supported facts.

### Inference

List reasoned conclusions and name the evidence used.

### Open Questions

List unresolved items and the missing official evidence.
