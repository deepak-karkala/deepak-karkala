# LLM Generated Review Summaries


> **Role:** Consultant ML Engineer
>
> **Context:** Mid-sized European E-commerce marketplace (multi-country, broad product catalog, few thousand daily orders)



> 'Automated summarisation of product reviews'
>
> 'Extracted key sentiment and feature insights'
>
> 'Improved product page engagement'


##

---

### The Problem

Many products had hundreds or thousands of customer reviews — but most users don’t read them. Others had only sparse or mixed reviews. This created:

* Cognitive overload for high-traffic SKUs
* Lack of reliable insight for niche products
* Inconsistent messaging between product categories
* Heavy manual work for merchandising teams

The hypothesis was simple:

> *If we could condense review sentiment into a single, trustworthy summary, users could make decisions faster.*

---

### Solution Overview

We designed a **batch Retrieval-Augmented Generation (RAG)** system instead of real-time inference.

Pipeline steps:

1. Generate embeddings for ~4M historical reviews
2. Store embeddings in **Pinecone serverless** (pay-per-use, scalable)
3. Retrieve key review snippets (recent + helpful + sentiment-balanced)
4. Summarize with a fine-tuned **Mistral-7B** model using structured prompts
5. Run evaluation (hallucination, relevance, toxicity)
6. Store final outputs in the product catalog

---

### Evaluation & Experiment Results

We A/B-tested the feature on a subset of product pages.

What we observed:

* Users interacted more with the review section
* Scroll depth and dwell time increased
* The conversion curve showed an **uplift of ~2%**, but it was **not statistically significant**

We treated this as directional validation and focused on:

* Quality improvements
* Operational time savings
* Future UX iteration opportunities

---

### Cost & Optimization

Initial prototypes using GPT-4 API cost ~$40–50/month <!--for weekly batch inference-->.

By switching to:

* **fine-tuned Mistral-7B**
* quantization
* inference batching via **vLLM**

we reduced inference cost to **~$10–20/month**, with no quality degradation.

---

### Lessons Learned

* Summaries are only as good as retrieval signal quality
* Model evaluation needs automation, not subjective review
* Cost modeling is critical for production viability
* Experimentation must include both UX and ML metrics


---