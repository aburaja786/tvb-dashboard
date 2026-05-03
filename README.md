# Topi Vappa Biriyani — Owner's Cockpit Dashboard

## What's in this folder

| File | Purpose |
|------|---------|
| `index.html` | The dashboard. Don't edit unless you know HTML. |
| `data.js` | All the data. **You edit this** to add new months. |
| `README.md` | This file. |

---

## ⚠️ Important: This dashboard cannot be opened by double-clicking on your laptop

Modern browsers block local file loads for security. The dashboard needs to be either:
- **Hosted online** (GitHub Pages — see below) — recommended ✅
- **Run via a local server** (Python `python -m http.server`) — for testing only

---

## 🚀 Step-by-step: Host on GitHub Pages (FREE, permanent URL)

### One-time setup (15 minutes)

**Step 1 — Create a free GitHub account**
- Go to https://github.com/signup
- Use any email; pick a username (e.g. `tvb-owner`)
- Verify email

**Step 2 — Create a new repository**
- Click the **`+`** icon (top-right) → **New repository**
- Repository name: `tvb-dashboard`
- Set it to **Public** (required for free GitHub Pages)
- ✅ Check **"Add a README file"**
- Click **Create repository**

**Step 3 — Upload your dashboard files**
- On the repo page, click **Add file** → **Upload files**
- Drag and drop **both** `index.html` and `data.js` into the upload area
- Scroll down → click **Commit changes**

**Step 4 — Enable GitHub Pages**
- Click the **Settings** tab (top of repo page)
- In the left sidebar, click **Pages**
- Under "Build and deployment":
  - Source: **Deploy from a branch**
  - Branch: **main** / folder: **/ (root)**
  - Click **Save**
- Wait 1–2 minutes
- Refresh the page — you'll see a green box saying:
  > **Your site is live at https://YOUR-USERNAME.github.io/tvb-dashboard/**

**Step 5 — Bookmark that URL** — that's your permanent dashboard. Share it with your business partner.

---

## 📝 Step-by-step: How to update data each month (DIY)

You no longer need me to rebuild anything. Here's how to add April 2026:

### Method A — Edit directly on GitHub (easiest, recommended)

1. Go to your repo: `https://github.com/YOUR-USERNAME/tvb-dashboard`
2. Click on **`data.js`**
3. Click the **pencil icon** (top-right of file view) to edit
4. Make your edits (see "What to edit" below)
5. Scroll down → **Commit changes**
6. Wait 30 seconds → refresh your dashboard URL → new month appears!

### Method B — Edit on your computer

1. Download `data.js` from GitHub
2. Open it in **any text editor** (Notepad, VS Code, Sublime — even TextEdit on Mac)
3. Make your edits
4. Save the file
5. Upload back to GitHub (drag-drop, replaces the old one)

---

## What to edit in `data.js`

The file has 8 sections. To add a new month, you'll typically edit 3–4 of them.

### 1. `window.MONTHS` — Monthly P&L summary

Find the **last entry** (the one for March 2026, marked `mar26`). It looks like:

```javascript
{
  key:'mar26', label:'Mar 2026', short:'Mar \'26', ym:'2026-03',
  sales:{cash:794.661, card:5776.192, talabat:2118.710, ...},
  totalSales:8721.233, salesExclCom:7769.717,
  food:{mutton:938.300, chicken:699.320, ...},
  ...
}
```

**Copy that entire `{ ... }` block** (including the comma after the closing brace), paste it after, and update the values for April 2026.

### 2. `window.DAILY` — Daily POS data

Append new entries from your **PetPooja Day-End Summary** reports. Each entry:

```javascript
{date:"2026-04-01", dow:"Wednesday", invoices:42, card_sales:152.50, cash_close:80.20, var_cash:0, var_card:0, shifts:1}
```

### 3. `window.CAT_DATA` — Category-wise sales

Add a new month key (e.g. `"2026-04"`) with category data from your **PetPooja Sales Report Category Wise**.

### 4. `window.EXP_TXNS` — Expense transactions

Append entries from your **PetPooja Expense Report** detail rows:

```javascript
{ym:"2026-04", date:"2026-04-15", category:"MUTTON", amount:140.00, explanation:"Pending bills payment", employee:"biller", paid_from:"From Cash"}
```

---

## ⚠️ JavaScript syntax rules (critical!)

When editing `data.js`, follow these rules:

1. **Strings need quotes**: `label:'Apr 2026'` ✅ — not `label:Apr 2026` ❌
2. **Use straight quotes** `'` and `"` — NOT curly quotes `'` `"` (Word does this automatically — that's why I recommend Notepad/VS Code, not Word)
3. **Decimal point**, not comma: `123.45` ✅ — not `123,45` ❌
4. **Comma after every entry** except the last one in an array
5. **Don't delete the closing `]` or `}`** — they match opening brackets

If something breaks, the dashboard will show "Could not load data.js". Just **undo your last edit on GitHub** (Commits → Revert) and try again.

---

## 🆘 Troubleshooting

| Problem | Solution |
|---------|----------|
| Dashboard shows "Could not load data.js" | You broke the syntax. Revert your last commit on GitHub. |
| Charts don't appear | Same as above — check the browser console (F12) for errors. |
| Numbers look wrong | Verify the values you copied match the source PDFs/spreadsheets. |
| Want me to verify your edits | Send me the updated `data.js` and I'll check it. |

---

## 📊 What the dashboard shows

7 tabs:
1. **⚡ Top 5 Priorities** — ranked by financial impact, drilldown on click
2. **Financials** — P&L trends, food cost %, channel mix
3. **Expense Detail** — vendor leaderboard, pending bills, 1,321 searchable transactions
4. **⚠ Reconciliation** — gaps between Expense Report (cash) and P&L (accrual)
5. **Menu** — category performance, top 20 items, discount intensity
6. **Operations** — hourly demand, daily heatmap, day-of-week patterns
7. **Ledger** — monthly P&L table + daily POS table with month filters

---

*Built with ❤️ for TVB Ruwi Muscat Branch · v4.0*
