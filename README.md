# Awesome-Global-Tax-Payment-Compliance

## Top Global Tax & Payment Compliance Ecosystem

**Curated List of SaaS Platforms & Open-Source GitHub Projects**  
*Focused on Tax Calculation Engines, Nexus Determination & Self-Hosted Compliance Primitives*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Global Tax & Payment Compliance**. These tools help businesses calculate, collect, and remit indirect taxes—sales tax, VAT, and GST—across jurisdictions, covering everything from commercial tax engines like Avalara and Vertex to open-source calculation primitives and nexus-determination libraries that handle the core logic without per-transaction fees.

**Examples** include Avalara AvaTax, Vertex Cloud, Anrok, TaxJar, Stripe Tax, and open-source alternatives like NexusTax and Laravel Nexus (the category leaders).

**Open-source emphasis**: This section highlights every major active project for self-hosted tax calculation, open-source nexus engines, and community-driven compliance primitives—ideal for developers seeking data sovereignty and avoiding per-transaction SaaS pricing that compounds with sales volume. The open-source landscape is genuinely nascent but functional: **NexusTax** provides a framework-agnostic tax calculation engine with reverse charge, partial exemptions, and place-of-supply rules [citation:13], **Cbox Nexus** delivers US economic-nexus determination for Laravel , and **Open-Invoice** bundles a pluggable multi-jurisdiction tax engine into a local-first invoicing tool [citation:6].

Contributions welcome! Open an PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [Sector Overview & Market Dynamics](#sector-overview--market-dynamics)
- [SaaS/Hosted Platforms](#saas-products)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## Sector Overview & Market Dynamics

The global tax compliance and management software market is estimated at approximately **$23 billion to $29 billion in 2026** (projected to reach over $50 billion by the mid-2030s at an ~11% CAGR). The sector is **moderately fragmented** due to disparate jurisdiction-specific rules, local e-invoicing mandates, and varying tax structures across countries; however, enterprise indirect tax calculation and filing remain heavily concentrated among a handful of multi-billion-dollar scale leaders (e.g., Stripe, Avalara, Vertex).

## SaaS/Hosted Platforms

| Product | Company Size (Valuation / Revenue) | Description | Pricing (Starting) | Free Tier / Trial Limits |
|---|---|---|---|---|
| **[Stripe Tax](https://stripe.com/tax)** | **$159B valuation** (~$6.8B net revenue) | Tax calculation and filing integrated directly into Stripe's payment platform. Supports sales tax, VAT, and GST across 100+ jurisdictions. | **0.5% per transaction** (no-code / Stripe Checkout) or **$0.50 per transaction** (Tax API); full compliance suite from **$90/month** | **No free tier or trial** (live production requires active paid transaction fees; testmode available for developers) |
| **[Avalara AvaTax](https://www.avalara.com/)** | **$8.4B valuation** at buyout (~$789M revenue) | **The enterprise standard for indirect tax calculation.** Real-time rate determination, exemption certificate management, and return filing across thousands of jurisdictions. Positioned for businesses with complex multi-state and international nexus. | Starts at **$69/month** (or **$699/year**) per state (Streamlined Sales Tax) / **$79/month** per state (non-SST); enterprise tiers require custom quote | **90-day free trial** for AvaTax evaluation/testing (capped at 5 orders/invoices per min, max 1,000 transactions/day; no permanent free tier) |
| **[Vertex Cloud](https://www.vertexinc.com/)** | **$2.9B market cap** (~$819M LTM revenue) | Enterprise tax technology for sales and use tax, VAT, and compliance. Deep ERP integrations (SAP, Oracle, Microsoft Dynamics). | Entry packages start from **$5,000/year** (mid-market median ~$33,000/year; custom quote based on revenue/volume) | **No free tier or trial** (enterprise evaluation via sales demo only) |
| **[TaxJar](https://www.taxjar.com/)** | **$850M–$900M valuation** (acquired by Stripe) | Sales tax automation with API, automated filing, and nexus tracking. Widely used by e-commerce and SaaS businesses. | Starts at **$39/month** (Starter Plan for up to 200 orders/month and 2 auto-filings/year) | **30-day free trial** (access to calculation and reporting features without auto-file) |
| **[Anrok](https://www.anrok.com/)** | **$250M valuation** (Series B, 2024) | **API-first sales tax and VAT compliance for SaaS and digital businesses.** Monitors nexus thresholds, calculates tax, and files returns. Positioned for software companies with global customers. | Starts at **$100/month per active market** (state/country) | **No free tier or public trial** (pre-sale sandbox evaluation available on request) |

## Open-Source GitHub Projects

| Project | Star Badge | Description |
|---------|------------|-------------|
| **[NexusTax](https://github.com/azaharizaman/nexus-tax)** | [![Stars](https://img.shields.io/github/stars/azaharizaman/nexus-tax?style=social&color=white)](https://github.com/azaharizaman/nexus-tax/stargazers) | **The most complete open-source tax calculation engine for multi-jurisdiction compliance.** **Framework-agnostic PHP library** with **stateless calculation engine** architecture [citation:13]. **Core capabilities**: multi-jurisdiction support with temporal rate resolution, **hierarchical compound taxes** (tax-on-tax), **reverse charge mechanism** for EU B2B cross-border transactions, **partial exemptions** (e.g., 50% exempt for agricultural cooperatives), **economic nexus determination**, and **place-of-supply rules** for cross-border services [citation:2][citation:13]. **Immutable audit log** via contra-transaction pattern—no UPDATE or DELETE permitted, adjustments create new records with negative amounts [citation:13]. **Best for teams building custom billing systems** needing a rigorous, auditable tax engine without per-transaction fees. |
| **[Cbox Nexus (Laravel)](https://github.com/cboxdk/laravel-nexus)** | [![Stars](https://img.shields.io/github/stars/cboxdk/laravel-nexus?style=social&color=white)](https://github.com/cboxdk/laravel-nexus/stargazers) | **The US economic-nexus engine for Laravel—UI-free primitives, not a finished app.** Accumulates a seller's sales per state, detects when **post-Wayfair thresholds** are crossed, and reports where registration is required [citation:7]. **Decision logic**: below / approaching / triggered / registered per state. **Thresholds ship from the `us-tax-data` dataset** with each state's measurement period and sales basis; you bind your own billing data for the rest. **Never infers nexus from a single invoice**—economic nexus turns on cumulative totals over a measuring period . **MIT licensed**. **Best for Laravel teams** needing to answer "do we need to register in this state?" without a commercial nexus-monitoring service. |
| **[Open-Invoice](https://www.npmjs.com/package/@rsl-innovation/open-invoice)** | — | **Local-first, agent-native invoicing with a pluggable multi-jurisdiction tax engine.** **One SQLite file you own**—no account, no sync, no network calls. **Tax is a first-class domain**: a rules engine resolves jurisdiction, place of supply, and registration status into named tax components. **India GST's CGST/SGST-vs-IGST split is expressed as data**, not special-case code—EU VAT reverse-charge and US sales tax are packs, not rewrites [citation:6]. **MCP daemon** exposes operations to AI agents (Claude, ChatGPT) with **fenced permissions**—agents can draft invoices but cannot issue, void, or delete unless explicitly allowed [citation:6]. **Status: v1, early**—254 tests passing, verified end-to-end on macOS; Linux/Windows untested [citation:6]. **Best for developers wanting invoicing + tax logic in one local-first package** with AI-agent integration. |
| **[Eisphora](https://github.com/OrionUnix/Eisphora)** | [citation:14] | **Privacy-first crypto tax calculator with a stateless security model.** **Django-based**, processes CSV files **entirely in-memory**—no database, no disk persistence, no user accounts required [citation:14]. **Zero-disk policy**: memory is wiped after FIFO calculations render results. **BSD-3-Clause licensed**—business-friendly for commercial forks. **Currently focused on French taxation**, with plans for US and Luxembourg. **SaaS Mode** available for forkers wanting to add accounts and PostgreSQL persistence with AES-256 encryption [citation:14]. **Best for crypto traders wanting a privacy-respecting tax estimator** without handing financial history to a SaaS honeypot. |

### Additional Strong Open-Source Options

| Project | Star Badge | Description |
|---------|------------|-------------|
| **[OpenAccountants MCP](https://github.com/openaccountants/openaccountants)** | — | **MCP server giving AI assistants on-demand access to open-source accounting skills across 180+ countries, 51 US states, and 13 Canadian provinces.** Covers **tax, bookkeeping, payroll, e-invoicing, formation, cross-border (Pillar Two, CBAM, FATCA/CRS, DST)**, and sector verticals [citation:4]. **AGPL-3.0**. **Best as an AI-accessible knowledge layer** for tax rules—not a calculation engine itself, but a way to ground AI assistants in jurisdiction-specific guidance [citation:10]. |
| **[vat-rates](https://github.com/kdeldycke/vat-rates)** | — | **Database of VAT rates for digital, cloud, and electronic services by country.** Pure rate data with no calculation logic—last updated September 2025 [citation:10]. **Best as a reference dataset** for EU VAT rates, not a complete tax engine. |
| **[valvat](https://github.com/yolk/valvat)** | — | **Ruby library for validating European VAT numbers** standalone or as an ActiveModel validator [citation:10]. **Building block, not a tax tool**—checks buyers' tax IDs but calculates no tax. |

**Frameworks for building custom systems**: Choose **NexusTax** for a rigorous multi-jurisdiction calculation engine with reverse charge and audit logging [citation:13], **Cbox Nexus** for US nexus determination in Laravel , or **Open-Invoice** for local-first invoicing with a pluggable tax engine and MCP agent access [citation:6]—all without per-transaction SaaS fees that compound with sales volume.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Tax compliance software handles financial data and regulatory obligations; **always verify calculations against official tax authority guidance** and consult qualified tax professionals. Open-source tools provide calculation primitives, not filing services—**none of the open-source projects identified registers for permits, files returns, or remits tax** [citation:10].
- **Open-source tax tooling is genuinely primitive compared to commercial platforms.** **NexusTax is the most complete calculation engine** with reverse charge, exemptions, and audit logging [citation:13], but it is a PHP library requiring integration—not a turnkey compliance solution. **Cbox Nexus solves only US economic nexus**—a single piece of the puzzle . **Open-Invoice bundles tax logic into invoicing** but is explicitly **v1/early** with Linux/Windows untested [citation:6]. **Eisphora is crypto-tax-specific** and currently French-only [citation:14]. **The commercial landscape is entirely proprietary**—a 2026 survey of 108 tax compliance tools found **zero open-source entries** [citation:5]. **Avalara and Vertex are enterprise quote-only**; Anrok, TaxJar, and Stripe Tax offer API-based calculation but charge per-transaction or monthly fees. **Validate whether you need a commercial engine for filing and remittance (Avalara, TaxJar), an open-source calculation primitive for custom billing (NexusTax), or a nexus-monitoring library (Cbox Nexus)** before committing.

---

**Made for finance engineers, billing developers, and organizations building tax compliance infrastructure.**  
Let's make global tax and payment compliance more open, auditable, and calculation-first.
