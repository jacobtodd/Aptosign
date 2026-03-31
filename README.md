# Aptosign

A lightweight, client-side tool for signing and verifying messages using the [Petra Wallet](https://petra.app) on the Aptos blockchain.

**No backend. No server. Zero data leaves your browser.**

## Features

- **Connect Petra Wallet** — one-click wallet connection with auto-reconnect
- **Sign Messages** — sign any text message using your Aptos private key (Ed25519)
- **Verify Signatures** — cryptographically verify any message signed through Aptosign
- **Copy-to-clipboard** — click any field value to copy it instantly
- **Auto-fill** — the Verify tab is automatically populated after signing

## How it works

### Signing

When you sign a message, Petra prefixes it with the Aptos standard format before signing:

```
APTOS
message: <your message>
nonce: <nonce>
```

The resulting `fullMessage`, `signature`, and `publicKey` are all you need to prove ownership of an address.

### Verification

Verification is done entirely in the browser using [TweetNaCl](https://tweetnacl.js.org) (Ed25519). The `fullMessage` is checked against the `signature` and `publicKey` — no private key or wallet required.

## Usage

1. Open `index.html` in a browser with the Petra extension installed
2. Click **Connect Petra** and approve the connection
3. **Sign tab** — enter a message and click Sign Message
4. **Verify tab** — paste the output fields and click Verify Signature

## Deployment

### GitHub Pages

1. Push this repo to GitHub
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)`
4. Your tool is live at `https://<your-username>.github.io/Aptosign`

## Requirements

- [Petra Wallet](https://petra.app) browser extension (Chrome/Brave/Firefox)
- Any modern browser

## Security notes

- Signing a message does **not** authorize any transaction — it is purely cryptographic proof of key ownership
- Always verify the content of what you are signing before approving in Petra
- This app has no analytics, no network requests, and no dependencies beyond TweetNaCl (loaded from jsDelivr CDN)

## Tech stack

- Vanilla HTML/CSS/JS — no build step, no framework
- [TweetNaCl](https://github.com/dchest/tweetnacl-js) for Ed25519 verification
- [Petra Wallet](https://petra.app) `window.aptos` API for signing
