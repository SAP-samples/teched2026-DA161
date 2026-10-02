# Getting Started — Data Product Creation Agent

## What is the Data Product Creation Agent?

The Data Product Creation Agent (DPCA) is an AI agent in Joule Studio that takes a natural-language business requirement and produces a fully governed, inspectable data product definition — without requiring you to write SQL, design a schema by hand, or configure authorization policies manually.

The agent searches your landscape for relevant source data, surfaces gaps and trade-offs for you to decide, and generates the complete technical definition once you have reviewed and approved each stage.

## Key Concepts

The agent works through four stages. You review and approve each one before it proceeds to the next.

| Stage | What it produces |
|---|---|
| **Intent** | The agent's structured interpretation of your business requirement |
| **Requirements** | Personas, must-have criteria, and explicit scope boundaries |
| **Specification** | The build plan translated into technical steps |
| **Solution** | The generated, inspectable data product definition (CDS, YAML) |

## What You Will Build

**Exercise 1 — Supplier Concentration Risk by Country**

A derived data product that joins Purchase Order and Supplier master data to help procurement teams identify supplier concentration risk by country. You will see the agent discover a real data gap — a missing supplier-country field — and guide you through resolving it.

**Exercise 2 — Active Cost Centers for India**

A derived data product for non-blocked cost centers filtered to India, with validity dates exposed for consumer-side date filtering. An optional extension (Exercise 3) adds planned budget amounts from a second source.

## How to Use These Exercises

Follow the facilitator's pace. Each step tells you exactly what to click or paste — paste-text blocks contain the exact prompts to enter in the Joule conversation panel.

At the end of each step, a **✓ Checkpoint** tells you what you should see on screen before moving on. If your screen looks different, ask a workshop assistant before continuing.

> **Important:** Do not click **Deploy** at any point during this session. Deployment is the next stage of the roadmap and is not demonstrated today.

---

Continue to [Exercise 1 — Supplier Concentration Risk by Country](../ex1/README.md)
