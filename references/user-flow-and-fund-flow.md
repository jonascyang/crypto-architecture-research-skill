# User Flow And Fund Flow

Reconstruct flows in a strict order. Start from the frontend action, then follow transaction execution, then separate asset movement from state updates.

## User Flow Sequence

For each important action, describe:
1. Frontend action
2. Wallet action
3. Entry contract and function
4. Downstream calls
5. State changes
6. User-visible result

Use concrete language:
- "User clicks Deposit"
- "Frontend prepares `deposit(uint256,address)`"
- "Wallet signs transaction to contract X on network Y"
- "Contract X transfers token A from user to vault B"
- "Vault B mints share token C"

## Fund Flow Questions

Answer all of these:
- Which asset leaves the user wallet?
- Which contract receives it first?
- Is that first recipient the final custodian or only a router?
- Which contract ultimately holds the asset?
- Which contract records balances, shares, debt, or claims?
- Which contract or module can later move or redeem that asset?

## State Flow Questions

Track:
- collateral balances
- debt balances
- share issuance
- receipt tokens
- oracle reads
- health factor or solvency checks
- fee accrual

State clearly when no asset transfer occurs and only accounting changes happen.

## Common Patterns To Check

- proxy -> implementation
- frontend -> router -> vault
- token wrapper -> core pool
- mint or burn module -> treasury or reserve
- manager contract -> strategy or executor
- oracle read -> risk check -> state update

## Reporting Rule

Write user flow and fund flow as ordered steps, not vague prose. If the path differs across networks or modes, split the paths instead of merging them.
