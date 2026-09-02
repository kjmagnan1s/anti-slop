---
profile: technical-blog
expected_flags:
  - mannered prose
  - density
---

Retrieval quality is the dial worth turning first, because every downstream stage inherits whatever the retriever hands it, and a reranker that has to rescue a bad candidate set is spending its budget on triage rather than on the ranking work it was built to do, which is why teams that skip this step tend to discover it months later in the form of a support queue. The chunking strategy earns its keep here: overlap that looks wasteful on paper is the thing that keeps a boundary from swallowing the one sentence that answered the question, and the cost of that overlap is a rounding error next to the cost of a wrong answer delivered with confidence. Embedding models are a garden that needs tending as the corpus grows, and the moment the vocabulary of new documents drifts from the vocabulary the index was built on, recall starts to bleed out quietly, which is the failure that nobody notices until a user does.
