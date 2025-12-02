# Skydiving Logbook

A modern web application that replaces traditional paper logbooks for skydivers, streamlining jump recording with auto-incremented jump numbers, pre-filled repetitive fields.

---

## Table of Contents

1. [Tech Stack](#tech-stack)
2. [Getting Started Locally](#getting-started-locally)
3. [Available Scripts](#available-scripts)
4. [Project Scope](#project-scope)
5. [Project Status](#project-status)
6. [License](#license)

---

## Tech Stack

- **Framework:** [Astro 5](https://astro.build/)
- **UI:** React 19 + shadcn/ui + Tailwind CSS 4
- **Language:** TypeScript 5
- **Backend & Auth:** Supabase (PostgreSQL, Row-Level Security)
- **Build Tooling:** Vite, ESLint, Prettier, Husky + lint-staged
- **CI/CD:** GitHub Actions (automatic build & deployment)

---

## Getting Started Locally

> Requires **Node 22.14.0** (see `.nvmrc`). Use `nvm` or `fnm` to match the project version.

```bash
# 1. Clone the repo
git clone https://github.com/<your-org>/skydiving-logbook.git
cd skydiving-logbook

# 2. Install dependencies
npm install     # or pnpm install / yarn install

# 3. Start the dev server
npm run dev

# 4. Open the app
# The server runs on http://localhost:4321 by default
```

Optional:

```bash
# Run ESLint
auth npm run lint
# Format code with Prettier
npm run format
```

---

## Available Scripts

| Command            | Description                                |
| ------------------ | ------------------------------------------ |
| `npm run dev`      | Start the Astro dev server with hot reload |
| `npm run build`    | Generate the production build              |
| `npm run preview`  | Preview the production build locally       |
| `npm run astro`    | Direct access to the Astro CLI             |
| `npm run lint`     | Run ESLint on all source files             |
| `npm run lint:fix` | Run ESLint with `--fix`                    |
| `npm run format`   | Format files with Prettier                 |

---

## Project Scope

**In Scope (MVP)**

- User profile with personalized data (canopy model and size, exit weight, default dropzone)
- Supabase authentication (email & password)
- Server-side auto-incremented jump numbers
- Batch entry modal with inline edit/delete before save
- Sortable & filterable logbook table
- Default dropzone data

For full functional requirements see [PRD](./.ai/prd.md).

---

## Project Status

🚧 **Active development.** Core MVP features are being implemented.

---

## License

This project is currently **unlicensed**.

---
