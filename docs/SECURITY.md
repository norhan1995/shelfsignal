# Safety and failure thinking

ShelfSignal is a prototype decision surface. It is deliberately bounded:

- No supplier order is transmitted from the demo.
- The system can stage a draft, never silently commit it.
- The approval control is explicit and changes the visible state.
- A correction cancels the previous draft before another action appears.
- Low confidence changes the action from “approve” to “verify” or “hold.”
- Synthetic branch, supplier, expiry, and policy fields are labeled as overlays.

The primary failure test is wrong context. A stale on-hand count can make a real demand trend look like a stockout; a short promotion can make a temporary spike look persistent. The recovery path lets the manager correct that one assumption, recomputes the recommendation, lowers confidence when appropriate, and records the transition in the on-screen trace.

This build does not make clinical decisions, purchase real inventory, or connect to production ERP credentials.
