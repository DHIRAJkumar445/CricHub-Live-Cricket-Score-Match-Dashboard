# CricHub

Cricket match management app with **Node.js** and **PHP** backends and **JWT authentication**.

## Quick Start (Node.js - Recommended)

1. Install dependencies and start the server:

```bash
npm install
npm start
```

2. Open **http://localhost:3000** in your browser.

3. **Register** a new account at [Register](http://localhost:3000/register.html), then **Login**. The Admin page is protected and requires login.

## Alternative: PHP Backend

If you prefer PHP:

1. Start PHP built-in server:

```bash
npm run start:php
```

2. Open **http://localhost:8000** and add this before using login/register (e.g. in browser console or a small script):

```javascript
window.API_BASE = 'http://localhost:8000/api';
```

3. Or add to `index.html` before other scripts:

```html
<script>window.API_BASE = 'http://localhost:8000/api';</script>
```

## Scripts

| Command | Description |
|--------|-------------|
| `npm start` | Node.js server (API + static files) on port 3000 |
| `npm run start:php` | PHP server on port 8000 |
| `npm run start:static` | Python static server (no auth API) |
| `npm test` | Run Jest tests |

## Authentication

- **Register**: Create account with username and password (min 4 chars)
- **Login**: JWT token stored in localStorage
- **Admin**: Protected; redirects to login if not authenticated
- **Logout**: Clears token and redirects to login

## Project Structure

```
crichub/
├── api/           # PHP API (login.php, register.php)
├── server/        # Node.js Express API
├── js/
│   ├── auth.js    # JWT auth (Node or PHP)
│   └── api-config.js
├── index.html
├── login.html
├── register.html
└── admin.html    # Protected
```

## API Endpoints (Node.js)

- `POST /api/register` - Register user
- `POST /api/login` - Login
- `GET /api/me` - Current user (requires `Authorization: Bearer <token>`)

## Notes

- Set `JWT_SECRET` env var in production
- Users stored in `server/data/users.json` (Node) or `api/data/users.json` (PHP)
