# YAO Inventory Dashboard

- `inventory-dashboard.html`: single-file web page (Inventory & Open PO, Billing & Delivery Terms, PO Receipt Calendar). Open it in any browser; no server needed.
- `agents/`: assistant definitions used in the working session (production-planner, website-developer, ux-designer, logistics-planner, task-delegation-architect).

Note: The Billing tab contains customer names and conditions. Keep this repository private.

## Lot expiry rules (applies to every lot, now and in future updates)

- **Lot code starts with DDMMYYYY** (for example `16102027` or `21072027FGBB`): the lot's expiry date is that DDMMYYYY date. Confidence is `confirmed`.
  - Tier by days remaining vs. the as-of date: `EXPIRED` below 0, `WATCH30` at 30 days or fewer, `WATCH90` at 90 days or fewer, otherwise `OK`.
- **No date in the lot code, Penta OEM lot (e.g. `IJ02`):** expiry = manufacturing date + shelf-life days from the product's expiry criteria (Excel, "ตามวันผลิต"). Confidence is `estimated`. Tier by % of shelf life left: `>=80%`, `70-80%`, `60-70%`, `<60%`, or `EXPIRED`.
- **Ambiguous codes** (`YYYYMM` prefix such as `202601EABD` and `202709FCCA`): not parsed. Confirm the expiry date before importing.
- Product expiry summary = the in-stock lot with the earliest expiry.
