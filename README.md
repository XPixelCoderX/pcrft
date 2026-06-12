# PCrft Xbox Invite Bot

The **PCrft Xbox Invite Bot** is a two-part system that makes inviting Bedrock players fast, simple, and automated. It combines a **Node.js Xbox Live bot** with a built-in dark dashboard, providing a clean control panel for sending Xbox invites and helpful messages instantly.

---

## Features

* Secure Microsoft Device Login authentication
* No passwords stored locally
* Connects to Xbox Live using `bedrock-portal`
* Compatible with any Minecraft Bedrock Edition server
* Modern dark gray dashboard
* Simple Gamertag-based interface
* Three quick actions:

  * Invite
  * Send Message
  * Invite + Message
* Live portal status indicator
* Mobile-friendly design

### Default Message

Configured in `config.yml`:

```yaml
message:
  text: >
    If you want to rejoin the server, add "PCrft" on Xbox,
    and you will be able to join through your friends list!
```

---

## Requirements

### Node.js

* Node.js 20 or newer
* Node.js 22 recommended

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

### 2. Install Node Dependencies

```bash
npm install
```

This installs:

* `bedrock-portal`
* `prismarine-auth`
* `express`
* `cors`
* `js-yaml`

---

## Configuration

Edit `config.yml`:

```yaml
server:
  ip: "play.pcsmp.net"
  port: 19132
  world_version: "26.23"

bot:
  cache_folder: "./cache"
  api_port: 3000

message:
  text: >
    If you want to rejoin the server, add "PCrft" on Xbox,
    and you will be able to join through your friends list!
```

---

## Running the Bot

Start the bot and dashboard:

```bash
npm start
```

The HTTP dashboard and API will be available at:

```text
http://127.0.0.1:3000
```

Open your browser and navigate to:

```text
http://127.0.0.1:3000
```

If you are accessing from another machine, replace `127.0.0.1` with your server IP.

---

## First-Time Login

On the first launch:

1. `bedrock-portal` and `prismarine-auth` will generate a Microsoft Device Login URL and code in the Node.js console.
2. Open the URL shown in the console, or visit:

```text
http://127.0.0.1:3000/auth
```

3. Click the Microsoft Device Login link.
4. Enter the provided code from the console.
5. Sign in with your Microsoft/Xbox account.

After authentication:

* Tokens are stored in the configured cache folder.
* Future launches automatically reuse cached credentials.
* No passwords are stored.

---

## Using the Dashboard

Open the dashboard in your browser.

Enter a player's Xbox Gamertag.

Select one of the following actions:

### Invite

Sends an Xbox invite.

### Send Message

Sends the configured message from `config.yml`.

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

If the portal shows **Offline** or **Error**, check the Node.js console logs.

---

## Project Structure

```text
pcrft/
├── bot.js
├── config.yml
├── package.json
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

---

## Future Ideas

Possible future additions:

* Recent invite history stored in a JSON file
* Dashboard activity log
* Multiple message templates
* Invite statistics
* Webhook notifications
* Multiple bot account support
