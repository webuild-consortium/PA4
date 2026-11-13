# WE BUILD PA4: Payment and eReceipt Issuance

PA4 defines how a buyer company pays a received eInvoice and obtains an eReceipt attestation in its European Business Wallet (EBW). Payment runs over a card rail (PSP) or an IBAN rail (Buyer Bank). Strong Customer Authentication (SCA) is performed by the company's Authorised Person through their EUDI Wallet.

Normative source: [wp3-technology-standards / sequence-diagrams / PA4](https://github.com/webuild-consortium/wp3-technology-standards/tree/main/sequence-diagrams/PA4), v1.0 final, 2026-06-19. This README gives an overview and maps the specification to the scenario folders in this repository. The actual sequences and workflows are in [pa4-ereceipt-scenarios.md](https://github.com/webuild-consortium/PA4/blob/docs/pa4-scenario-readme/pa4-ereceipt-scenarios.md).

## Scenarios

| Scenario                          | Folder                         | Invoice process                         | Payment rail        | Person and mandate checks                              |
| --------------------------------- | ------------------------------ | --------------------------------------- | ------------------- | ------------------------------------------------------ |
| 1. Deferred invoice, card payment | [`scenario-01/`](scenario-01/) | Payment first, then invoice and receipt | Card via PSP        | SCA in the EUDI Wallet; PoA checked by the PSP         |
| 2. Upfront invoice, IBAN payment  | [`scenario-02/`](scenario-02/) | Invoice first, then payment and receipt | IBAN via Buyer Bank | Bank token check; SR + PoA for high-value transactions |
| 3. No invoice                     | [`scenario-03/`](scenario-03/) | Placeholder, to be detailed separately  |                     |                                                        |

Scenarios 1 and 2 are the two constellations covered by the MVP and MVP+ in the upstream specification. Deferred invoice with IBAN payment and upfront invoice with card payment are not part of the MVP or MVP+. Scenario 3 is not covered by the upstream specification.

## Actors

| Actor / System    | Role                                | Wallet / credentials                              |
| ----------------- | ----------------------------------- | ------------------------------------------------- |
| Seller            | eInvoice holder, eReceipt issuer    | Active EBW, minimum PA4 attestations              |
| Seller Bank       | Receives settlement                 | n/a                                               |
| Buyer             | Relying Party, payer                | Active EBW, minimum PA4 attestations, SR and PoA  |
| Authorised Person | Natural person acting for the Buyer | EUDI Wallet (Active) with PID and SCA attestation |
| Buyer Bank        | Buyer's home bank, IBAN rail        | Bank Wallet linked to the Buyer                   |
| PSP               | Card payment processor              | n/a                                               |
| Invoice Processor | eInvoice delivery infrastructure    | n/a                                               |
| Business Register | Issuer of the EBWOID                | n/a                                               |

The upstream text also uses "Authorised Representative" and, in PSD2 terms, "Authorised User" for the Authorised Person.

## Pre-requisites

- Business Register has issued an EBWOID to Seller and Buyer.
- Seller and Buyer EBWs hold only the minimum PA4 attestation set. No PA3 or BU1 onboarding.
- Buyer EBW holds valid SR attestations and the PoA for the Authorised Person.
- Authorised Person's EUDI Wallet is Active, with WUA, PID and SCA attestation.
- A Bank Wallet exists for the Buyer at its home bank.
- Seller and Buyer are connected to an Invoice Processor; the Buyer is also connected to a Payment Processor.
- Seller is classified as low or medium risk.
- The flow runs sequentially in a single-user session.
- No attestation is issued to the Authorised Person's EUDI Wallet. The eReceipt lands in the Buyer EBW.

MVP wallet simplifications: the holder EBW has mutual authentication enabled by default and accepts offers automatically within an active corporate session (automatic flow), or reduces authentication and authorisation to a visual check and manual approval (manual flow). The relying-party EBW performs cryptographic validation and issuer identification against an internal trusted list only. LOTL and device-binding checks are not applied.

## Out of scope

- Home-Bank onboarding (PA3); KYS and KYC onboarding (BU1).
- Separate business-representative onboarding (PA2).
- IBAN validation.
- Invoice delivery channel (SC5).
- Provisioning of the Authorised Person's EUDI Wallet.
- High-risk seller classifications.
- Lifecycle management of e-addresses.

## Acceptance criteria

| Criterion                                                                         | Sc. 1 | Sc. 2 |
| --------------------------------------------------------------------------------- | :---: | :---: |
| Flow executes with only the minimum PA4 attestation set                           | ✓     | ✓     |
| SCA requested and presented via the EUDI Wallet before settlement                 | ✓     |       |
| Token validity check passes without an SCA prompt                                 |       | ✓     |
| SR + PoA checked against the Buyer EBW before settlement (high-value transaction) |       | ✓     |
| Buyer EBW receives the eReceipt attestation after settlement                      | ✓     | ✓     |
| No attestation issued to the Authorised Person's EUDI Wallet                      | ✓     | ✓     |
| Flow completes in a single sequential user session                                | ✓     | ✓     |

## Open points

- Exact contents of the minimum attestation set for Seller and Buyer EBW.
- Trusted-list source used by the relying-party wallet.
- Whether eReceipt issuance is always direct or may be indirect in the MVP.
- Error and retry behaviour when SCA fails mid-flow.
- The earlier upstream draft (`PA4_Flow.mmd`) requested SCA for risk transactions on the IBAN rail. The final v1.0 flow does not. To be confirmed for high-value transactions in Scenario 2.

## Glossary

| Term        | Meaning                                           |
| ----------- | ------------------------------------------------- |
| EBW         | European Business Wallet                          |
| EBWOID      | EBW Organisational Identifier                     |
| EUDI Wallet | European Digital Identity Wallet (natural person) |
| PID         | Personal Identification Data credential           |
| WUA         | Wallet Unit Attestation                           |
| SCA         | Strong Customer Authentication                    |
| SR          | Signatory Rights attestation                      |
| PoA         | Power of Attorney attestation                     |
| PSP         | Payment Service Provider                          |
| KYS / KYC   | Know Your Supplier / Know Your Customer           |
| LOTL        | List of Trust Lists                               |

## References

- Upstream specification: [wp3-technology-standards / sequence-diagrams / PA4](https://github.com/webuild-consortium/wp3-technology-standards/tree/main/sequence-diagrams/PA4), v1.0 final, 2026-06-19. A verbatim copy is kept in [`pa4-ereceipt-scenarios.md`](pa4-ereceipt-scenarios.md).
- Sibling workflows: PA2 (business-representative onboarding), PA3 (Home-Bank onboarding), BU1 (KYS/KYC), SC5 (invoice delivery).
