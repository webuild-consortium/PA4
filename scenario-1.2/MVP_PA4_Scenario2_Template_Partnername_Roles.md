# MVP BU1 Scenario 1 – Scenario Tracker Baseline

**Purpose:** Use-case-lead working baseline for BU1 Scenario 1 scenarios. Copy and approve scenario-specific requirements before creating a partner/technical-role tracker. Based on `WP4_Tracker_TEMPLATE.md`

**Approval:** ❔ Not approved · **Progress:** No partner execution evidence was supplied. All execution statuses are ⚪ Not started; applicability and proposed test cases remain ❔ To confirm.

**Status legend:** ⚪ Not started · 🟡 In progress · ✅ Done · 🔴 Blocked · ➖ N/A (with reason) · ❔ To confirm. **Test outcomes:** Not run / Pass / Fail / Blocked / Retest pending.

## 1. Scenario baseline profile
| Field           | Baseline value                 |
|-----------------|--------------------------------|
| Use case        | PA4                            |
| Scenario scope  | Scenarios 4                    |
| Partner         | Business Partner Name          |
| Contact         | Business Contact person        |
| Business roles  | Seller or Buyer                |
| Technical roles | Holder+Issuer or Verifier (RP) |
| Baseline        | baseline                       |
| Last update d   | date                           |

**Copy rule:** For each partner, instantiate `MVP_BU1 Scenario 1-S<Scenario>_<Partner>_<BusinessRole>_<TechnicalRole>.md` for each actual partner/role combination. Retain N/A items with a justification; duplicate per-wallet and per-attestation items as needed.

## 2. Wallet inventory and proposed roles

## Wallet inventory and proposed roles
| Wallet   | Wallet type / purpose                                            | MVP or MVP+ | Provider / version                               | Scenario / partner / role | Required? | Status | Evidence |
|----------|------------------------------------------------------------------|-------------|--------------------------------------------------|---|---|---|---|
| EBW      | EBW for legal-entity workflows (can be cloud or mobile solution) | MVP         | Spherity,Procivis, Telekom -Wallet, Sphereon.... | TBD | ❔ | ⚪ | |
| EUDI     | EUDI Wallet for legal representative to obtain EBWOID& & EUCC    | MVP         | Procivis,Credenco, D-You Wallet, ...             | TBD | ❔ | ⚪ | |

*Source note:** The supplied BU1 Scenario 1 file proposes these wallet/persona combinations; whether separate physical wallet instances are needed and which scenarios require them must be confirmed. The generic template requires a separate row per distinct implementation.

## Stage 1 – Role identification
| ID   | Requirement                                                        | Status | Evidence / decision |
|------|--------------------------------------------------------------------|--------|---------------------|
| 1.1  | Business role per PA3 scenario and partner clarified               | ⚪      |                     |
| 1.2  | Technical role(s): Holder, Verifier/RP, Issuer, or combination     | ⚪      |                     |
| 1.3  | Confirm MVP versus MVP+ scope and required natural-person personas | ⚪      |                     |
| 1.4  | Approve wallet-to-role mapping and partner contacts                | ⚪      |                     |

## Stage 2 – Wallet initialization and deployment
| ID  | Wallet | Requirement                                                                      | Status | Date | Evidence |
|-----|--------|----------------------------------------------------------------------------------|--------|------|----------|
| 2.1 | EBW    | Install/configure wallet, record provider/version and verify reachability (MVP)  |  ⚪     |      |          |
| 2.2 | EUDI   | Install/configure wallet, record provider/version and verify reachability (MVP)  | ⚪      |      |          |

## Stage 3 – ITB onboarding
| ID    | Requirement                                         | Status | Date | Evidence |
|-------|-----------------------------------------------------|--------|---|---|
| 3.1   | ITB portal account activated                        | ⚪      | | |
| 3.2   | Join `#wp4-testing` and review WP4 testing guidance |  ⚪     | | |

## Stage 4 – ITB Basic Conformance
The PA3 source lists `VCI-006` and `VP-001` for EBW and EUDI Wallets. These are **candidate PA3 test cases, not confirmed requirements**. A second source gives `VP-011` and `VP-013` as examples. The use-case lead must resolve the test selection for each scenario, wallet and role.

| ID   | Wallet     | Role                 | Block              | Candidate test case | Status | Result | Execution date | Evidence / issue |
|------|------------|----------------------|--------------------|---------------------|--------|--|---|---|
| 4.1  | EBW        | Holder or Verifier   | CS-01 Issuance     | `VCI-006`           | ⚪      | Not run | | |
| 4.2  | EBW        | Holder or Verifier   | CS-02 Presentaton  | `VP-001`            | ⚪      | Not run | | |
| 4.3  | EUDI MVP   | Holder or Verifier   | CS-01 Issuance     | `VCI-006`           | ⚪      | Not run | | |
| 4.4  | EUDI MVP   | Holder or Verifier   | CS-02 Presentation | `VP-001`            | ⚪      | Not run | | |
| 4.5  | EBW        | Issuer               | CS-01 Issuance     | `VCI-006`           | ⚪      | Not run | | |

## Stage 5 – WEBUILD Trust List Registration
Follow the generic Stage 5 instructions in `WP4_Onboarding.md`. The detailed PA3 source identifies the candidate registry checks below. **Applicability must be decided by the use-case lead for each role, credential type and scenario**. Pure Holders may qualify for the documented Holder exception; do not assign registry tasks automatically.

| ID  | Applicable role / wallet | Registration or verification requirement                          | Registry / authority                        | Status | Evidence / N/A reason |
|-----|--------------------------|-------------------------------------------------------------------|---------------------------------------------|--------|-----------------------|
| 5.1 | Verifier / EUDI          | Access Certificate                                                | WEBUILD – Access Certificate Authorities    |        | ⚪                     | |
| 5.2 | Verifier / EUDI          | Registration Certificate covering service, attributes and purpose | WEBUILD – Access Registration Authorities   | ⚪      |                       |
| 5.3 | Wallet Provider          | Wallet-provider registry entry                                    | WEBUILD – Wallet Providers                  |        | ⚪                     |  |

**Note** the Registration of the PUB-EAA, QEAA, PID, EBWOID Issuer* is not part of this tracking

**Verification note:** Access and Registration Certificates are obtained from the appropriate certificate authorities (the source references Raidiam), not uploaded as ordinary entries to IDunion. For pure Holders, record `➖ Holder exception` only after role applicability is confirmed. Duplicate attestation-specific registration rows as needed.

## Stage 6 – Trust conformance (CS-Trust)
| ID   | Wallet                     | Role | Test case ID                   | Status | Result  | Date | Evidence / defect |
|------|----------------------------|------|--------------------------------|--------|---------|------|-------------------|
| 6.1  | EBW                        | TBD  | TBD – use-case lead to define  | ⚪      | Not run |      |                   |
| 6.2  | EUDI (repeat per provider) | TBD  | TBD – use-case lead to define  | ⚪      | Not run |      |                   |
*TBD*

## Stage 7 – Sectorial-specific conformance
| ID    | Wallet | Role                   | Conformance block | Test case ID |  Status | Result | Date | Evidence |
|-------|--------|------------------------|-------------------|--------------|---|---|------|----------|
| 7.1   | EUDI   | Holder / signatory – ❔ | CS-Signature      | TBD          |⚪ | Not run |      |          |
| 7.2   | EBW    | Issuer – ❔             | CS-Issuer         |  TBD         |  ⚪ | Not run |      |          |
*TBD*

# Stage 8 – Role-Specific Prerequisite Provisioning

**Purpose:** Track use-case-specific credential prerequisites separately for the Holder, Verifier and Issuer roles. The use-case lead determines applicability for each scenario. The partner records actual status and evidence.
**Status legend:** ⚪ Not started · 🟡 In progress · ✅ Done · 🔴 Blocked · ➖ Not applicable · ❔ To confirm.

## Stage 8.1 – Supplier: Credential Provisioning

**Objective:** Obtain or self-issue required credentials and make them available in the appropriate wallet.

| ID     | Credential     | Wallet  | Holder action                   | Source / issuer reference | Status | Date | Evidence / dependency |
|--------|----------------|---------|---------------------------------|--------------------------|--------|---|---|
| 8.1.1  | PID            | EUDI    | Obtain credential               | [EUDI PID issuer]        | ⚪      |  | |
| 8.1.2  | EBWOID         | EBW     | Obtain credential               | [EBWOID issuer]          | ⚪      |  | |
| 8.1.3  | EUCC           | EBW     | Obtain credential               | [EUCC Issuer]            | ⚪      |  | |
| 8.1.3  | POR            | EBW     | Obtain credential               | [POR Issuer]             | ⚪      |  | |
| 8.1.4  | CompanyInfo    | EBW     | Obtain credential (self-issued) | Company wallet           | ⚪      |  | |
| 8.1.5  | ContactPerson  | EBW     | Obtain credential (self-issued) | Company wallet           | ⚪      |  | |
| 8.1.6  | VAT            | EBW     | Obtain credential (self-issued) | Company wallet           | ⚪      |  | |
| 8.1.9  | PaymentTerms   | EBW     | Obtain credential (self-issued) | Company wallet           | ⚪      |  | |
| 8.1.10 | IBAN-OV        | EBW     | Obtain credential               | [Bank Issuer]            | ⚪      |  | |

## Stage 8.2 – Customer: Schema and DCQL Configuration

**Objective:** Prepare credential schemas and DCQL proof requests for the attestations that the scenario requires the Verifier to check. The wallet column identifies the credential's target wallet, not necessarily the Verifier's software environment.

| ID     | Credential    | Wallet  | Verifier action                              | Source / issuer reference | Status | Date | Evidence / dependency |
|--------|---------------|---------|----------------------------------------------|---------------------------|--------|------|-----------------------|
| 8.2.1  | PID           | EUDI    | Import schema; configure DCQL proof request  | [EUDI PID issuer]         | ⚪      |      |                       |
| 8.2.2  | EBWOID        | EBW     | Import schema; configure DCQL proof request  | [EBWOID PID issuer]       | ⚪      |      |                       |
| 8.2.3  | EUCC          | EBW     | Import schema; configure DCQL proof request  | Company wallet            | ⚪      |      |                       |
| 8.2.4  | POR           | EBW     | Import schema; configure DCQL proof request  | Company wallet            | ⚪      |      |                       |
| 8.2.5  | CompanyInfo   | EBW     | Import schema; configure DCQL proof request  | Company wallet            | ⚪      |      |                       |
| 8.2.6  | ContactPerson | EBW     | Import schema; configure DCQL proof request  | Company wallet            | ⚪      |      |                       |
| 8.2.7  | VAT           | EBW     | Import schema; configure DCQL proof request  | Company wallet            | ⚪      |      |                       |
| 8.2.8  | PaymentTerms  | EBW     | Import schema; configure DCQL proof request  | Company wallet            | ⚪      |      |                       |
| 8.2.9  | IBAN-OV       | EBW     | Import schema; configure DCQL proof request  | [Bank issuer]             | ⚪      |      |                       |
| 8.2.10 | eInvoice      | EBW     | Import schema; configure DCQL proof request  | Company wallet            | ⚪      |      |                       |
| 8.2.10 | eReceipt      | EBW     | Import schema; configure DCQL proof request  | Company wallet            | ⚪      |      |                       |

## Stage 8.3 – Issuer: Credential Issuance Configuration

**Objective:** Configure schemas, test data and issuance capabilities for credentials that the partner is authorized and required to issue. PID, EBWOID and EUCC issuance is applicable only to designated issuers; do not assume that a partner can issue these credentials.

| ID    | Credential    | Wallet | Issuer action | Source / issuer reference             | Status |  Date | Evidence / dependency |
|-------|---------------|---------------|---------------|---------------------------------------|--------|---|---|
| 8.3.1 | CompanyInfo   | EBW    | Self-issue    | Company wallet ; configure test data  | ⚪      |          | |
| 8.1.2 | ContactPerson | EBW    | Self-issue    | Company wallet; configure test data   | ⚪      |          | |
| 8.1.3 | VAT           | EBW    | Self-issue    | Company wallet; configure test data   | ⚪      |          | |
| 8.1.4 | PaymentTerms  | EBW    | Self-issue    | Company wallet; configure test data   | ⚪      |          | |
| 8.1.5 | eInvoice      | EBW    | Issue         | Company wallet; configure test data   | ⚪      |          | |
| 8.1.6 | eReceipt      | EBW    | Issue         | Company wallet; configure test data   | ⚪      |          | |

## Stage 9 – MVP interoperability execution
**Only this baseline and its scenario/partner tracker copies define and record MVP interoperability execution.** Neither PA4 Scenario 1 source provides approved end-to-end test steps or actual execution results. The rows below are placeholders to be specified by the use-case lead; they are not evidence of completion.

## 9.1. Direct case
| Test ID   | Scenario step                                          | Participants          | Expected result / acceptance criterion | 
|-----------|--------------------------------------------------------|-----------------------|---|
| Step1     | Seller is onboarded as business partner                | Initiator / Verifier  | Identification process is successfully initiated. | 
| Step2     | Seller create invoice in the internal system           | Initiator / Verifier  | Identification process is successfully initiated. | 
| Step3     | Seller issue the eInvoice directly to business partner | Initiator / Verifier  | Required information is captured and validated. | 

## 9.2. Indirect case

| Test ID | Scenario step                                                   | Participants | Expected result / acceptance criterion | Owner |
|---------|-----------------------------------------------------------------|---|---|
| Step1   | Seller is onboarded as business partner                         | Initiator / Verifier | Identification process is successfully initiated. | 
| Step2   | Seller trigger the invoice generation for indirect invoice      | Initiator / Verifier | Identification process is successfully initiated. | 
| Step3   | Seller - ERDS issue the eInvoice to specified business partner | Initiator / Verifier | Required information is captured and validated. | 
| Step4   | Buyer receive the invoice and  accept  it                       | Initiator / Verifier | Required information is captured and validated. | 
| Step5   | Buyer validate the invoice                                      | Initiator / Verifier | Required information is captured and validated. | 
| Step6   | Buyer validate against internal system ( ex. SAP and non -SAP)   | Initiator / Verifier | Required information is captured and validated. | 
| Step7   | Buyer trigger the settlement                                    | Initiator / Verifier | Required information is captured and validated. | 

## Actual MVP Execution Runs

> Record each execution and retest separately. Do not overwrite historical runs.

### Actual execution runs (append every run and retest)
| Run ID | Test ID | Date | Partner / wallet version | Actual result | Outcome  | Evidence / log | Defect ID | Retest of | Executor |
|--------|---------|------|--------------------------|---------------|----------|----------------|-----------|-----------|----------|
| TBD    | TBD     |      |                          |               | Not run  |                |           |           |          |

## Issues and blockers
| ID   | Scenario / stage / test | Description | Severity | Owner | Opened | Status | Resolution / date |
|------|-------------------------|-------------|----------|-------|--------|--------|-------------------|
| TBD  |                         |             |          |       |        |        |                   |

## Issues and blockers
| ID  | Scenario / stage / test | Description | Severity | Owner | Opened | Status | Resolution / date |
|-----|-------------------------|-------------|----------|-------|--------|--------|-------------------|
| TBD |                         |             |          |       |        |        |                   |

## Change log
| Date | Author | Change | Baseline version |
|---|---|---|---|
| 2026-11-19 | Draft prepared from three uploaded files | Consolidated BU1 Scenario 1 candidate requirements into WP4 nine-stage tracker; no partner progress inferred | 0.1 draft |
