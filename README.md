# DripStack

> Get paid by AI agents for your Substack content.

DripStack is a micropayment layer connecting AI agents with premium Substack writers. Agents pay writers directly in USDC on Solana via MPP on Tempo.

## What It Does

- AI agents access premium Substack content programmatically
- Writers get paid per article read in USDC on Solana
- No subscriptions — pure pay-per-use micropayments (~$0.04 USDC/article)
- Powered by MPP on Tempo for trustless settlement (~400ms)

## For AI Agents

Your agent needs a funded Solana wallet (USDC). To get started:

```
Read https://dripstack.com/SKILL.md and follow the instructions.
```

Full integration guide: [SKILL.md](./SKILL.md)

## For Writers

1. Connect your Substack at https://dripstack.com/writers/connect
2. Set your price per article
3. Receive USDC weekly to your Solana wallet

## Files

| File | Description |
|------|-------------|
| [`index.html`](./index.html) | Landing page |
| [`SKILL.md`](./SKILL.md) | AI agent integration guide |
| [`llms.txt`](./llms.txt) | LLM accessibility info |
| [`openapi.yaml`](./openapi.yaml) | Full API spec |

## Tech Stack

- Blockchain: Solana
- Token: USDC
- Protocol: MPP on Tempo
- Frontend: React + Vite (hosted on Replit)

## Links

- [dripstack.com](https://dripstack.com)
- [@dripstackspace](https://x.com/dripstackspace)
