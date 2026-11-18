# MVP Implementation Status Tracker – PA4 Scenario 2

This tracker monitors the progress of preparation for the Buyer, the Seller and the ERP / Payment system in order to run the MVP for PA4 Scenario 2 (eInvoice → Pay → eReceipt).

| Company                 | Related Person    | Role                                                           |
|:------------------------|:------------------|:---------------------------------------------------------------|
| **Seller**              | <name_partner2>   | eInvoice & eReceipt Issuer                                     |
| **Buyer**               | <name_partner1>   | Holder (eInvoice, eReceipt) / Payer                            |
| **Seller ERP Provider** | <name_erp_seller> | ERP system of the Seller (e.g. SAP – eInvoice / eReceipt data) |
| **Buyer ERP Provider**  | <name_erp_buyer>  | ERP system of the Buyer (approval, payment, reconciliation)    |

| Setting          | Selection           |
|:-----------------|:--------------------|
| **Payment mode** | ☐ Mocked ☐ Real 1 € (optional extension) |

## A. Environment Readiness

### 1. Seller Environment (Partner2)

| Component                | Detail operating system | Status |
|:-------------------------|:------------------------|:------:|
| **EBW Installed**        |                         |  ✅❌   |
| **ERP connected to EBW** | ERP provider: <name>    |  ✅❌   |

### 2. Buyer Environment (Partner1)

| Component                | Detail operating system | Status |
|:-------------------------|:------------------------|:------:|
| **EBW Installed**        |                         |  ✅❌   |
| **ERP connected to EBW** | ERP provider: <name>    |  ✅❌   |

## B. Conformance Specification

> **Note – CS-Trust for EAA issuance (eInvoice & eReceipt):** In the MVP, the issuers of eInvoice and eReceipt are not added to a trust list, as trust lists are not considered a scalable solution for this at this point. A vision for MVP+ is foreseen from BU1 and needs to be reconfirmed with all MVP members.

### 1. Seller Environment (Partner2)

| Component | Conformance                             | Status |
|:----------|:----------------------------------------|:------:|
| **EBW **  | CS-Basic, Role: Issuer                  |  ✅❌   |
| **EBW **  | CS-Issuer, Role: Issuer                 |  ✅❌   |

### 2. Buyer Environment (Partner1)

| Component | Conformance            | Status |
|:----------|:-----------------------|:------:|
| **EBW **  | CS-Basic, Role: Holder |  ✅❌   |

## C. Credential Tracking

## Prerequisite (BU1 / PA3)

Assumption: KYS & KYC (BU1 / PA3) have been completed, so Buyer and Seller are whitelisted and have each other's IBAN and EBW connectivity data in their ERP; all members are onboarded to the Trust Console and trust works.

### 1. Attestations held

| Component       | Attestations          | Status |
|:----------------|:----------------------|:------:|
| **Seller EBW ** | EBWOID, EUCC, IBAN-OV |  ✅❌   |
| **Buyer EBW **  | EBWOID, EUCC, IBAN-OV |  ✅❌   |

### 2. Schemas loaded (for issuance & receiving in Scenario2) - see https://github.com/webuild-consortium/webuild-attestation-rulebooks-catalog 

| Component       | Schemas                                                                       | Status |
|:----------------|:------------------------------------------------------------------------------|:------:|
| **Seller EBW ** | eInvoice, eReceipt – to issue                                                 |  ✅❌   |
| **Buyer EBW **  | eInvoice, eReceipt – to receive (only if the wallet requires a schema import) |  ✅❌   |

## Scenario2

> Steps 2 and 3 run in the ERP and bank systems, not in the EBW. Pass/fail is judged by what the ERP shows (payment status, confirmation, reconciliation)

### Step 1 – eInvoice issued and approved

| Component       | Test step                                                                       | Status |
|:----------------|:--------------------------------------------------------------------------------|:------:|
| **Seller ERP ** | eInvoice created, data fetched from ERP (e.g. SAP: amount, IBAN, payment terms) |  ✅❌   |
| **Seller EBW ** | eInvoice issued into Buyer EBW                                                  |  ✅❌   |
| **Buyer EBW **  | eInvoice received, attestation valid and active (not revoked)                   |  ✅❌   |
| **Buyer ERP **  | eInvoice checked (ERP check) and approved                                       |  ✅❌   |
| **Buyer EBW **  | Approved eInvoice stored in EBW                                                 |  ✅❌   |

### Step 2 – Payment initiated and confirmed

| Component       | Test step                                                              | Status |
|:----------------|:-----------------------------------------------------------------------|:------:|
| **Buyer ERP **  | Payment instruction mock-triggered according to payment terms (x days) |  ✅❌   |
| **Buyer Bank ** | Payment instruction received (IBAN, amount, invoice reference)         |  ✅❌   |
| **Buyer Bank ** | Legal entity chosen in bank channel, payment executed                  |  ✅❌   |
| **Buyer ERP **  | Confirmation of successful transaction displayed                       |  ✅❌   |

### Step 3 – Money transfer, notification and reconciliation

| Component       | Test step                                               | Status |
|:----------------|:--------------------------------------------------------|:------:|
| **Buyer Bank ** | Money transferred to Seller Bank                        |  ✅❌   |
| **Buyer ERP **  | Status information displayed                            |  ✅❌   |
| **Seller ERP ** | Credit notice displayed                                 |  ✅❌   |
| **Buyer ERP **  | Reconciled: eInvoice shown as paid within payment terms |  ✅❌   |

### Step 4 – Payment matched and eReceipt issued

| Component       | Test step                                                                       | Status |
|:----------------|:--------------------------------------------------------------------------------|:------:|
| **Seller ERP ** | Payment matched to eInvoice                                                     |  ✅❌   |
| **Seller ERP ** | eReceipt data fetched (invoice, payment, Buyer EBW connectivity from whitelist) |  ✅❌   |
| **Seller EBW ** | eReceipt attestation issued into Buyer EBW                                      |  ✅❌   |
| **Buyer EBW **  | eReceipt received, attestation valid and active (not revoked)                   |  ✅❌   |

### Step 5 – Into the books

| Component       | Test step                            | Status |
|:----------------|:-------------------------------------|:------:|
| **Buyer ERP **  | eReceipt linked to the paid eInvoice |  ✅❌   |
| **Seller ERP ** |
