# Product Scope Document: Mizzle Open Market

> **Status:** APPROVED (G0 Scoping Gate Passed)  
> **Version:** 1.0.0  
> **Target Release:** Phase 1 MVP  

---

## 1. Executive Summary & Problem Space

### Problem Statement
Enterprise data centers, cloud service providers (CSPs), Independent Software Vendors (ISVs), and resellers operate with severe operational friction:
1. **Unutilized Peak Compute Capacity**: Data centers keep ~30% buffer capacity idle to handle peak loads. No secure, policy-governed secondary marketplace exists to monetise excess compute safely without risking SLA breaches or data leakage.
2. **Fragmented B2B IT Procurement**: Enterprise IT buyers and resellers spend 4–8 weeks manually negotiating RFQs, verifying security postures, conducting credit checks, and setting up manual billing rails across disparate provider portals.
3. **Lack of Interoperable Open Protocol**: Traditional cloud marketplaces are walled gardens. There is no open-source, Beckn-protocol-based P2P engine that enables decentralized discovery, fulfillment, and financial clearing across heterogeneous clouds and data centers.

### Value Proposition
**Mizzle Open Market** is an open-source, Beckn-based P2P e-commerce and compute engine. It decentralizes the discovery, provisioning, resale, and financial clearing of compute capacity, ISV SaaS assets, and managed services.
- **For Buyers (CTO/CISO/SCM/Finance)**: Instant discovery, multi-vendor BoM comparison, automated RFQ workflows, DigiLocker/SumSub KYB compliance, and embedded ONDC trade finance.
- **For Sellers/Data Centers/ISVs**: Scarcity-based yield optimization, excess capacity auto-downsizing via telemetry, TEE/MPC policy enforcement, reseller whitelisting, and automated Virtual Billing Account (VBA) settlement.
- **For Ecosystem Partners & Agents**: Autonomous RPA/AI agents operating on Beckn and Model Context Protocol (MCP), third-party technical auditors, and network affiliates earning facilitation fees.

### For-Profit Sister Company Boundary
- **Open-Source Mizzle Core (This Repository)**: Beckn protocol schemas, open Provider & Consumer portals, basic workspace chat UI, standard inventory management, basic telemetry sync, and open RFQ templates.
- **Commercial Sister Company (Enterprise Extension)**: White-glove migration services, proprietary TEE/MPC key brokerage, enterprise trade credit underwriting, custom FinOps analytics (Telnium engine), and premium SLAs.

### Strategic Goals & Success Metrics

| Metric Name | Baseline | Target (Post-GA) | Measurement Window |
| :--- | :--- | :--- | :--- |
| **Peer-to-Peer Onboarding Latency** | 14 days (manual) | < 15 minutes (KYC/B + Credit) | Day 30 post-GA |
| **Excess Compute Utilization Recovery** | 0% (idle buffer) | > 22% monetized excess compute | Q2 Close |
| **Beckn Search-to-Fulfillment Time** | 3–5 days | < 60 seconds (API automated) | Day 60 post-GA |
| **Reseller Ecosystem GMV** | \$0 | \$12.5M throughput | Month 6 post-GA |

---

## 2. Boundaries & Scoping Matrix

| Capability / Module | In Scope (Open-Source Core) | Explicitly Out of Scope | Deferred to Phase 2+ |
| :--- | :--- | :--- | :--- |
| **Beckn Protocol Engine** | Beckn v1.1 search, select, init, confirm, status, cancel, track, update | Proprietary legacy non-Beckn API wrappers | Cross-chain crypto atomic swaps |
| **Excess Capacity & Secondary Market** | Telemetry auto-downsizing, CLI/API telemetry reporting, standard container provisioning | Raw physical hardware server racking | Hardware TEE enclave key brokerage (Sister Co) |
| **Workspace & Service Binding** | Service tagging, project workspace binding, simple Chat UI with read-only telemetry insights | In-chat direct resource mutation/destruction buttons | Autonomous Chat agent auto-scaler |
| **Provider Portal** | XL/API IT Inventory management, scarcity pricing logic, customer order form generator, customer task tracker | Proprietary ERP deep integration (SAP/Oracle) | Multi-entity global tax automation |
| **Consumer / Reseller Portal** | Multi-vendor comparison tool, RFQ/BoQ draft estimator, partner LMS list, support/grievance agent | Custom hardware benchmark lab hosting | Proprietary FinOps engine (Telnium engine - Sister Co) |
| **Embedded Finance & Compliance** | ONDC VBA payments integration, DigiLocker/SumSub KYB hooks, basic credit check API | Direct banking balance sheet underwriting | AI dynamic credit limit scoring |

---

## 3. Functional Requirements & User Journeys

### Epic 1: Secondary Compute Marketplace & Telemetry Auto-Downsizing
- **Objective**: Allow data centers to share excess 30% peak compute capacity safely.
- **User Flow**: Data Center registers node -> Telemetry agent monitors load -> Auto-downsizes idle allocation -> Lists compute on Beckn P2P network -> Qualified enterprise purchases slot -> TEE/MPC policy enforced.

#### Detailed Capabilities:
1. **FR-1.1: Telemetry-Driven Downsizing**
   - **Description**: The system shall consume real-time CPU/GPU/memory telemetry via CLI/API and auto-downsize reserved peak instances when utilization drops below 40% for > 15 minutes.
   - **Preconditions**: Data center seller node running Mizzle Telemetry Agent.
   - **Acceptance Criteria**:
     - *Scenario 1 (Standard Auto-Downsize)*:
       - **Given** a data center reserving 100 vCPUs with 70 vCPUs idle
       - **When** telemetry reports idle state for 15 consecutive minutes
       - **Then** system releases 50 vCPUs to the Beckn Open Compute Market tagged as "Secondary Excess Compute".
     - *Scenario 2 (Fault / Spike Recovery)*:
       - **Given** excess compute is currently rented on Secondary Market
       - **When** primary workload spikes above 85% capacity
       - **Then** system issues a Beckn `update/reclaim` signal with 300-second eviction grace period and migrates secondary workload via Migration Tool.

---

### Epic 2: Workspace Service Tagging & Simple Chat UI
- **Objective**: Bind open-source services, cloud infrastructure, and APIs to isolated project workspaces.
- **User Flow**: User logs into Consumer Portal -> Selects/Creates Organization -> Creates Project Workspace -> Tags Services -> Opens Chat UI -> Views telemetry & insight cards (read-only).

#### Detailed Capabilities:
1. **FR-2.1: Workspace Service Binding & Insights**
   - **Description**: The system shall provide a workspace listing tool allowing users to bind services by tag. The primary UI shall be a conversational Chat UI containing read-only telemetry cards (no action buttons).
   - **Acceptance Criteria**:
     - *Scenario 1 (Workspace Service Tagging)*:
       - **Given** an active workspace `Project-Alpha`
       - **When** a user applies tag `env:prod` and `service:database`
       - **Then** only resources matching both tags are populated into `Project-Alpha` workspace and API mappings.
     - *Scenario 2 (Read-Only Insight Cards in Chat UI)*:
       - **Given** user is interacting with `Project-Alpha` Chat UI
       - **When** asking "What is our current memory utilization?"
       - **Then** Chat UI renders an inline telemetry insight card showing utilization graphs without action buttons, adhering to security guidelines.

---

### Epic 3: Provider Portal & Beckn Inventory Management
- **Objective**: Equip data centers, ISVs, and resellers with open-source Beckn catalog, inventory management, and pricing controls.
- **User Flow**: Provider logs in -> Uploads inventory via Excel/API -> Applies scarcity pricing rules -> Generates Customer Order Form link -> Whitelists approved resellers.

#### Detailed Capabilities:
1. **FR-3.1: Scarcity-Based Dynamic Pricing**
   - **Description**: Provider portal shall adjust service rates dynamically based on available inventory scarcity and business targets.
   - **Acceptance Criteria**:
     - *Scenario 1 (Scarcity Trigger)*:
       - **Given** available GPU compute inventory falls below 15% threshold
       - **When** a new Beckn `search` or `select` request arrives
       - **Then** provider portal automatically applies configured +20% scarcity surcharge rate.

---

### Epic 4: Consumer/Reseller Portal, RFQ & FinOps Engine
- **Objective**: Enable SCM, Finance, CTO, and CISO personas to execute RFQs, compare specs, run FinOps estimations, and manage ONDC VBA payments.
- **User Flow**: Consumer registers (SumSub KYB) -> Creates VBA -> Enters RFQ with BoM & Tech Specs -> System runs automated bidding & scoring -> Generates comparison report -> Executes contract & payment terms.

#### Detailed Capabilities:
1. **FR-4.1: Automated RFQ & BoM Comparison**
   - **Description**: System shall ingest BoM parameters and tech specs, issue Beckn search requests, score vendor proposals against ONDC-aligned criteria, and generate a downloadable comparison report.
   - **Acceptance Criteria**:
     - *Scenario 1 (RFQ Generation & Bidding)*:
       - **Given** a CTO submits an RFQ for 500TB S3-compatible storage with SOC2 compliance
       - **When** bidding closes after configured duration
       - **Then** system scores all bids on Price, Latency, Compliance, and SLA Assurance, outputting a ranked BoQ estimation matrix.

---

## 4. Non-Functional Requirements (NFRs) & Constraints

- **Performance & Latency**:
  - Beckn protocol message processing (on_search, on_select, on_init, on_confirm) p95 < 200 ms.
  - Chat UI insight retrieval latency < 500 ms.
- **Scalability & Capacity**:
  - System architecture must support 50,000 concurrent Beckn network catalog queries per second across decentralized gateway nodes.
- **Reliability & Availability**:
  - Provider & Consumer Portal SLA: 99.95% uptime.
  - Telemetry ingestion pipeline RPO < 10 seconds, RTO < 5 minutes.
- **Security & Compliance**:
  - Data encrypted via AES-256 at rest and TLS 1.3 in transit.
  - TEE (Trusted Execution Environment) policy verification for secondary compute workloads.
  - Complete append-only audit trail for all contract signings, KYB approvals, and reseller whitelist/blacklist modifications.

---

## 5. Technical Dependencies & Architecture Touchpoints

- **Upstream Dependencies**: Beckn Protocol Core Specifications (v1.1), DigiLocker API, SumSub Verification SDK.
- **Downstream Dependencies**: ONDC Financial Ecosystem Payment Rails, Virtual Billing Account (VBA) banking gateways.
- **Third-Party Tooling / Connectors**: Open-source CRM (SuiteCRM / Twenty), Open-source LMS (Canvas / Moodle API), Zapier Webhooks, Model Context Protocol (MCP) agents.
- **Infrastructure Footprint**: Containerized Kubernetes deployment, Redis cache tier, PostgreSQL main store, ClickHouse telemetry store.

---

## 6. Assumptions, Risks & Mitigations

| Risk / Unknown | Impact (H/M/L) | Probability (H/M/L) | Mitigation Strategy |
| :--- | :---: | :---: | :--- |
| **Secondary Compute Eviction Spike** | High | Medium | Implement 300-second eviction buffer and automated Migration Tool fallback to sister company public cloud nodes. |
| **Reseller Default on Trade Credit** | High | Low | Enforce mandatory SumSub KYB, credit check threshold, and ONDC VBA lock policy before releasing service credentials. |
| **Beckn Protocol Gateway Drift** | Medium | Medium | Maintain automated protocol conformance test suite running against Beckn Sandbox daily. |
