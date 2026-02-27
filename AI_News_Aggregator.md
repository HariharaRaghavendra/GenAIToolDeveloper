AI Update Tool – Technical Architecture & System Design

Role: Chief Content Aggregator
Audience: Highly Technical AI Engineers
Governance: Fully Automated Daily
Deployment: Serverless (Free-tier-first)
Vector DB: Managed (Free-tier preferred)
Historical Retention: 90 Days

1. System Objective

Build a fully automated AI Update Tool that:

Aggregates public AI news daily (24h window)

Tracks benchmark performance across AI providers

Detects documentation changes automatically

Captures direct + early social signals

Computes hybrid Provider Performance Index

Generates quantitative executive briefing (HTML)

Produces daily technical “Tip of the Day”

Maintains 90-day historical intelligence

Provides full explainability layer

2. High-Level Architecture
                    ┌────────────────────────┐
                    │   Scheduled Trigger    │
                    │ (Daily Serverless Job) │
                    └─────────────┬──────────┘
                                  │
            ┌─────────────────────┼─────────────────────┐
            │                     │                     │
    ┌───────▼───────┐     ┌───────▼────────┐     ┌──────▼──────┐
    │ Source Ingest │     │ API Integrator │     │ Web Scraper │
    └───────┬───────┘     └───────┬────────┘     └──────┬──────┘
            │                     │                     │
            └──────────────┬──────┴──────────────┬──────┘
                           ▼                     ▼
                 ┌────────────────────────┐
                 │  Content Normalizer    │
                 └────────────┬───────────┘
                              ▼
                 ┌────────────────────────┐
                 │  Embedding Generator   │
                 │ (Single Model)         │
                 └────────────┬───────────┘
                              ▼
                 ┌────────────────────────┐
                 │ Managed Vector Store   │
                 │ (Free Tier Preferred)  │
                 └────────────┬───────────┘
                              ▼
        ┌─────────────────────────────────────────┐
        │ Intelligence & Scoring Engine           │
        │ - Credibility Weighting                 │
        │ - Benchmark Taxonomy Mapping            │
        │ - Documentation Diff Engine             │
        │ - Early Signal Classifier               │
        │ - Hybrid Performance Index              │
        │ - Momentum & Delta Engine               │
        └────────────┬────────────────────────────┘
                     ▼
        ┌─────────────────────────────────────────┐
        │ Explainability Engine                   │
        │ - Score breakdown                       │
        │ - Benchmark contribution                │
        │ - Adaptive weighting adjustments        │
        └────────────┬────────────────────────────┘
                     ▼
        ┌─────────────────────────────────────────┐
        │ Report Generator                        │
        │ - HTML Executive Briefing               │
        │ - Dashboard Tables                      │
        │ - Recent Events                         │
        │ - Tip of the Day                        │
        └─────────────────────────────────────────┘
3. Data Sources
Vector Embedded Sources

Official AI provider websites

Documentation portals

Benchmark publishing pages

Google search results

Official social media (LinkedIn, X, YouTube, Blogs)

Public developer social accounts

4. Credibility Scoring Model
Source Type	Weight
Official Website	1.0
Documentation	0.9
Benchmark Site	0.8
Official Social	0.6
Developer Social	0.5
General Search	0.3

Used in:

Signal confidence score

Conflict resolution

Performance index weighting

5. Dynamic Benchmark Taxonomy Engine
Purpose

Map equivalent benchmark metrics across providers.

Method

Embed benchmark descriptions

Cluster semantically similar metrics

Assign to canonical categories:

Reasoning

Coding

Multimodal

Efficiency

Latency

Cost Efficiency

Output

Normalized Benchmark Vector:

{
  provider: "X",
  reasoning_score: 0.82,
  coding_score: 0.91,
  multimodal_score: 0.75,
  confidence: 0.88
}
6. Documentation Change Detection
Pipeline

Daily snapshot capture

Content hashing

Structural diff

Embedding diff similarity

Change severity classification

Severity Levels

Cosmetic

Minor Technical

Major Capability

Breaking Change

Strategic Shift

7. Social Signal Engine
Signal Types
Direct Signals

Model release

Benchmark result

Infrastructure scaling

Early Signals

Hiring spike

GPU mentions

Subtle performance hints

Roadmap leaks

Each signal:

{
  type: "early",
  provider: "X",
  confidence_score: 0.61,
  impact_estimate: 0.45
}
8. Hybrid Provider Performance Index
Base Deterministic Layer

Weighted Score:

Performance Index =
  (0.60 × Benchmark Composite)
+ (0.25 × Documentation Change Impact)
+ (0.10 × Infra Signals)
+ (0.05 × Early Signals)
Adaptive AI Layer

Adjust weights dynamically based on:

Historical predictive accuracy

Signal volatility

Benchmark recency

Final Output
{
  provider: "X",
  base_score: 0.81,
  adaptive_adjustment: +0.03,
  final_index: 0.84,
  confidence: 0.89
}
9. Explainability Layer

Each ranking must show:

Benchmark contribution %

Documentation change impact %

Early signal adjustment %

Credibility weighting applied

Day-over-Day delta

30-day momentum trend

10. Historical Storage (90 Days)
Stored Data

Raw ingested content

Embeddings

Benchmark normalized vectors

Daily performance index

Documentation diffs

Signal metadata

Supports:

7-day, 30-day, 90-day momentum

Volatility tracking

Stability index

11. Daily HTML Executive Briefing Structure
Section 1: Dashboard

Ranking Table

Performance Index

Momentum Score

Confidence Score

Section 2: Top Events (Last 24h)

Each entry:

Headline

Summary

Credibility Score

Reference Link

Section 3: Documentation Changes

Provider

Change Type

Severity

Impact on Ranking

Section 4: Early Signals

Provider

Signal Type

Confidence

Section 5: Tip of the Day

Generated from:

Significant benchmark shifts

Major documentation updates

Example:

“Provider X’s reasoning benchmark improved 4.3% following parameter update in v3.2. Consider re-evaluating task allocation if using reasoning-heavy workloads.”

12. Serverless Deployment Model
Components

Scheduled Function (Daily Trigger)

Stateless Processing Functions

Managed Vector DB (Free Tier)

Object Storage (Historical Snapshots)

Lightweight Metadata DB (Structured Scores)

Design Constraints

Free-tier optimized

Stateless compute

Deterministic execution

Observability logging

13. Copilot Agent Phased Execution Prompt Design
Phase 1 – Data Ingestion

"Collect last 24 hours updates from registered providers. Apply credibility scoring."

Phase 2 – Normalization

"Map benchmarks to canonical taxonomy and normalize metrics."

Phase 3 – Diff Detection

"Compare documentation snapshots and classify change severity."

Phase 4 – Signal Extraction

"Classify social signals into Direct or Early."

Phase 5 – Scoring Engine

"Compute base index, apply adaptive adjustment, generate confidence score."

Phase 6 – Explainability

"Break down score contributions and rank providers."

Phase 7 – Report Generation

"Generate structured HTML executive briefing with dashboards and references."

Phase 8 – Archival

"Store embeddings, metrics, signals, and performance index for 90-day retention."

14. Risk Controls

Anomaly detection for abnormal benchmark jumps

Outlier suppression

Duplicate clustering thresholding

Confidence gating (low confidence signals do not affect index heavily)

Source reliability decay model

15. Output Guarantees

The system guarantees:

No hallucinated metrics

All news traceable to reference links

Quantified ranking logic

Fully automated daily publishing

Explainable scoring

15. Confirmed Technology Stack

Core Language

Python

Cloud Platform

Azure (Serverless-first)

Serverless & Orchestration

Azure Functions (Python runtime)

Azure Durable Functions (Orchestrator pattern)

Timer Trigger (daily execution)

Vector Database

Pinecone (Free Tier)

Namespaces:

provider

date

source_type

Metadata filtering enabled

Structured Metadata Database

Azure Cosmos DB (NoSQL)

Stores:

Performance index

Benchmark normalized scores

Diff metadata

Signal metadata

Explainability breakdown

Historical daily snapshots

Embedding & LLM Layer

Azure OpenAI

Single embedding model

Same deployment for reasoning + summarization

Used for:

Embeddings

Adaptive scoring

Explainability generation

Tip of the Day

Scraping Stack

Hybrid:

requests + BeautifulSoup → static pages

Playwright → JS-heavy portals

HTML Report Generation

Jinja2 templating engine

Chart.js for interactive dashboards

Fully static HTML output

Dashboard features:

Ranking tables

Momentum graphs

Benchmark comparison charts

Confidence indicators

Secrets Management

Hybrid:

Azure Key Vault → Production

Environment variables → Local development

Managed Identity for Key Vault access

16. Orchestrated Pipeline (Durable Function Flow)

Orchestrator Phases

Phase 1 – Source Ingestion

Collect official sites

Collect documentation

Collect benchmark sites

Collect social posts

Apply credibility scoring

Phase 2 – Normalization

Clean content

Standardize structure

Attach metadata

Phase 3 – Embedding

Generate embedding via Azure OpenAI

Store in Pinecone with metadata

Phase 4 – Documentation Diff Engine

Compare current snapshot vs previous

Structural diff

Embedding similarity diff

Classify severity

Phase 5 – Dynamic Benchmark Taxonomy

Cluster semantically similar benchmark metrics

Map to canonical categories:

Reasoning

Coding

Multimodal

Latency

Cost efficiency

Normalize across providers

Phase 6 – Social Signal Classification

Classify:

Direct signal

Early signal

Assign:

Confidence score

Impact estimate

Phase 7 – Hybrid Performance Index Calculation

Base Formula:

Performance Index =
(0.60 × Benchmark Composite)

(0.25 × Documentation Impact)

(0.10 × Infra Signals)

(0.05 × Early Signals)

Adaptive Layer:

AI adjusts weights based on:

Signal volatility

Historical predictive alignment

Confidence weighting

Final Output:

base_score

adaptive_adjustment

final_index

confidence_score

Phase 8 – Explainability Engine

For each provider:

% contribution per category

Documentation impact breakdown

Early signal adjustment breakdown

Credibility weighting applied

Day-over-Day delta

30-day momentum

Phase 9 – Report Generation

HTML Executive Briefing Structure:

Dashboard Overview

Ranking Table

Performance Index

Momentum Score

Confidence Score

Top Events (Last 24h)

Headline

Summary

Credibility Score

Reference link

Documentation Changes

Provider

Severity

Impact on ranking

Early Signals

Provider

Type

Confidence

Technical Tip of the Day

Derived only from:

Benchmark shifts

Documentation changes

Phase 10 – Archival (90 Days)

Store:

Raw content

Embeddings

Scores

Diff results

Signal metadata

Retention:

90-day TTL policy

Optional cold archival later