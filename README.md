# PCrft Xbox Invite Bot

The **PCrft Xbox Invite Bot** is a two-part system that makes inviting Bedrock players fast, simple, and automated. It combines a **Node.js Xbox Live bot** with a **Python-powered dark neon dashboard**, providing a clean control panel for sending Xbox invites and helpful messages instantly.

---

## Features

* Secure Microsoft Device Login authentication
* No passwords stored locally
* Connects to Xbox Live using `bedrock-portal`
* Compatible with any Minecraft Bedrock Edition server
* Modern dark neon dashboard
* Simple Gamertag-based interface
* Three quick actions:

  * Invite
  * Send Message
  * Invite + Message
* Live portal status indicator
* Mobile-friendly design
* Easy HTTPS setup with Nginx Proxy Manager

### Default Message

> If you want to rejoin the server, add "PCrft" on Xbox, and you will be able to join through your friends list!

---

## Requirements

### Node.js

* Node.js 20 or newer
* Node.js 22 recommended

### Python

* Python 3.9 or newer

### Other

* Xbox / Microsoft account for the bot
* Minecraft Bedrock server IP and port

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/XPixelCoderX/pcrft.git
cd pcrft
```

---

### 2. Install Node Dependencies

```bash
npm install
```

This installs:

* bedrock-portal
* prismarine-auth
* express
* cors
* js-yaml

---

### 3. Install Python Dependencies

```bash
pip install -r requirements.txt
```

This installs:

* flask
* requests
* pyyaml

---

## Configuration

Edit `config.yml`:

```yaml
server:
  ip: "play.pcsmp.net"
  port: 19132
  world_version: "1.21.80"

bot:
  cache_folder: "./cache"
  api_port: 3000
  auto_start: true

dashboard:
  host: "0.0.0.0"
  port: 5000
  title: "PCrft Invite Panel"
  message_text: >
    If you want to rejoin the server, add "PCrft" on Xbox,
    and you will be able to join through your friends list!
```

---

## Running the Bot

Start the dashboard:

```bash
python dashboard.py
```

### What Happens

1. `dashboard.py` automatically starts `bot.js`
2. `bot.js` launches the Xbox Portal API on:

```
http://localhost:3000
```

3. Flask hosts the dashboard on:

```
http://0.0.0.0:5000
```

Open your browser and navigate to:

```
http://your-server-ip:5000
```

---

## First-Time Login

On the first launch:

1. `bedrock-portal` and `prismarine-auth` will generate a Microsoft Device Login URL and code.
2. Open the URL shown in the Node.js console.
3. Enter the provided code.
4. Sign in with your Microsoft/Xbox account.

After authentication:

* Tokens are stored in the configured cache folder.
* Future launches automatically reuse cached credentials.
* No passwords are stored.

---

## Using the Dashboard

1. Open the dashboard in your browser.
2. Enter a player's Xbox Gamertag.
3. Select one of the following actions:

### Invite

Sends an Xbox invite.

### Send Message

Sends the configured message.

### Invite + Message

Sends both an invite and the configured message.

---

## Status Indicator

The dashboard includes a live portal status pill:

| Status  | Meaning                         |
| ------- | ------------------------------- |
| Online  | Xbox portal is running normally |
| Offline | Portal is not running           |
| Error   | API or authentication issue     |

If the portal shows Offline or Error, check the Node.js console logs.

---

## HTTPS Setup (Optional)

### Nginx Proxy Manager

Ensure `dashboard.py` is running on port `5000`.

Create a new Proxy Host:

#### Details

Domain:

```
invite.yourdomain.com
```

Forward Host:

```
your-server-ip
```

Forward Port:

```
5000
```

#### SSL

Enable:

* Request a new Let's Encrypt certificate
* Force SSL
* HTTP/2 Support
* HSTS

Your dashboard will then be available at:

```
https://invite.yourdomain.com
```

---

## Project Structure

```text
pcrft/
├── bot.js
├── dashboard.py
├── config.yml
├── package.json
├── requirements.txt
├── cache/
└── README.md
```

---

## Security

* Uses official Microsoft Device Authentication
* No password storage
* Authentication tokens stored locally
* Does not bypass Xbox Live security systems
* Respects Microsoft authentication requirements

---

## Disclaimer

This project is intended for managing Xbox invites for Minecraft Bedrock Edition communities. Users are responsible for complying with Microsoft's Terms of Service and Xbox Live policies.

---

## License

MIT License

```

Copyright (c) PCrft

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files to deal in the Software without restriction.
```
