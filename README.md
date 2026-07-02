# Bx02 - GitHub Contribution Automation API

**Price: $1.50 USDC/call** | Powered by x402 protocol on Base

## Capabilities

| Action | Description |
|--------|-------------|
| `handle_fork_limit` | Fork-limit workaround via API (use when GitHub fork limit hit) |
| `api_pr_workflow` | Submit PR via GitHub API v3 — branch + PR in one call |
| `readme_editor` | Parse README, insert entry in correct category |
| `secure_token_cleanup` | Validate tokens, return cleanup protocol |

## Quick Start

```bash
# Install dependencies
npm install

# Deploy to Cloudflare Workers
npx wrangler deploy
```

## API Endpoints

- `GET /health` — Service health + pricing info
- `POST /v1/bx02` — Main API endpoint (requires x402 payment)

## Pricing

| Tier | Price |
|------|-------|
| Single call | $1.50 USDC |
| Bundle (10 calls) | $12.00 USDC |
| Bundle (50 calls) | $50.00 USDC |

## x402 Payment

All endpoints require x402 protocol payment:
- **Asset:** USDC on Base (0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913)
- **Network:** eip155:8453 (Base Mainnet)
- **Recipient:** 0x57EEC52d76A4A78D4562fc2564101A4bD2e3F357

## Example Usage

```javascript
// handle_fork_limit
const r1 = await fetch('https://bx02.YOUR_SUBDOMAIN.workers.dev/v1/bx02', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json', ...x402Headers },
  body: JSON.stringify({
    action: 'handle_fork_limit',
    params: { name: 'my-project', description: '...', auth_token: 'ghp_...' }
  })
});

// api_pr_workflow
const r2 = await fetch('https://bx02.YOUR_SUBDOMAIN.workers.dev/v1/bx02', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json', ...x402Headers },
  body: JSON.stringify({
    action: 'api_pr_workflow',
    params: { owner: 'USER', repo: 'repo-name', head_branch: 'feature', ... }
  })
});
```

## License

MIT — Built by prpo_ai for B0x70
