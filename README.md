# Expense Tracker — JavaScript Mini Project

## Run the project

1. Extract the ZIP.
2. Open `dist/index.html` in Chrome, Firefox or Edge.
3. Add an income transaction (for example, Allowance ₹5,000).
4. Add an expense (for example, Food ₹120).
5. Try editing, deleting, filtering and exporting the transactions.

No installation, API key or internet connection is required for the downloaded app. If your browser restricts storage for local files, run `python3 -m http.server 8000 --directory dist` in the project folder and open `http://localhost:8000`.

## Files

| File | Purpose |
| --- | --- |
| `dist/index.html` | Accessible form, summaries and transaction table |
| `dist/style.css` | Responsive layout and visual styling |
| `dist/core.js` | Validation, calculations, filters and CSV generation |
| `dist/script.js` | DOM events, CRUD actions and localStorage |
| `PROJECT_REPORT.md` | Abstract, objectives, architecture, algorithm and viva |
| `verify.cjs` | Automated checks for calculations and interface state |

## Features

- Add income and expenses in a global currency selector with names and ISO codes. Each currency has its own balance.
- Switch between light, dark and system themes, remembered between visits.
- Set and remove monthly budgets per currency, with progress and overspending indicators.
- Edit entries and confirm deletion.
- View income, expenses and net balance for all time or a selected month.
- Search descriptions and filter history by type and category.
- View expenses grouped by category.
- Save transactions between visits with localStorage.
- Export the filtered history as CSV.
- Use the responsive interface on mobile or desktop.

The selected currency applies to summaries, history, breakdowns and CSV exports. No currency conversion is performed. The budget uses its own month field; selecting a summary month also selects that budget month. Summary cards and spending breakdown use the month filter. Search, category and type filters affect the history and CSV export only.

## Example demonstration

Add Allowance ₹5,000 (Income / Allowance), Lunch ₹120 (Expense / Food) and Bus fare ₹40 (Expense / Transport) with today's date. The expected balance is ₹4,840. Edit Lunch to ₹100: the balance becomes ₹4,860. Delete Bus fare: the balance becomes ₹4,900. Reload to show persistence. Filter Food and export the CSV.

## Verification

Run `node verify.cjs`. Checks cover money arithmetic, currency isolation, decimal precision, legacy INR migration, monthly budgets, theme persistence, invalid input, filtering, CSV escaping, CRUD flows, saved-data reload, failed writes and the optional summary tool. The interface-state checks use a lightweight simulated DOM; they do not replace visual browser testing.

## Storage and limitations

This is a frontend educational project. Data is stored on the current browser profile and origin, not in a database. It is not synchronized between devices, browsers or the hosted and downloaded versions. Private browsing and clearing browser data can remove it. CSV is an export only; importing backups is not implemented. There is no login or encrypted ledger. Use fictional data for classroom demonstrations.

## Possible future improvements

Recurring entries, CSV import, user authentication and database synchronization can be added as a separate next phase.

## Currencies, themes and budgets

Choose a currency from the top-right selector; options include currency codes and names. Existing transactions stay in their original currency, and old rupee-only records are restored as INR. Currency selection changes the ledger being viewed and the currency for new entries. It does not convert past entries. Currency-specific decimal precision is enforced: JPY uses whole units, INR/USD use two decimal places, KWD uses three. The catalogue is provided by browser internationalization support with a bundled fallback; some supported options are historical currencies.

Choose Light, Dark or System in the theme selector. System follows your operating system theme and responds to changes.

Select a budget month, enter a positive limit and click Save budget. Income does not increase the spending limit. Expenses alone count toward the budget. Above the limit, the status shows the amount over budget; the progress bar stops at 100% while the text reports the actual percentage. Remove budget clears only that currency/month limit.

Transactions are saved under `expense-tracker-v2`; preferences and budgets use `expense-tracker-settings-v2`. On first load, existing `expense-tracker-v1` data is read as INR. The old key is retained, and the new key is created when you save a transaction. Keep the same host and port when replacing local project files to retain browser data.
# expensetracker
