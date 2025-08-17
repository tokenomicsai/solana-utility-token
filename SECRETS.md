# GitHub Secrets Checklist

Add these in **Settings → Secrets and variables → Actions**:

- `SOLANA_RPC_URL` → Your RPC endpoint
- `MINT_CA` → Your token mint address
- `DECIMALS` → `9`
- `EXPECTED_SUPPLY` → `1000000000`
- `REQUIRE_NO_MINT_AUTH` → `true` (or `false` if not renounced yet)
- `REQUIRE_NO_FREEZE_AUTH` → `true` (or `false` if not renounced yet)

Optional:
- `UPDATE_AUTHORITY_PUBKEY`
- `TREASURY_PUBKEY`
- `ECOSYSTEM_PUBKEY`
