# Contract Mapping Checklist

Use this checklist when building the full project-wide architecture map.

## For The Whole System

Collect:
- all user-facing products
- all protocol-issued tokens and wrappers
- network or networks
- deployment registries, factories, and address lists
- major product modules
- key tokens, wrappers, vaults, pools, routers, executors, and accounting contracts
- governance and admin control contracts

## Project Inventory

Before deep-diving contracts, answer:
- What are the project's main product lines?
- Which tokens belong to which product lines?
- Which contracts are shared across the whole protocol?
- Which contracts exist only for one product or one chain?
- Which modules are operational infrastructure rather than user-facing products?

## For Each Contract

Record:
- contract name
- address
- network
- proxy, beacon, clone, or direct deployment pattern
- implementation address if applicable
- official source path or verified code location
- primary responsibility
- user-facing or internal-only role
- provenance path showing how the address was tied back to official resources

## Address To Code Resolution

For every core address:
- check whether the published address is a proxy
- resolve the implementation if present
- capture the verified contract name and explorer code URL
- record whether the ABI and source are fully verified or only partially available
- if no source is verified, note that explicitly and switch to ABI, events, and bytecode-assisted analysis

## Function-Level Review

For each core contract, identify:
- key external functions
- key internal functions that move assets or update balances
- events required to trace user actions
- access control modifiers or permission checks
- external calls into other contracts or oracles
- any project-specific logic that does not fit generic router, vault, or pool behavior

## Architecture Classification

Classify contracts into roles such as:
- router or entrypoint
- pool or vault
- token or wrapper
- accounting or share ledger
- oracle or pricing
- liquidation or keeper
- governance, pause, admin, guardian
- registry or factory

Also classify each contract by scope:
- shared protocol infrastructure
- product-specific infrastructure
- chain-specific deployment

## Relationship Questions

Answer these questions explicitly:
- Which contracts are true entrypoints?
- Which contracts custody assets?
- Which contracts only route calls?
- Which contracts maintain accounting state?
- Which contracts enforce risk checks?
- Which contracts can upgrade, pause, mint, seize, or reconfigure the system?
- Which contracts exist only because of project-specific constraints described in the docs?
