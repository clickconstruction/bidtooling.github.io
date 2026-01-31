# Plumbing Bid Worksheet

Single-page web app for building plumbing bids: job details, fixture counts, labor and materials, markups, and client-ready summaries. Built for Click Plumbing and Electrical; runs in the browser with no backend (static HTML + JS).

## Features

### Top bar

- **Fill with sample** — Populates the form with sample data for testing.
- **Clear all fields** (top right) — Resets the form, hides summaries, and clears the URL hash. Handy when viewing someone else’s shared plan. Tooltip: "Viewing someone else's plan? Clear the form to start fresh."

### Job information

- Customer name/address, job name/address, bid date, bid number.
- **Bid number** is auto-suggested from date (YYMMDD) and job name (e.g. `251224-SVP-Chicos`); you can override it.
- Required: customer name, job address, bid date, bid number.

### Fixture counts

- Grid of fixture types (toilets, sinks, showers, tubs, water heaters, etc.) with quantities.
- **Plan Page Ledger** (right column): saved plan pages; **Load** fills the grid from that page; **Delete** removes it. **Total fixtures** appears below the title; **Export Labor Summary** produces a PDF of ledger pages (fixture tables).
- At the bottom of the section: **Clear counts**, **Plan page:** (input), and **Upload to Ledger** (all left-aligned).

### Fixture prices

- Toggle **Fixture mode** (residential vs commercial) for different price sets.
- Optional table of prices and labor times; **Reset to default**; **Export my prices and times** (JSON).

### Fixture Material Takeoffs

- Collapsible section (coming soon from PipeTooling.com); item/qty rows. Collapsed by default.
- Delete/Backspace clears the focused field.

### Additional Labor and Materials

- **Fixture Labor Estimate:** Rough in / Top out / Trim hours on the left; total fixtures, manhours, and cost on the right.
- **Additional labor** (work not included in fixture price): rows for description, hours, crew, rate with crew multiplier. Delete/Backspace clears the focused labor field.
- **Crew pricing ($/hr):** Collapsible at the bottom with 1 Tech, Plumber and Helper, 3 Techs rates.
- **Additional materials:** Description and amount rows; Delete/Backspace clears the focused material field. **Add row** at the bottom.
- **Labor total** (Hours • Rate) and grand total logic feed into the Pricing section.

### Pricing

- Table of fixture labor, materials, additional labor (with optional markups) and **Grand Total**. No separate additional-materials block here; that lives in Additional Labor and Materials.

### Rough calculator

- Optional L×W → SF, cost per SF, fixture count, price per fixture → rough bid.

### Inclusions / Exclusions and scope / Terms and warranty

- Multi-line text; included in summaries and PDFs.

### Internal summary

- **View** toggles a detailed preview (fixtures, labor, materials, totals); **Print** prints that view.
- Button turns orange when the summary is visible; click again to hide.

### External summary

- **View** toggles a client-facing summary (letterhead style, proposal amount, inclusions, scope, terms).
- **Copy Text**, **Download PDF**, **Print**. Same orange toggle behavior.

### Google Doc

- One-click copy flow (copy letterhead/text, then paste in a new doc); instructions show "Click once → ⌘+V".

### Share via URL

- Copy button builds a URL with the current form state (job info, fixtures, ledger, labor, materials, inclusions, scope notes — not terms) and copies it; address bar updates.
- If the URL is long (>2000 chars), a modal warns that it was copied and to use apps that support long URLs.
- **Email** button opens a mailto with the same URL and subject = bid number.

### Reset

- **Reset Fields** (below Rough Calculator) clears the form only.
- **Clear all fields** (top right) clears form, hides/clears external summary, and removes the share hash from the URL.

## Share via URL

Opening a link with a `#...` hash restores the saved state (job info, fixtures, ledger, labor, materials, inclusions, scope notes; terms use the app default). Useful for sending a pre-filled bid to someone; they can edit and re-share or clear and start fresh with **Clear all fields**.

## Keyboard shortcuts

- **Delete / Backspace** in fixture materials (takeoff), additional labor, or additional materials: clears the focused input (or crew select resets to first option); does not remove the row.

## Tech and deployment

- **Stack:** Single HTML file (`index.html`), inline CSS and JavaScript; [jsPDF](https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js) for PDF export. No build step; no server-side logic.
- **Hosting:** Suited for static hosting (e.g. GitHub Pages). `CNAME` points to bidtooling.com. Open `index.html` in a browser or serve the folder with any static server.
- **Browser:** Modern browsers with JavaScript enabled; clipboard and optional `replaceState` for share URL.

## Repository files

- `index.html` — App (single file).
- `favicon.svg` — Favicon.
- `make-a-copy.png` — Google Doc step image.
- `CNAME` — Custom domain (bidtooling.com).

No dependencies to install.
