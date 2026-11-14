# instaleys

> Instagram Bot Framework for Node.js following the `@neoxr` / `znx-v5` architecture.

## Features

- **High-Level Client**: Event-driven Instagram bot client (`client.on('message', ctx => ...)`, `client.on('connect', ...)`)
- **Plugin System**: Built-in hot-reloading `Loader` that scans plugins and commands recursively
- **Modular Architecture**: Inspired by `@neoxr/wb` and `@neoxr/tg`
- **SQLite Proxy**: Auto-saving SQLite database proxy for bot state, users, groups, settings, and statistic
- **Full Messaging API**: `reply`, `sendMessage`, `sendFile`, `sendAlbumMessage`, `sendReact`, `sendMessageModify`
- **Built-in Utilities**: `Utils.Styles`, `Utils.texted`, `Utils.formatSize`, `Utils.toTime`, `Utils.greeting`, `Utils.example`
- **Spam & Cooldown**: Built-in rate limiting and anti-spam detection
- **Bundled Tools**: `dotenv`, `colors`, `chalk`, `cfonts`, `syntax-error` included

## Installation

```bash
npm install github:krsna081/instaleys
```

## Quick Start

```javascript
import 'dotenv/config'
import { Client, Utils, Proxy, Config } from 'instaleys'

// Initialize SQLite database proxy
Proxy.proxySqlite.startDbAutoSave(15000)

// Create client
const client = new Client({
   plugsdir: 'plugins',
   session: 'session'
})

// Listen for incoming messages
client.on('message', async (ctx) => {
   const { m, command, args, isPrefix } = ctx
   if (command === 'ping') {
      m.reply('Pong!')
   }
})

// Connect to Instagram
client.connect()
```

## License

ISC
