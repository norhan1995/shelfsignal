# 90-second walkthrough

**0–10s — contrast.** Show the spreadsheet/ERP mock and the blank prompt. Say: “A manager should not have to scan every SKU or explain the question to a chatbot.”

**10–28s — proactive cue.** Land on ShelfSignal’s live decision surface. Four exceptions exist, but only the highest-cost-to-ignore one is expanded: four days of cover, a six-day supplier lead time, and demand up 31%. The system has already staged a 24-unit PO.

**28–45s — evidence to action.** Point to the right-side trace: data arrived, the intent was inferred, and the action was staged. Click **Approve purchase order**. The state changes to `COMMITTED · AUDIT LOGGED`; the demo makes clear that no order was sent before human approval.

**45–68s — failure.** Click **Simulate wrong context**. Choose **On-hand count is stale** or **Short promotion spike**. The previous PO is canceled before execution, confidence drops below the auto-stage threshold, and a safer recovery plan appears.

**68–82s — recovery.** Show the corrected intent, the new staged action, and the visible audit trace. Switch to another exception to prove the scorer recomputes instead of playing one hardcoded flow.

**82–90s — thesis.** End on: “AI should own the watch, the synthesis, and the reversible preparation. Humans should own the consequential decision.”
