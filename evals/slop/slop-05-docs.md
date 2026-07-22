---
profile: docs
expected_flags:
  - template phrases
  - filler phrases
  - passive voice and subjectless fragments
  - cutoff disclaimers
  - chatbot artifacts
---

## Getting started with the export API

Whether you're a solo developer or an enterprise team, this guide covers everything you need.

It is important to note that API keys must be created before any request can be made. Keys are generated in the dashboard. No configuration needed. Once created, the key should be passed in the Authorization header.

As of my last update, the rate limit was 100 requests per minute, though specific details may vary based on available information. In terms of pagination, results are returned in pages of 50.

The reality is that most integrations only need the /export endpoint. Requests are validated automatically, and malformed payloads are rejected before processing.

Great question if you're wondering about webhooks: they are covered in the next section. I hope this helps! Feel free to reach out to support if you need anything.
