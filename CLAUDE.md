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

Single-page React app with no routing, no backend, and no persistence.

**Component tree:**
```
App                          — holds transactions[] state, passes it down
├── Summary                  — computes and displays totalIncome, totalExpenses, balance
├── TransactionForm          — owns its own form state; calls onAdd(transaction) prop
└── TransactionList          — owns filter state; receives transactions[] as prop
```

`App.jsx` lives in `src/`. All reusable components live in `src/components/`.

**Transaction data model:**
```js
{ id, description, amount, type: "income"|"expense", category, date }
```
`amount` is always a numeric value (not a string).

**Categories** are a hardcoded array defined in both `TransactionForm.jsx` and `TransactionList.jsx`: `["food", "housing", "utilities", "transport", "entertainment", "salary", "other"]`.

**Known issues (intentional for course exercises):**
- `Freelance Work` is typed as `"expense"` instead of `"income"` in the seed data.

Styling is plain CSS in `src/App.css` with class names `.income-amount`, `.expense-amount`, `.balance-amount` used for green/red coloring.