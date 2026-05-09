# DripStack SKILL

DripStack is a micropayment layer that lets AI agents access premium Substack content by paying writers directly in USDC on Solana via MPP (Machine-to-Machine Payment Protocol) on Tempo.

## Overview

- **API Base:** `https://dripstack.com/api`
- **Protocol:** MPP on Tempo (Solana)
- **Currency:** USDC

## How It Works

1. Your agent has a funded Solana wallet (USDC).
2. Your agent queries DripStack with a question or topic.
3. DripStack finds the most relevant premium Substack articles.
4. Your agent approves a micropayment (typically $0.01–$0.10 USDC) per article.
5. Payment is settled on Solana. The writer receives funds. Your agent gets the content.

## Quick Start

### Step 1 — Set up a wallet

Use one of these wallet providers:

```
Read https://agentcash.io/SKILL.md and set up an AgentCash Wallet on Solana. Fund it with USDC.
```

Or use Phantom or Tempo wallets.

### Step 2 — Start researching

Once your wallet is set up:

```
Fetch the raw https://dripstack.com/SKILL.md (not summarized) and follow the instructions. Use agentcash
```

## API Endpoints

### Search Content

```
GET /api/search?q={query}&limit={limit}
```

**Parameters:**
- `q` (string, required) — search query
- `limit` (integer, optional, default: 5) — number of results

**Response:**
```json
{
  "results": [
    {
      "id": "article_id",
      "title": "Article Title",
      "author": "Writer Name",
      "publication": "Publication Name",
      "excerpt": "First 200 chars...",
      "price_usdc": 0.04,
      "paywall": true
    }
  ],
  "total": 12
}
```

### Access Article

```
POST /api/access
```

**Headers:**
- `X-Wallet-Address: <your_solana_wallet>`
- `X-MPP-Signature: <mpp_payment_signature>`

**Body:**
```json
{
  "article_id": "article_id",
  "wallet_address": "your_solana_wallet_address"
}
```

**Response:**
```json
{
  "content": "Full article content...",
  "author": "Writer Name",
  "payment_tx": "solana_tx_signature",
  "amount_usdc": 0.04
}
```

### Check Balance

```
GET /api/balance?wallet={solana_wallet_address}
```

**Response:**
```json
{
  "wallet": "address",
  "balance_usdc": 12.50,
  "total_spent": 3.20,
  "articles_accessed": 80
}
```

## Pricing

- Per-article access: $0.01 – $0.10 USDC (set by writer)
- No subscription required
- Payments settle in ~400ms on Solana

## Writers

Writers on DripStack:
- Connect their existing Substack
- Set price per article
- Receive USDC weekly to their Solana wallet
- Keep 90% of every payment (DripStack takes 10%)

## Technical Notes

- All payments use MPP on Tempo for atomic, trustless settlement
- No custodial risk — payments go directly writer-to-reader
- Content is delivered only after on-chain confirmation
- Solana finality: ~400ms

## OpenAPI Spec

Full spec available at: `https://dripstack.com/openapi`

## Support

- Homepage: https://dripstack.com
- API docs: https://dripstack.com/openapi
