# Roadmap & Implementation Plan: Mizzle Open Market

> **Run ID:** `mizzle-open-market-v1`  
> **Status:** APPROVED (G5 Roadmap Gate Passed)  

---

## 1. Phased Execution Roadmap (CPI Prioritised)

The roadmap is strictly ordered by Customer Pain Index (CPI) score to ensure maximum value delivery at each milestone.

```
┌───────────────────────────────────────────────────────────────────────────┐
│                           IMPLEMENTATION PHASES                           │
├───────────────────┬───────────────────────┬───────────────────────────────┤
│ Phase 0: Spike    │ Phase 1: MVP          │ Phase 2: GA & Hardening       │
│ (Weeks 1 – 4)     │ (Weeks 5 – 14)        │ (Weeks 15 – 24)               │
│ • Beckn Gateway   │ • Secondary Compute   │ • ONDC Embedded Finance       │
│ • Workspace Chat  │   Marketplace         │ • TEE/MPC Policy Guard        │
│ • Tagging Engine  │ • Provider Portal     │ • Partner Program & LMS       │
│                   │ • Consumer Portal RFQ │ • Custom Migration Service    │
└───────────────────┴───────────────────────┴───────────────────────────────┘
```

---

## Phase 0: Foundation Spike & Protocol Gateway (Weeks 1–4)
* **Goal**: Validate Beckn Protocol BAP/BPP gateway communication and Workspace Chat UI prototype.
* **Core Deliverables**:
  - Beckn v1.1 protocol schema definitions for compute & ISV services.
  - Workspace tagging system (`service:tag` to project workspace binding).
  - React/Vite Chat UI prototype with read-only telemetry insight components.
* **CPI Covered**: Core Beckn Engine (CPI 53.3), Workspace Chat (CPI 30.0).

---

## Phase 1: MVP — Secondary Compute & Portals (Weeks 5–14)
* **Goal**: Enable data centers to monetize 30% excess peak compute and launch Provider/Consumer Portals.
* **Core Deliverables**:
  - Telemetry agent for CLI/API monitoring and automated 15-min idle downsizing.
  - Secondary Reserved Instance Marketplace with 300s eviction grace period.
  - Provider Portal: XL/API IT inventory upload, scarcity pricing engine, customer order form generator link, reseller whitelist/blacklist.
  - Consumer/Reseller Portal: SumSub/DigiLocker KYB integration, Verified Supplier badge issuer, RFQ generator with BoM comparison reports.
  - My Customers task tracking table (Account, Billing FOCUS, Service, Support filters).
* **CPI Covered**: Secondary Compute (CPI 66.7), RFQ Engine (CPI 42.7), Verified Supplier (CPI 32.0), Scarcity Pricing (CPI 28.8).

---

## Phase 2: GA — Embedded Finance, TEE & Ecosystem Expansion (Weeks 15–24)
* **Goal**: Full commercial launch with ONDC trade credit rails, TEE confidential enclaves, and partner ecosystem.
* **Core Deliverables**:
  - ONDC Financial Ecosystem integration (Virtual Billing Account / VBA payments policy, trade credit underwriting).
  - TEE / MPC enclave execution policy engine (Apache Teaclave integration).
  - FinOps analytics connectors (Telnium engine, Cloudability, CSP Connect).
  - Open-source LMS + AI Chat learning & certification environment with points/rewards.
  - Open-source CRM integration (SuiteCRM / Twenty) for Partner Program management.
* **CPI Covered**: ONDC Trade Finance (CPI 53.3), FinOps Integrations (CPI 25.6), Partner LMS (CPI 14.4).

---

## 2. P50, P80 & Downside Timeline Estimates

| Milestone Phase | P50 (Target Days) | P80 (Confidence Days) | Downside Risk (Days) | Key Risk Factor |
| :--- | :---: | :---: | :---: | :--- |
| **Phase 0: Spike** | 28 days | 35 days | 45 days | Beckn protocol schema validation edge cases. |
| **Phase 1: MVP** | 70 days | 84 days | 105 days | Telemetry downsizing eviction grace handling in heterogeneous DCs. |
| **Phase 2: GA** | 140 days | 168 days | 210 days | ONDC VBA banking gateway certification lead times. |

---

## 3. Pre-Scheduled Decision Gates & Exit Criteria

```
  ┌─────────────┐       ┌─────────────┐       ┌─────────────┐
  │   Gate 1:   │  ──►  │   Gate 2:   │  ──►  │   Gate 3:   │
  │ Spike Exit  │       │  MVP Release│       │ GA Hardening│
  └─────────────┘       └─────────────┘       └─────────────┘
```

- **Gate 1 (Week 4)**: 100% Beckn Sandbox compliance test suite pass + Chat UI read-only card rendering verified.
- **Gate 2 (Week 14)**: Automated telemetry downsizing tested across 3 sample data center nodes without workload SLA violation + 10 verified reseller signups.
- **Gate 3 (Week 24)**: ONDC VBA payment settlement end-to-end sandbox pass + SOC2 Type II audit readiness review.
