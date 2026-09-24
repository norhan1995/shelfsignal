# ShelfSignal

ShelfSignal is an action-first AI interface for pharmacy and health-and-beauty replenishment. It replaces the morning spreadsheet/ERP scan and the blank “which SKUs should I reorder?” chatbot prompt with one ranked exception and one accountable next decision.

Open the live demo: **https://shelfsignal.nrifaie77.chatgpt.site**

## The 90-second story

1. A sales trend, on-hand count, open PO, supplier lead time, and policy arrive as one operational signal.
2. ShelfSignal infers the operational intent: protect availability, avoid expiry, or test a demand spike.
3. It surfaces only the highest-cost-to-ignore exception and shows the evidence behind it.
4. It stages a reversible purchase order or branch transfer automatically, but a manager must approve it.
5. If the on-hand count is stale or a promotion explains the spike, the manager corrects that one context field. The old plan is canceled before execution and a new plan is staged.

## Run locally

This is a dependency-free static application. The readable source lives in `src/index.html`, while `dist/index.html` is the deployable static artifact. Serve the `dist` directory with any static server:

```bash
python3 -m http.server 4173 --directory dist
```

Then open http://localhost:4173.

## What is real

- The sample transaction schema and seed rows are from the public [UCI Online Retail dataset](https://archive.ics.uci.edu/dataset/352/online%2Bretail), which contains 541,909 UK retail transactions and is licensed CC BY 4.0.
- Branch inventory, supplier lead time, expiry, and policy fields are clearly labeled synthetic overlays. They make a purchase-order decision possible without pretending the public dataset is pharmacy data.
- The browser runs a deterministic weighted signal scorer. It combines multi-word anchors, demand/expiry language, uncertainty, and a confidence threshold. There is no hidden API call or chat model.
- Every state transition is visible in the decision trace: incoming data → inferred intent → staged action → human commit or recovery.

## Repository map

- `src/index.html` — readable source for the responsive demo and local inference engine.
- `dist/index.html` — deployable static artifact used by the live demo.
- `data/online-retail-sample.csv` — small provenance-labelled sample from the UCI schema.
- `docs/ARCHITECTURE.md` — data, inference, decision, and action contract.
- `docs/COMPETITION.md` — public-pattern research and differentiation.
- `docs/DEMO.md` — judging flow and walkthrough script.
- `docs/SECURITY.md` — autonomy boundary and failure handling.
- `docs/TESTING.md` — deterministic checks and manual acceptance tests.
- `docs/THESIS.md` — two-year view on post-chatbot interfaces.
- `docs/SUBMISSION.md` — copy-ready challenge submission materials.

## Out of scope

ShelfSignal is a decision-surface prototype, not a live purchasing system. It does not connect to a pharmacy ERP, send supplier orders, make clinical recommendations, or claim the synthetic inventory overlay came from the UCI file.
