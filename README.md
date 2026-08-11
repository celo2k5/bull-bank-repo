# BULL BANK - Solana Token Distribution Frontend

A sleek, real-time frontend for BULL BANK token distributions powered by WebSocket integration with the backend.

## Features

- 🔗 Real-time WebSocket connection to distribution backend
- 📊 Live stats: eligible holders, creator balance, distributed amount
- ⏱️ Distribution countdown timer
- 🎨 Dark theme with gold accents for dramatic bull aesthetic
- 📱 Responsive design
- 🔄 Auto-reconnect with exponential backoff
- 💰 Decimal precision support for token amounts
- 🎯 Mint-aware tracking across multiple tokens

## Usage

### Local Development

```bash
cd bull-bank-repo
# Serve index.html on localhost:3000 or similar
```

### Deployment

1. Push to GitHub
2. Deploy to Railway, Vercel, or any static host
3. Server automatically connects to `wss://marcelo-admin.up.railway.app`

### Query Parameters

- `?ca=<TOKEN_MINT>` — Lock stats to specific token mint

Example: `https://bull-bank.example.com/?ca=TokenMintHereXXXXXXXXXXXXXXXXXX`

## Backend Integration

- **WebSocket URL**: `wss://marcelo-admin.up.railway.app` (public, no auth)
- **Message Format**: `{type: string, data: T}`
- **Auto-reconnect**: Exponential backoff (1s → 15s)

Supported events:
- `state` — Initial hydration
- `tick` — Countdown updates
- `cycle_start`, `cycle_update`, `cycle_end` — Distribution lifecycle
- `transfer` — Live transfers
- `token_metadata` — Token info (image, symbol)
- `holders_update`, `holder_pnl_update`, `holder_sent_update` — Holder data
- `fee_claim`, `token_swap` — Transaction events

## Theme

- **Primary**: Deep black (#0a0a0a)
- **Surface**: Dark surface (#121212)
- **Accent**: Metallic gold (#d4af37)
- **Text**: Light gray (#e0e0e0)
- **Border**: Subtle border (#1a1a1a)

## File Structure

```
bull-bank-repo/
├── index.html              (Single-file frontend, embedded CSS/JS)
├── public/
│   ├── bull-bank-hero.png  (Hero image)
│   ├── favicon.png         (Browser tab icon)
│   └── favicon.ico         (Multi-size icon)
└── README.md
```

## Live Indicators

- 🟢 **Live**: Connected and receiving events
- 🟡 **Connecting**: WebSocket handshake in progress
- 🟠 **Reconnecting**: Retrying connection

---

Powered by BULL BANK · Solana Network
