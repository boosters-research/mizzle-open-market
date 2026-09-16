# Customer Pain Index (CPI) Evidence Ledger — Mizzle Open Market

**Run ID:** `mizzle-open-market-v1`  
**Formula:** $$\text{CPI} = \text{round}\left(\frac{\text{Frequency} \times \text{Severity} \times (6 - \text{Workaround Quality}) \times \text{WTP Signal}}{7.5}, 1\right)$$  
*(Scores range from 0 to 100)*

---

## CPI Scoring Matrix

| Feature / Module | Persona | Frequency (1-5) | Severity (1-5) | Workaround Quality (1-5) | WTP Signal (1-5) | CPI Score (0-100) | Priority Rank | Key Pain / Rationale |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **Secondary Excess Compute Marketplace & Telemetry Downsizing** | Data Center Operator / CTO | 5 | 5 | 2 | 5 | **66.7** | P0 (Rank 1) | Data centers idle 30%+ compute for peak capacity; zero liquidity for excess compute without automated telemetry auto-downsizing and TEE security. |
| **Beckn Open Provider & Consumer Engine** | SCM / ISV Reseller | 5 | 4 | 2 | 4 | **53.3** | P0 (Rank 2) | High cost of custom B2B e-commerce integrations; lack of decentralized protocol standards for enterprise cloud service trade. |
| **ONDC Embedded Finance & Trade Credit Rails** | Finance / SCM | 4 | 5 | 2 | 4 | **53.3** | P0 (Rank 3) | 60-90 day enterprise payment terms create liquidity bottlenecks; lack of automated VBA payment settlement and trade credit underwriting. |
| **Multi-Vendor RFQ, BoM & Architecture Comparison Engine** | CTO / CISO / SCM | 4 | 4 | 2 | 4 | **42.7** | P1 (Rank 4) | Complex cloud RFQ processes take weeks; comparing specs across vendors and architectures requires expensive manual consulting. |
| **Workspace Service Tagging & Chat UI** | CTO / Dev Lead | 5 | 3 | 3 | 3 | **30.0** | P1 (Rank 5) | Fragmented service visibility across projects; manual binding of APIs/microservices to project workspaces. |
| **KYC/KYB, DigiLocker & SumSub Verified Supplier Badge** | CISO / Compliance | 3 | 4 | 2 | 4 | **32.0** | P1 (Rank 6) | Vendor onboarding delays due to manual legal & compliance verification; lack of cross-participant verified supplier credentials. |
| **Scarcity-Based Pricing & Inventory Engine** | Reseller / Seller | 4 | 3 | 3 | 4 | **28.8** | P2 (Rank 7) | Rigid pricing models prevent data centers from dynamic yield management during demand spikes or idle periods. |
| **FinOps Integrations (Telnium, Cloudability, CSP Connect)** | Finance / FinOps Lead | 4 | 4 | 3 | 3 | **25.6** | P2 (Rank 8) | Cloud cost opacity across hybrid/multi-cloud deployments; lack of unified BoQ total cost of ownership forecasting. |
| **AI Learning & Certification LMS Engine** | Reseller / Developer | 3 | 3 | 3 | 3 | **14.4** | P3 (Rank 9) | Partner enablement slow; manual certification for complex cloud service architectures. |

---

## Evidence Ledger Details

- **E-MKT-001 (Compute Utilization)**: Data centers operate at an average 35–45% unutilized capacity reserved for peak loads. Current workarounds (manual spot instance auctions) lack enterprise SLAs or TEE policy enforcement.
- **E-MKT-002 (B2B E-Commerce Standards)**: Enterprise IT procurement relies on heavy custom portals. Beckn protocol enables open, interoperable discovery and transaction across disparate provider portals.
- **E-MKT-003 (Trade Credit Liquidity)**: SMB data centers and ISV resellers suffer 90-day DSO (Days Sales Outstanding). ONDC financial ecosystem integration provides instant liquidity via Virtual Billing Accounts (VBA) and supply chain finance.
- **E-MKT-004 (RFQ Complexity)**: Enterprise cloud RFQs take 3–6 weeks to build BoMs, verify security posture, and negotiate private pricing offers.
