# RAG-Powered Search & Discovery

> **Role:** Consultant ML Engineer
>
> **Context:** Mid-sized European E-commerce marketplace (multi-country, broad product catalog, few thousand daily orders)



> '4% improvement in search-to-purchase conversion'
>
> '30% reduction in "no results found" searches'
>
> 'Sub-500ms p99 latency'


##

### The Problem

The marketplace’s existing search stack was built around **keyword matching and rule-based ranking**. While functional at small scale, it struggled as the catalog and user base grew:

* Natural-language and multi-constraint queries failed frequently
* Long-tail products were under-discovered
* Synonyms, attributes, and multilingual queries were poorly handled
* A significant fraction of searches returned **“no results”**, even when relevant products existed

From a business perspective, search was a **high-intent surface**, but relevance failures directly translated into lost conversions and user frustration.

The challenge was not just to “add an LLM,” but to design a **production-grade, low-latency, cost-efficient system** that could improve relevance without destabilizing the platform.

---

### Business Definition of Success

We defined success in **operationally measurable terms**, aligned with product and finance stakeholders:

* **Primary metric:**

  * *Search-to-purchase conversion* (relative improvement vs control)
* **Secondary metrics:**

  * Reduction in “no results found” queries
  * Latency SLOs (p95 / p99)
  * Error rate under peak load
* **Explicit non-goals:**

  * We did **not** require AOV uplift for success
  * We did **not** optimize for long conversational responses

The system had to be:

* Fast enough for real-time use
* Cheap enough to run continuously
* Observable and governable in production

---

### Data & Indexing Foundations

**Data sources**

* Product catalog (titles, descriptions, attributes, specs)
* Category and brand metadata
* Historical search queries and clickstream events
* Product images
* User interaction signals (views, clicks, add-to-cart)

**Indexing strategy**

* Semantic chunking of product text and metadata
* Separate indexes for:

  * Textual content
  * Attribute-heavy fields
* Vector + keyword hybrid indexing to balance recall and precision
* Strict versioning of embeddings and index schemas to avoid silent drift

This foundation ensured retrieval quality was **traceable, reproducible, and debuggable**.

---

### Retrieval & Generation Architecture

Rather than a “chatbot-first” design, we treated the LLM as **one component in a retrieval pipeline**:

1. **Query understanding**

   * Light query normalization and expansion
   * Intent classification (navigational vs exploratory)

2. **Hybrid retrieval**

   * Vector search for semantic recall
   * Keyword/BM25 search for precision and exact matches
   * Adaptive top-K selection based on query complexity

3. **Reranking**

   * Contextual reranker incorporating relevance and business constraints
   * Guardrails to prevent over-fetching and latency blowups

4. **Generation (minimal by design)**

   * Short, structured responses
   * No verbose descriptions unless explicitly required

This architecture was deliberately chosen to **minimize token usage**, control cost, and keep latency predictable.

---

### Production Architecture & MLOps

**Real-time inference**

* Async API running on containerized compute with autoscaling
* Sub-500ms p99 latency under peak load
* Circuit breakers and graceful degradation paths

**Evaluation & monitoring**

* Offline metrics: recall@k, MRR
* Online metrics: conversion, “no results” rate
* LLM-as-judge for sampled quality checks
* Drift monitoring on:

  * Query distributions
  * Retrieval outputs
  * Embedding versions

**CI/CD & governance**

* Model and index versioning
* Canary deployments and rollback
* Load-tested capacity envelopes
* Explicit cost budgets per query

---

### Business & Operational Impact

After staged rollout and controlled experiments:

* **~4% relative improvement in search-to-purchase conversion**
* **~30% reduction in “no results found” searches**
* **Stable sub-500ms p99 latency**, including during traffic spikes

Importantly, these gains were achieved **without introducing heavy operational complexity or runaway costs**.

---

### Cost & Capacity Discipline

A key design constraint was **cost predictability**:

* Token usage minimized via short prompts and responses
* Caching for repeated and popular queries
* Model tiering (cheap models for most traffic, larger models only when needed)
* Capacity planning driven by measured per-node throughput and headroom

This allowed the system to scale with traffic while keeping per-query cost firmly bounded.

---

### What I Learned

This project reinforced several production-grade lessons:

* **Search relevance improvements compound slowly but reliably** — even single-digit conversion gains matter at scale.
* **Most e-commerce search does not need “chatty” LLMs**; retrieval quality matters more than generation verbosity.
* **Cost is a first-class ML metric** in real-time systems.
* **Observability beats intuition** — silent failures in retrieval pipelines are more dangerous than obvious model crashes.
* **Conservative metrics build trust** with product, finance, and leadership teams.

Overall, this project demonstrated how LLMs can be integrated into core commerce systems **responsibly**, with measurable impact, strong ROI, and production-grade reliability.

---


