# MVP PA4 Scenario 2 – Bosch Buyer / Verifier Tracker

**Status legend:** ⚪ Not started · 🟡 In progress · ✅ Done · 🔴 Blocked · ➖ N/A (with reason) · ❔ To confirm. **Test outcomes:** Not run / Pass / Fail / Blocked / Retest pending.

## Partner and scenario profile
| Field                   | Baseline value                |
|-------------------------|-------------------------------|
| Use case / scenario     | PA4_Scenario2                 |
| Partner                 | Robert Bosch GmbH             |
| Partner owner / contact | Florin Coptil                 |                
| Business role           | Buyer                         |
| Technical role          | Verifier / Relying Party (RP) |
| Baseline version        | 0.1                           |
| Last updated            | 2026-11-19                    |
| Overall status          | ⚪                             |

## Wallet inventory and proposed roles
| Wallet| Wallet type / purpose                                          | MVP or MVP+ | Provider / version    | Scenario / partner / role | Status     | Evidence |
|-------|----------------------------------------------------------------|-------------|-----------------------|---------------------------|------------|----------|
| EBW   | EBW for legal-entity workflows                                 | MVP         | Procivis EBW          | Buyer- Verifier           | installed  |          |
| EUDI  | EUDI Wallet for legal representative to obtain EBWOID& & EUCC  | MVP         | Procivis One Android  | Buyer - Verifier          | installed  |          |

## Stage 1 – Role identification
| ID   | Requirement                            | Status | Evidence / decision |
|------|----------------------------------------|--------|---------------------|
| 1.1  | **Business role:** Buyer.              | ⚪      |                     |
| 1.2  | **Technical roles recorded:** Verifier | ⚪      |                     |
| 1.3  | MVP and MVP+Plus                       | ⚪      |                     |
| 1.4  | Tests: SBB, Datev,....                 | ⚪      |                     |

## Stage 2 – Wallet initialization and deployment

| ID  | Wallet | Requirement                                                                      | Status | Date | Evidence |
|-----|--------|----------------------------------------------------------------------------------|--------|------|----------|
| 2.1 |  EBW | Procivis EBW         | 2026-05-04         | ✅ |       |

## Stage 3 – ITB onboarding


| ID  | Requirement           | Status | Evidence / action                                                                 |
|-----|-----------------------|--------|-----------------------------------------------------------------------------------|
| 3.1 | ITB account active    | ✅      | Bosch-specific source reports verified active account; username/link not supplied |
| 3.2 | `#wp4-testing` joined | ❔      |                                                                                   |


## Stage 4 – ITB Basic Conformance


| ID    | Wallet              | Block                          | Test case ID | Reported status     | Date       | Evidence / notes |
|-------|---------------------|--------------------------------|--------------|---------------------|------------|---|
| 4.1   | EBW – Procivis      | CS-01 Issuance                 | `VCI-006`    | ✅ Passed (reported) | 2026-05-04 | ITB result link pending |
| 4.2   | EBW – Procivis      | CS-02 Presentation             | `VP-001`     | ✅ Passed (reported) | 2026-05-04 | ITB result link pending |

## Stage 5 — WEBUILD Trust List Registration

Use `WP4_Onboarding.md` Stage 5 for the generic procedure. Applicability must be approved per technical role and credential type.

| ID   | Requirement                       | Status | Evidence / next action                                                            |
|------|-----------------------------------|--------|-----------------------------------------------------------------------------------|
| 5.1. | Verifier Access Certificate       |        | ❔      | Check applicability for EUDI credentials; certificate and issuer evidence missing |
| 5.2. | Verifier Registration Certificate |        | ❔      | Confirm service scope and evidence                                                |


## Stage 6 – Trust conformance (CS-Trust)
| ID   | Wallet                     | Role | Test case ID                   | Status | Result  | Date | Evidence / defect |
|------|----------------------------|------|--------------------------------|--------|---------|------|-------------------|
| 6.1  | EBW                        | TBD  | TBD – use-case lead to define  | ⚪      | Not run |      |                   |
| 6.2  | EUDI (repeat per provider) | TBD  | TBD – use-case lead to define  | ⚪      | Not run |      |                   |
*TBD*

## Stage 7 – Sectorial-specific conformance
| ID    | Wallet | Role                   | Conformance block | Test case ID |  Status | Result | Date | Evidence |
|-------|--------|------------------------|-------------------|--------------|---|---|------|----------|
*not required*

# Stage 8 – Role-Specific Prerequisite Provisioning

### Stage 8.1 — Holder: credential provisioning

| ID    | Credential          | Wallet  | Action            | Status | Date       | Evidence / dependency     |
|-------|---------------------|---------|-------------------|--------|------------|---------------------------|
| 8.1.1 | PID                 | EUDI    | Obtain credential | ✅      | 2026-06-23 | PID Issuer  (EUDI Tester) | 
| 8.1.2 | EBWOID              | EBW     | Obtain credential | ✅      | 2026-06-23 | Bundesanzeiger Issuer     |

### Stage 8.2 — Verifier: schema and DCQL configuration

| ID     | Credential    | Wallet   | Action                                        | Status | Date       | Evidence / dependency                                                               |
|--------|---------------|----------|-----------------------------------------------|--------|------------|-------------------------------------------------------------------------------------|
| 8.2.1  | PID           | EUDI     | Import schema; configure DCQL proof request   | ✅      | 2026-06-23 | |
| 8.2.2  | EBWOID        | EBW      | Import schema; configure DCQL proof request   | ✅      | 2026-06-10 | |
| 8.2.3  | EUCC          | EBW      | Import schema; configure DCQL proof request   | ✅      | 2026-06-10 | |
| 8.2.3  | POR           | EBW      | Import schema; configure DCQL proof request   | ✅      | 2026-11-02 | |
| 8.2.4  | CompanyInfo   | EBW      | Import schema; configure DCQL proof request   | ✅      | 2026-07-14 | |
| 8.2.5  | ContactPerson | EBW      | Import schema; configure DCQL proof request   | ✅      | 2026-07-14 | |
| 8.2.6  | VAT           | EBW      | Import schema; configure DCQL proof request   | ✅      | 2026-07-14 | |
| 8.1.9  | PaymentTerms  | EBW      | Import schema; configure DCQL proof request   | ✅      | 2026-07-14 | |
| 8.1.10 | IBAN-OV       | EBW      | Import schema; configure DCQL proof request   | ✅      | 2026-07-14 | |       |  | |

## Stage 9 – MVP interoperability execution and sign-off

## 9.1. Direct case

## 9.1.1 SBB
| Test ID | Scenario step                                                                                                                                | Participants             | Status  | Date       | Expected result / acceptance criterion | 
|---------|----------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|---------|------------|----------------------------------------|
| Step 1  | Seller onboarding: The seller is registered and onboarded as an approved business partner.                                                   | Seller / Buyer           | ✅       | 2026-08-05 |Seller identity is successfully verified, and the seller is registered as an approved business partner in the buyer's system. |
| Step 2  | Invoice generation: The seller initiates the generation of an direct eInvoice for the selected business partner.                             | Seller                   | ✅       | 2026-08-05 |The eInvoice is generated with the required invoice data and linked to the correct business partner. |
| Step 3  | eInvoice issuance: The seller uses the ERDS to issue and securely deliver the eInvoice to the designated buyer.                              | Seller / Buyer           | ✅       | 2026-08-05 |The eInvoice is successfully issued and delivered to the intended buyer, with delivery confirmation recorded. |
| Step 4  | eInvoice receipt and acceptance: The buyer receives the eInvoice and acknowledges its receipt.                                               | Buyer                    | ✅       | 2026-08-05 |The eInvoice is successfully received, and its receipt is acknowledged and recorded. |
| Step 5  | eInvoice validation: The buyer validates the received eInvoice.                                                                              | Buyer / Verifier         | ✅       | 2026-08-05|The eInvoice passes the applicable format, integrity, authenticity and required-data checks. |
| Step 6  | Internal system validation: The buyer validates the eInvoice against internal business and financial systems (e.g., SAP or non-SAP systems). | Buyer / ERP System       | ✅       | 2026-08-05 |Invoice data is successfully matched against the relevant internal records, and the validation result is recorded. |
| Step 7  | Settlement initiation: The buyer initiates the invoice settlement process.                                                                   | Buyer / Financial System | ⚪       |            |The approved invoice is transferred to the payment process, and settlement initiation is confirmed. |

## 9.2. Indirect case 

## 9.2.1 Freelancer - Germany

| Test ID | Scenario step                                                                                                                                  | Participants             | Status | Date       |Expected result / acceptance criterion |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|--------|------------|---|
| Step 1  | Seller onboarding: The seller is registered and onboarded as an approved business partner.                                                     | Seller / Buyer           | ✅       | 2026-10-01 |Seller identity is successfully verified, and the seller is registered as an approved business partner in the buyer's system. |
| Step 2  | Invoice generation: The seller initiates the generation of an indirect eInvoice for the selected business partner.                             | Seller                   | ⚪      |            |The eInvoice is generated with the required invoice data and linked to the correct business partner. |
| Step 3  | eInvoice issuance: The seller uses the ERDS to issue and securely deliver the eInvoice to the designated buyer.                                | Seller / ERDS / Buyer    | ⚪      |            |The eInvoice is successfully issued and delivered to the intended buyer, with delivery confirmation recorded. |
| Step 4  | eInvoice receipt and acceptance: The buyer receives the eInvoice and acknowledges its receipt.                                                 | Buyer / ERDS             | ⚪      |            |The eInvoice is successfully received, and its receipt is acknowledged and recorded. |
| Step 5  | eInvoice validation: The buyer validates the received eInvoice.                                                                                | Buyer / Verifier         | ⚪      |            |The eInvoice passes the applicable format, integrity, authenticity and required-data checks. |
| Step 6  | Internal system validation: The buyer validates the eInvoice against internal business and financial systems (e.g., SAP or non-SAP systems).   | Buyer / ERP System       | ⚪      |            |Invoice data is successfully matched against the relevant internal records, and the validation result is recorded. |
| Step 7  | Settlement initiation: The buyer initiates the invoice settlement process.                                                                     | Buyer / Financial System | ⚪      |            |The approved invoice is transferred to the payment process, and settlement initiation is confirmed. |

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


## Change log
| Date | Author | Change | Baseline version |
|---|---|---|---|
| 2026-11-19 | Draft prepared from three uploaded files | Instantiated BU1 Scenario 2 Bosch Buyer / Verifier tracker from supplied template; no partner progress inferred | 0.1 draft |

