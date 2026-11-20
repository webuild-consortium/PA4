# MVP PA4 Scenario 2 Tracking

**Purpose:** Central entry point for PA4 Scenario 2 MVP onboarding, partner and scenario documentation, registration, and results tracking.

**Status:** Work in progress (WIP). Document paths, partner assignments, and scenario requirements must be confirmed before publication.

## 1. Reference documents

| Document                                                                                           | Purpose                                                                                                                            | Status |
|----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|---|
| [tracking.md](wp4/tracking.md)                                                                     | Explains the WP4 MVP tracking methodology, responsibilities, and progress reporting.                                               | WIP |
| [onboarding.md](wp4/readme.md)                                                                     | Generic onboarding guidance: wallet setup, ITB onboarding, conformance testing, trust registration, and prerequisite provisioning. | WIP |
| [MVP_PA4_Scenario2_Template_Partnername_Roles.md](MVP_BU1_Scenario1_Template_Partnername_Roles.md) | Template for recording PA4 partner roles, requirements, progress, evidence, and test results.           | Final (source-reported; file path to verify) |

## 2. How to get started

### A. Onboard and prepare the wallets

1. Read the [onboarding.md](wp4/readme.md)
2. Review the PA4-specific conformance requirements once the canonical BU1 specification is confirmed.
3. Identify participating partners and confirm their business and technical roles (for example, Buyer / Verifier or Supplier / Holder / Issuer).
4. Initialize and configure the required wallets in accordance with the generic onboarding guidance and the BU1 scenario requirements.
5. Use the partner tracker to record applicable test cases, status, dates, evidence, and open issues. Example test cases are not automatically mandatory for BU1.

### B. Create and document the MVP

1. Copy the [PA4 partner tracker template](MVP_PA4_Scenario2_Template_Partnername_Roles.md).
2. Rename the copy to identify the use case, partner, business role, and technical role(s); use the naming convention shown in the results table below.
3. Record the scenario scope, contacts, wallet implementations, applicable prerequisites, conformance requirements, and current status.
4. Record interoperability test runs, outcomes, evidence links, defects, retests, and sign-off in the partner tracker.
5. Clearly identify unconfirmed requirements and missing evidence. Do not treat reported completion as independently verified without supporting evidence.

### C. Register the new MVP

1. Add the partner tracker to the results table below and to the relevant project index.
2. Link the tracker to the associated PA4 scenario and other participating partners, where applicable.
3. Record the responsible owner, last update, and acceptance status. Keep these fields current as testing progresses.

## 3. Results tracking

The entries below reproduce the partner/role combinations supplied in the source. **No actual test completion or acceptance status has been established by this index.** Confirm the filenames and links in the target repository.

| Company        | Business role | Technical role(s) | Partner tracker                                                               | Current status |
|----------------|---------------|-------------------|-------------------------------------------------------------------------------|---|
| Bosch          | Buyer         | Verifier          | [MVP_PA4_Bosch_Buyer+Verifier.md](MVP_BU1_Bosch_Buyer+Verifier.md)            | To confirm |
| SBB            | Seller        | Holder + Issuer   | [MVP_PA4_SBB_Supplier+Holder+Issuer.md](MVP_BU1_SBB_Supplier+Holder+Issuer.md) | To confirm |
| Freelancer(DE) | Seller        | Holder + Issuer   | [MVP_PA4_Freelance+Holder+Issuer.md](MVP_BU1_Bosch_Supplier+Holder+Issuer.md) | To confirm |
