# DOO submission materials

## Project

**ShelfSignal**

## Tagline

The interface that protects the next shelf instead of asking you to scan every SKU.

## Repository

https://github.com/norhan1995/shelfsignal

## Live demo

`https://shelfsignal.nrifaie77.chatgpt.site`

## Write-up

ShelfSignal is an exception-first replenishment surface for pharmacy and health-and-beauty operations. It watches demand, on-hand stock, open purchase orders, supplier lead time, expiry, and policy. When the cost of waiting is high, it surfaces one decision packet: protect availability, avoid expiry, or test a demand spike. It stages a purchase order or branch transfer automatically, but requires a manager to approve it. If the context is wrong, the manager corrects one assumption; the prior draft is canceled before execution and the recommendation is recomputed with lower confidence.

The demo uses a public UCI Online Retail transaction schema plus clearly labeled synthetic branch and supplier overlays. The browser runs a transparent weighted signal scorer rather than an LLM wrapper or hidden API.

## Notes

AI tools helped with research synthesis, UX iteration, copy editing, and test-case generation. The decision contract, inference scorer, confidence threshold, approval boundary, and recovery behavior are explicit in the source. Out of scope: production ERP integration, live supplier orders, clinical recommendations, and undisclosed private data.
