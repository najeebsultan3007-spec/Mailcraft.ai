# MailCraft AI Backend v2

Backend server with built-in **Admin Panel** — no code editing needed to set your API key.

---

## Quick Start (Local)

```bash
npm install
cp .env.example .env
node server.js
```

Then open: **http://localhost:3001/admin**

Default admin password: `mailcraft2024`  
(Change via `ADMIN_PASSWORD` in `.env`)

---

## Folder Structure

```
mailcraft-v2/
├── server.js          ← Main backend server
├── package.json
├── .env.example       ← Copy to .env
├── public/
│   └── admin.html     ← Admin panel (auto-served at /admin)
└── README.md
```

---

## Admin Panel Features

| Feature | Description |
|---------|-------------|
| 🔑 API Key Config | Add/update Anthropic key from browser |
| ✅ Connection Test | Test if API key works with one click |
| ⚙️ Settings | Change model, token limit, rate limit |
| 📖 Docs | How to connect frontend, deploy guide |

---

## Deploy on Railway

1. Push this folder to GitHub
2. railway.app → New Project → Deploy from GitHub  
3. Add env variables:
   - `ANTHROPIC_API_KEY=sk-ant-...`
   - `ADMIN_PASSWORD=your-secret-password`
   - `ALLOWED_ORIGINS=https://your-frontend-domain.com`
4. Done — you get a URL like `https://mailcraft-xxx.railway.app`

Then in `index.html` set:
```js
const USE_BACKEND = true;
const BACKEND_URL = 'https://mailcraft-xxx.railway.app';
```

---

## API Endpoints

| Method | Path | Auth | Description |
|--------|------|------|-------------|
| GET | `/` | None | Server info |
| GET | `/health` | None | Health check |
| GET | `/admin` | None | Admin panel UI |
| POST | `/api/generate` | None | Generate email |
| GET | `/admin/config` | Admin | Get config |
| POST | `/admin/config` | Admin | Update config |
| POST | `/admin/test` | Admin | Test API key |
