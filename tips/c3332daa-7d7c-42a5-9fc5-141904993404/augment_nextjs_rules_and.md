---

# 🧠 Agent Development Guidelines (Next.js + Drizzle ORM + PostgreSQL + Shadcn UI + TailwindCSS v4 + TypeScript)

## 🛠️ General Workflow

* Always use **pnpm** for all commands and package management.
* After any change in `lib/server/db/schema.ts`, you must run:

  ```bash
  bash db.sh -i
  ```

  This will (re)initialize the database schema.
* For any new technology or problem, search documentation online first.
* You have access to tools like **context7**, **Playwright**, and **sequential reasoning on MCP servers**. Use them.

## ⚙️ Dev Server Behavior

* When checking if the dev server is already running:

  * First, inspect the `ports.notes` file.
  * If a line contains `*dev-server`, that means the dev server is already manually started by the user.
  * Do **not** kill any process using the same port — the user intentionally opened it.
  * Never open a new random port; if the port is taken, trust that it’s the correct one and **do not interfere**.

## 🔧 Functions (Utility & Logic)

* Keep functions small: ideally 5–10 lines, max 20.
* Follow the **Single Responsibility Principle** (SRP): one task per function.
* Limit nesting (1–2 levels).
* Limit to 2–3 arguments per function. Group related args if necessary.

## 🧩 React (Next.js) Components

### Size & Structure

* Keep component files **< 200–300 lines**:

  * ✅ Ideal: <100 lines
  * ⚠️ Warning at 200 lines
  * 🚫 Refactor if >300 lines
* JSX in a render block should be <50 lines.

### Design Guidelines

* Each component should only do one thing (UI, logic, data — not all).
* Extract complex logic into hooks or utility functions.
* Limit props to 2–3. If more, group related ones in objects.
* Prefer **early returns** over nested ternaries or deeply nested conditions.

### TailwindCSS v4 Guidelines

* Use Tailwind v4 utilities only.
* Avoid long class strings inline — break them into multiple lines if needed.
* Global styles live in `global.css`, but prefer Tailwind utilities when possible.

### UI Library

* Use **Shadcn UI** components by default.
* Extend Shadcn components when needed, but don't override their core structure.

## 🧠 TypeScript Rules

* Always use `strict` mode (`strict: true` in tsconfig).
* Avoid `any`. Use `unknown` and type guards if unsure.
* All components, hooks, and util functions must be typed.

---
