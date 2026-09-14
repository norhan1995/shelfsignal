# Verification

## Static checks

```bash
node --check /tmp/shelfsignal-check.js
test -f dist/index.html
test -f .openai/hosting.json
```

The page is dependency-free and served from `dist/`; all interaction logic is in the page’s module-free script.

## Manual acceptance checks

1. Open the page and confirm a decision card and staged action are visible without typing.
2. Click each of the four exception tabs. The evidence, confidence, action, and case hash update.
3. Click **Approve purchase order**. Confirm the state becomes `COMMITTED · AUDIT LOGGED` and the copy says manager approval was required.
4. Reload and click **Adjust inference**. Choose a stale count or promotion spike. Confirm the prior PO is canceled, confidence drops, and a recovery action appears.
5. Resize to a narrow viewport. Confirm there is no horizontal overflow and the controls remain usable.
6. View the “What this replaces” section. Confirm the spreadsheet and chatbot contrast is visible beside ShelfSignal.

## Deterministic intent test

The local scorer uses the same fixture text every time. Availability signals contain runway/lead-time/demand anchors; expiry signals contain expiry/transfer anchors; spike signals contain temporary/weather/promotion anchors. The surfaced intent changes when the selected case changes, not because of an API response.
