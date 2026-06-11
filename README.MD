<div align="center">
  <img src="https://cdn.nefusoft.cloud/0rK13.png" alt="Lumina Proxy" width="200"/>
</div>

<h1 align="center">✨ @lumina-npm/proxy ✨</h1>

<p align="center">
  A lightweight proxy fetching library to bypass web restrictions — part of the Lumina ecosystem.
</p>

<p align="center">
  <a href="https://www.npmjs.com/package/@lumina-npm/proxy"><img src="https://img.shields.io/npm/v/@lumina-npm/proxy.svg" alt="NPM Version"></a>

</p>

---

`@lumina-npm/proxy` is a modern, promise-based HTTP proxy client. It routes your requests through a pool of web proxy servers to help you fetch content that would otherwise be inaccessible.

### 🚀 Features

- **Simple & Intuitive API** — Get started in seconds with a clean, modern API.
- **Flexible Server Selection** — Pick from a wide range of US and EU servers manually.
- **Built-in Retry Mechanism** — Smart `.auto()` mode retries with a different server on failure.
- **Multiple Usage Patterns** — Simple function calls, client factory, or drop-in `fetch` replacement.

### 📦 Installation

```bash
npm install @lumina-npm/proxy
```

### 📖 Usage

#### 1. Basic (`proxy`)

```javascript
import proxy from '@lumina-npm/proxy';

// Default: us1 server
const html = await proxy('https://example.com');

// With specific server
const html2 = await proxy('https://example.com', { region: 'eu', serverId: 15 });
```

#### 2. Client Factory (`createProxyClient`)

```javascript
import { createProxyClient } from '@lumina-npm/proxy';

const client = createProxyClient({ region: 'us', serverId: 7 });

const page1 = await client.fetch('https://example.com/page1');
const page2 = await client.fetch('https://example.com/page2');
```

#### 3. Auto Mode (`proxy.auto`)

Handles server selection and retries automatically.

```javascript
import proxy from '@lumina-npm/proxy';

const html = await proxy.auto('https://example.com', { region: 'us', retries: 3 });
```

#### 4. Drop-in Fetch Replacement (`createProxyFetch`)

```javascript
import { createProxyFetch } from '@lumina-npm/proxy';

const proxyFetch = createProxyFetch({ region: 'us', serverId: 1 });

const response = await proxyFetch('https://example.com');
const html = await response.text();
```

### ⚙️ Options

| Key | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `region` | `string` | `'us'` | Server region: `'us'` or `'eu'` |
| `serverId` | `number` | `1` | Server ID, from 1 to 20 |
| `retries` | `number` | `2` | Retry count for `.auto()` mode |

### 🌐 Available Servers

| US (`us`) | EU (`eu`) |
| :--- | :--- |
| US1 – US20 | EU1 – EU20 |

---

<p align="center">
  Built with ✨ by <a href="https://github.com/hiuraaaaa">Nefu</a> — part of the <strong>Lumina</strong> ecosystem.
</p>
