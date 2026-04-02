# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev      # Start dev server at http://localhost:5173
npm run build    # Production build
npm run lint     # Run ESLint
npm run preview  # Preview production build
```

No test suite is configured.

## Architecture

Single-page React app with no routing, no backend, and no persistence — all state lives in `useState` in `src/App.jsx`.

**Transaction data model:**
```js
{ id, description, amount, type: "income"|"expense", category, date }
```

**Known issues (intentional for course exercises):**
- `amount` is stored as a string, so `totalIncome`/`totalExpenses` use string concatenation instead of numeric addition — the summary cards show wrong values.
- `Freelance Work` is typed as `"expense"` instead of `"income"` in the seed data.

**Categories** are a hardcoded array: `["food", "housing", "utilities", "transport", "entertainment", "salary", "other"]`.

Styling is plain CSS in `src/App.css` with class names `.income-amount`, `.expense-amount`, `.balance-amount` used for green/red coloring.