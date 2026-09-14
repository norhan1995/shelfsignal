# ShelfSignal architecture

ShelfSignal is intentionally a small, inspectable loop rather than a general-purpose assistant.

```text
UCI transactions + synthetic ops overlay
        ↓
signal normalizer (demand, runway, lead time, expiry, uncertainty)
        ↓
intent scorer (weighted multi-word anchors + contradiction penalty)
        ↓
decision ranker (cost of waiting × confidence × actionability)
        ↓
one decision packet (evidence, alternatives, confidence, safe boundary)
        ↓
staged PO / transfer → manager approval or correction
```

## Data contract

Each signal contains a product, branch, demand window, current cover, open-order state, supplier lead time, expiry context, and optional external context such as weather or promotion. The demo keeps these values in a replayable local fixture so the workflow is deterministic.

## Intent inference

The browser scorer tokenizes the signal corpus and compares it against three operational prototypes: `Protect availability`, `Avoid expiry`, and `Test demand spike`. Multi-word anchors such as “days of cover”, “lead time”, and “above baseline” count more than single tokens. The confidence is reduced when the best and second-best intents are close. This is a transparent feature scorer, not a hardcoded screen transition and not an LLM wrapper.

## Decision packet

The surfaced packet has a typed purpose, confidence, evidence chips, recommended quantity or transfer, supplier/branch, and the weakest input. The main surface renders one packet; a small rail preserves sequence without exposing a KPI grid.

## Action boundary

The system may prepare a purchase order or branch transfer when confidence and policy permit. It never sends the action without the manager’s explicit approval. Corrections cancel the prior draft before a new plan is staged. The UI labels each state: `ACTION STAGED`, `RECOVERY READY`, or `COMMITTED · AUDIT LOGGED`.
