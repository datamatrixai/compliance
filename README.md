# Regulatory Reporting Intelligence Layer – Prototype

Client-demo prototype by DataMatrix.AI. Single static page, no backend, synthetic data only.

## Deploy on GitHub Pages
1. Create a repo (e.g. `regulatory-reporting-prototype`) and upload `index.html` and this README.
2. Repo **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*, Branch = `main`, folder = `/ (root)`.
3. Share the URL: `https://<your-username>.github.io/regulatory-reporting-prototype/`

If the repo is private, GitHub Pages needs a paid plan; otherwise make it public or send `index.html` directly (it works when opened locally).

## Demo script
1. Pick a template and customer C1001, click **Auto-populate**. Each field shows the best-match value, source, and reasoning.
2. Open the **Address** dropdown: current (utility bill), permanent, shop/factory, previous addresses. Change one and watch the audit trail and assurance score update.
3. Switch to customer C2002 to show validation catching a bad PAN, short mobile, future opening date, minor DOB and negative balance (gate = BLOCK).
4. Upload a CSV whose first row is field names (e.g. `Customer Name,PAN,Mobile,Residence Address,Net Worth`). Unmatched fields (Net Worth) are flagged as needing new sourcing.
5. Export the report CSV and the JSON evidence pack.

## How scoring works
Field confidence = 40% semantic match + 30% source authority + 30% freshness (static fields such as PAN ignore freshness).
Report assurance = weighted blend of source authority, match strength, freshness, cross-source consistency, validation pass rate, and share of fields human-reviewed.
Gate: any FAIL = BLOCK, any WARN = PASS WITH REVIEW, else PASS.

## Not in this prototype
Live connectors, real OCR/LLM matching, vintage record search across past filings, filing tracker, user roles. Matching here is rule/score based on sample data.
