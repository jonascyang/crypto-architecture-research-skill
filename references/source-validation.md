# Source Validation

Use this checklist before accepting any repo, domain, frontend, or contract address as official.

## Allowed Core Sources

- Official website
- Official docs
- Official GitHub org and repositories
- Official frontend code or official deployed frontend resources
- Official X/Twitter account announcements
- Verified contract source code only after official provenance is established

Once an address is proven official, verified source code on the relevant chain explorer becomes a valid code-analysis source even if the corresponding GitHub repo is private or incomplete.

## Validation Order

1. Find the official website and docs.
2. Find the GitHub org or repo linked from those official surfaces.
3. Find the official X/Twitter account linked from the website, docs, or GitHub.
4. Cross-check that the same domains, org names, and repos appear across at least two official surfaces.
5. Accept contract addresses only if they are confirmed by at least two official surfaces or by one official surface plus the official frontend code.

## Resource Acceptance Matrix

Accept a resource as official only if at least two of these checks pass:

| Resource | Check 1 | Check 2 | Check 3 |
| --- | --- | --- | --- |
| Website | Linked by docs | Linked by GitHub/org | Linked by official X |
| Docs | Same domain family as website or explicitly linked | Linked by GitHub/org | Referenced by official X |
| GitHub | Linked by website or docs | Repo/org links back to official domain | Referenced by official X |
| Frontend | Same official domain or official repo path | Uses official addresses/constants | Referenced by docs |
| Contract address | Published in docs | Present in official repo/frontend constants | Announced by official X |

## Phishing And Impersonation Red Flags

- Similar-looking domain with no link from docs or GitHub
- GitHub org or repo with the right name but no backlink to the official domain
- Address lists published only in a third-party article or gist
- Frontend app with different domains, different assets, or mismatched contract constants
- X/Twitter account that mentions the project but is not linked by official docs or website

## Evidence Discipline

- Treat search engine results as leads, not evidence.
- Treat third-party explorers as execution aids, not provenance by themselves.
- Treat explorer-hosted verified source as a valid code source only after the contract address itself has been corroborated by official project resources.
- If provenance is weak, mark the item `Unverified` and exclude it from core conclusions.
- If sources conflict, show the conflict explicitly instead of choosing one silently.
