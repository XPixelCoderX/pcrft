# PCrft Xbox Invite Bot

The **PCrft Xbox Invite Bot** is a two‑part system that makes inviting Bedrock players fast, simple, and automated. It combines a **Node.js Xbox Live bot** with a **Python-powered dark neon dashboard**, giving you a clean control panel for sending Xbox invites and helpful messages instantly.

---

## Features

- Safe Microsoft device login (no passwords stored)
- Connects to Xbox Live using `bedrock-portal`
- Works with any Bedrock server (e.g. `play.pcsmp.net`)
- Dark neon web dashboard
- One input: **Gamertag**
- Three actions:
  - **Invite**
  - **Send Message**
  - **Invite + Message**
- Auto message text:

> If you want to rejoin the server, add "PCrft" on Xbox, and you will be able to join through your friends list!

- Live portal status indicator
- Mobile‑friendly UI
- Can be put behind HTTPS using Nginx Proxy Manager

---

## Requirements

- Node.js 20+ (22 recommended)
- Python 3.9+
- An Xbox/Microsoft account for the bot
- A Bedrock server IP + port

---

## Installation

### 1. Clone the project

```bash
git clone https://github.com/yourname/pcrft-xbox-invite-bot.git
cd pcrft-xbox-invite-bot
