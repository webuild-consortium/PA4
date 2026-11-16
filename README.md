# WE BUILD PA4: Payment and eReceipt Issuance

PA4 defines how a buyer company pays a received eInvoice and obtains an eReceipt attestation in its European Business Wallet (EBW). Payment runs over a card rail (PSP) or an IBAN rail (Buyer Bank). Strong Customer Authentication (SCA) is performed by the company's Authorised Person through their EUDI Wallet.

Normative source: [wp3-technology-standards / sequence-diagrams / PA4](https://github.com/webuild-consortium/wp3-technology-standards/tree/main/sequence-diagrams/PA4), v1.0 final, 2026-06-19. This README gives an overview and maps the specification to the scenario folders in this repository. The actual sequences and workflows are in [pa4-ereceipt-scenarios.md](https://github.com/webuild-consortium/PA4/blob/docs/pa4-scenario-readme/pa4-ereceipt-scenarios.md).

## Scenarios

| Scenario                                                    | Invoice process                         | Payment rail                         | Person and mandate checks                                                                                          |
| ----------------------------------------------------------- | --------------------------------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| [1.1 Deferred invoice, card or IBAN payment](scenario-1.1/) | Payment first, then invoice and receipt | Card via PSP, or IBAN via Buyer Bank | Card: SCA in the EUDI Wallet, PoA checked by the PSP. IBAN: bank token check, SR + PoA for high-value transactions |
| [1.2 Upfront invoice, IBAN payment](scenario-1.2/)          | Invoice first, then payment and receipt | IBAN via Buyer Bank                  | Bank token check; SR + PoA for high-value transactions                                                             |
| [1.3 No invoice, card payment (retail)](scenario-1.3/)      | Placeholder, to be detailed separately  |                                      |                                                                                                                    |

Scenarios 1.1 and 1.2 follow the upstream specification. Scenario 1.3 is not covered by it.

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
