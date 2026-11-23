# CheesePad agent skills

Skills that let an AI agent trade on [CheesePad](https://www.cheesepad.ai) from a Binance
Agentic Wallet.

| Skill | What it does |
| --- | --- |
| [`cheesepad`](skills/cheesepad/SKILL.md) | Find, buy and sell on Melt Curves. Contribute to, claim from and refund presales, fair launches, subscriptions and microsales, including Agent ID-only ones. |

## Install

Tell your agent:

```
Install the CheesePad skill from https://github.com/cheesepad-ai/cheesepad-agent-skills
```

Or install it yourself (Node.js 22.20 or later):

```bash
npx skills add https://github.com/cheesepad-ai/cheesepad-agent-skills
```

It works with agents that load Agent Skills, such as OpenClaw and Claude Code. To get a newer
version later, run `npx skills update`.

## Before you start

1. Create an Agentic Wallet in the Binance App and sign in on the agent's device:
   `baw auth signin`. The skill needs the `baw` CLI (`npm install -g @binance/agentic-wallet`).
2. Turn on Developer Mode: Agentic Wallet management page → Settings → Developer Mode. It lasts
   7 days and renews with each use.
3. For Agent ID-only launches, claim an Agent ID: Binance App → Web3 Wallet → Agent ID.

Then ask in plain words, for example "buy 0.05 BNB of CHEESE on CheesePad".

## How it works

1. The agent asks the CheesePad API (`https://api.cheesepad.ai`, public, no login) for
   ready-to-send transaction steps.
2. For each step it shows Binance's transaction preview, then sends it with
   `baw contract-call` only after you say yes.
3. It refuses any step that isn't addressed to the CheesePad contract for that chain.

| Chain | Chain ID | Melt Curves and sales | Agent ID-only |
| --- | --- | --- | --- |
| BNB Smart Chain | 56 | yes | yes |
| Robinhood Chain | 4663 | yes | no |

Agents can't create launches. Sales that need a contribution signature, and finalized overflow
sales, are on the website only.

Full guide: [AI agents and the Binance Agentic Wallet](https://docs.cheesepad.ai/docs/developers/ai-agents).

## Layout

```
skills/
  cheesepad/
    SKILL.md        entry point: routing, chains, rules that always apply
    references/     one file per task: find, buy, sell, sales, Agent ID, safety
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). To report a security issue, see [SECURITY.md](SECURITY.md).

## Disclaimer

The skill sends nothing without your yes on each step, and it gives no investment advice. New
tokens are high risk and you can lose what you put in. Check every preview before you confirm.

## License

[MIT](LICENSE)
