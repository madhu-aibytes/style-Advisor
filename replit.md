# ClothedInYou Workspace

## Overview

pnpm workspace monorepo using TypeScript. Full-stack AI fashion recommendation web app.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **Frontend**: React + Vite + TailwindCSS + Wouter (routing)
- **API framework**: Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **Build**: esbuild (CJS bundle)
- **Auth**: Cookie-based session auth with SHA-256 password hashing
- **UI Libraries**: lucide-react, framer-motion, clsx, tailwind-merge

## Application: ClothedInYou

AI-based personal styling assistant that recommends colors and outfits based on:
- Gender (Women / Men)
- Body type (Women only: Apple, Pear, Hourglass, Rectangle, Inverted Triangle, Diamond)
- Skin tone (Fair, Light, Deep/Dusky, Dark)
- Undertone (Cool, Warm, Neutral)

### Pages
1. **Landing Page** (`/`) - Hero with lavender gradient, Login and Signup buttons
2. **Signup Page** (`/signup`) - Name, Email, Password registration
3. **Login Page** (`/login`) - Email, Password login
4. **Gender Selection** (`/gender-select`) - Women or Men cards
5. **Mode Selection** (`/mode-select`) - Manual Mode or Image Mode (placeholder)
6. **Manual Mode** (`/manual-mode`) - Select body type, skin tone, undertone
7. **Image Mode** (`/image-mode`) - Coming soon placeholder
8. **Results** (`/results`) - Color palette + outfit recommendations by category

### Design Theme
- Lavender / Purple gradients
- Colors: #E6E6FA, #C084FC, #A855F7, #7C3AED
- Card-based layout, soft shadows, rounded corners

## Structure

```text
artifacts-monorepo/
├── artifacts/
│   ├── api-server/         # Express API server
│   └── clothed-in-you/     # React + Vite frontend (preview at /)
├── lib/
│   ├── api-spec/           # OpenAPI spec + Orval codegen config
│   ├── api-client-react/   # Generated React Query hooks
│   ├── api-zod/            # Generated Zod schemas from OpenAPI
│   └── db/                 # Drizzle ORM schema + DB connection
└── scripts/                # Utility scripts
```

## API Endpoints

- `GET /api/healthz` — Health check
- `POST /api/signup` — Create user account
- `POST /api/login` — Login
- `POST /api/logout` — Logout
- `GET /api/me` — Get current user
- `POST /api/recommend` — Get fashion recommendations

## Database Schema

### users
- `id` (serial PK)
- `name` (text)
- `email` (text, unique)
- `password` (text, SHA-256 hashed)

## Dev Commands

- Frontend: `pnpm --filter @workspace/clothed-in-you run dev`
- Backend: `pnpm --filter @workspace/api-server run dev`
- DB push: `pnpm --filter @workspace/db run push`
- Codegen: `pnpm --filter @workspace/api-spec run codegen`
