# Clean Otter — AI-Launched Meme Coin on Solana (SPL)

This repository contains:
- **/site** → the public website (static, GitHub Pages–ready)
- **/scripts** → verification & injection scripts
- **/.github/workflows** → CI to auto-verify your mint daily
- Transparency docs (**AUDIT.md**, **SECURITY.md**, **COMPLIANCE.md**)

> Replace placeholders such as `Ottertok`, `[TICKER]`, `MINT_PUBLIC_KEY`, `MOONSHOT_TOKEN_URL` throughout the repo.
> Or run the **inject** script to fill them automatically.

## Quick Start

1) **Clone & install**  
```bash
git clone <your-repo-url>.git
cd <repo>
npm install
cp .env.example .env
# fill in your RPC URL and MINT (or run inject below)
```

2) **(Optional) Inject your real values**  
```bash
npm run inject --   --coin "MyCoin"   --ticker "MYC"   --mint MINT_PUBLIC_KEY_HERE   --moonshot https://moonshot.url/your-token   --updateAuth UPDATE_AUTHORITY_PUBKEY   --treasury TREASURY_PUBKEY   --ecosystem ECOSYSTEM_PUBKEY   --firstTx FIRST_TX_SIGNATURE   --metadataPda METADATA_PDA
```

3) **Verify the mint** (decimals, supply, authorities)  
```bash
npm run verify
```
Expected checks:
- Decimals = 9
- Supply = 1,000,000,000 * 10^9
- Mint Authority = None (if you enabled REQUIRE_NO_MINT_AUTH)
- Freeze Authority = None (if you enabled REQUIRE_NO_FREEZE_AUTH)

4) **Website**  
- The full static site lives in **/site**.  
- You can host via GitHub Pages (Settings → Pages → Source: Deploy from branch → `/site`).  
- Update **site/index.html** with your values OR use the inject script above.

## Environment

Copy `.env.example` to `.env` and fill values:

```
RPC_URL=https://api.mainnet-beta.solana.com
MINT=MINT_PUBLIC_KEY
DECIMALS=9
EXPECTED_SUPPLY=1000000000
REQUIRE_NO_MINT_AUTH=true
REQUIRE_NO_FREEZE_AUTH=true
```

## CI Verification (GitHub Actions)

The workflow in `.github/workflows/verify.yml` runs `npm run verify` on each push and on a daily schedule.  
Set the following **Repository Secrets** in GitHub:
- `SOLANA_RPC_URL`
- `MINT_CA`
- `DECIMALS` (default `9`)
- `EXPECTED_SUPPLY` (default `1000000000`)
- `REQUIRE_NO_MINT_AUTH` (`true` or `false`)
- `REQUIRE_NO_FREEZE_AUTH` (`true` or `false`)

## Disclaimers

- **Not financial advice.** Tokens are volatile and can go to zero.
- Utilities marked “Planned” are **not live** until verifiable on-chain or via partner endpoints.
- We publish authority status, liquidity actions, and proof transactions for transparency (see `AUDIT.md`).

