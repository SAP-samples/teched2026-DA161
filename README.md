# DA161 — Develop and Create Data Products in Joule Studio

## Description

This session introduces attendees to the Data Product Creation Agent (DPCA) in Joule Studio — an AI agent that turns a natural-language business requirement into a fully governed, inspectable data product definition. No manual SQL or schema design is required.

You will build two derived data products from scratch, guided step by step through the full agent flow: Intent → Requirements → Specification → Solution.

## Learning Objectives
By the end of this session, attendees will be able to:
- Describe the end-to-end Data Product Creation Agent flow: Intent → Requirements → Specification → Solution.
- Create a derived data product from a natural-language business requirement, without writing SQL or a schema by hand.
- Recognize how the agent handles a genuine data gap — asking for a decision instead of guessing.
- Explain how personal data and authorization are handled automatically as part of data product creation.
- Identify what's in scope today (creation and inspection) versus what's on the roadmap (testing and deployment).


## Requirements

- A [provisioned Joule Studio](https://747391938.eu10.sapdas.cloud.sap/new/) tenant and working login (provided for workshop attendees)
- No prior experience with SQL, CDS, or data modelling is required

## Exercises

- [Getting Started — Introduction to the Data Product Creation Agent](exercises/ex0/)
- [Exercise 1 — Supplier Concentration Risk by Country](exercises/ex1/)
- [Exercise 2 — Active Cost Centers for India](exercises/ex2/)
- [Exercise 3 — Planned Budget Extension *(optional)*](exercises/ex3/)

## Recap
- Natural language in, governed data product out — no manual schema design required to get started.
- The agent grounds every recommendation in what actually exists in your landscape — it doesn't guess.
- When the data doesn't have what's needed, the agent surfaces the gap and lets you decide — it doesn't silently work around it.
- Personal data and authorization are handled deliberately, not as an afterthought.
- Everything generated is inspectable — as a business document (PRD) and as code (CDS, YAML).
- Today's session covered creation and review. Testing and deployment are the next stage of the roadmap.

## Contributing

Please read the [CONTRIBUTING.md](./CONTRIBUTING.md) to understand the contribution guidelines.

## Code of Conduct

Please read the [SAP Open Source Code of Conduct][code-of-conduct].

## How to obtain support

Support for the content in this repository is available during the actual time of the online session for which this content has been designed. Otherwise, you may request support via the [Issues](../../issues) tab.

## License

Copyright (2026) SAP SE or an SAP affiliate company and teched2026-DA161 contributors. Please see our [LICENSE](LICENSE) for copyright and license information. Detailed information including third-party components and their licensing/copyright information is available [via the REUSE tool][reuse-tool].

[code-of-conduct]: https://github.com/SAP-samples/.github/blob/main/CODE_OF_CONDUCT.md
[reuse-tool]: https://api.reuse.software/info/github.com/SAP-samples/teched2026-DA161
