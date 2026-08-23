# MigrantLife AI — Submission Summary

## Recommended track

Choose **Track 2: code-heavy with LangChain + LangGraph**.

This concept wins through retrieval quality, jurisdiction control, citations, confidence-based refusal, multilingual questions, and evaluation—not primarily through integrations. The code track makes each of those differentiators visible and testable.

## What is included

- Working Streamlit chat app
- LangGraph route → retrieve → decide → answer/fallback flow
- Hybrid BM25 + switchable local/Pinecone dense retrieval
- Pinecone serverless index creation, namespace isolation, metadata filtering, and idempotent corpus sync
- Topic and jurisdiction reranking
- Fifteen curated official-source notes with freshness metadata
- Citation validation and privacy/safety boundaries
- Twenty-question benchmark, including Spanish, edge, out-of-scope, and unanswerable cases
- Twelve automated tests
- Project documentation and five-minute demo script

## Verified results

- 12/12 automated tests passed
- 100% retrieval hit@3 on the 17 answerable development questions
- 100% answer/fallback routing on the 20-question development set
- 100% topic routing and citation-reference validity
- Browser smoke test passed for the Streamlit UI
- Live Pinecone index contains 30 chunks in the `official-sources-v1` namespace
- Live Pinecone evaluation retained 100% tuned-set metrics with 75.1 ms mean and 110.6 ms p95 latency
- 13/15 source URLs responded directly to the automated freshness check; the NY State of Health page returned an anti-bot 403 and ACCESS NYC timed out, so both are flagged for manual browser review rather than treated as dead links

These are tuned development-set results, not a claim of production readiness. The next evaluation should be a blinded set from recent newcomers and service navigators.

The Pinecone integration is implemented, contract-tested, and live-tested. No API key is stored in the project or submission package; configure a rotated key in the ignored local `.env` to reconnect.

## Run locally

    python -m venv .venv
    .venv\Scripts\Activate.ps1
    python -m pip install -r requirements-dev.txt
    python -m pip install -e .
    python -m pytest
    python scripts/evaluate.py
    streamlit run app.py

## Best demo sequence

1. School documents and the temporary-housing exception.
2. Spanish out-of-state driver-license question.
3. Notario scam warning with trusted legal-help source.
4. Los Angeles school question to demonstrate jurisdiction refusal.
5. Evaluation report, including the real failure found and fixed.
