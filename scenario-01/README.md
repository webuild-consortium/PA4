# Scenario 1: Deferred invoice, card payment

The Seller requests payment first. The Authorised Person pays by card through the EUDI Wallet. The PSP performs SCA against the wallet and checks the card mandate (PoA) against the Buyer EBW. After settlement the Seller delivers the eInvoice and the eReceipt. Overview and shared context: [repository README](../README.md).

## Steps

| Step | Name                               | What happens                                                                                                             |
| ---- | ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| 0    | Trigger                            | Seller requests payment and presents a payment code                                                                      |
| 1    | Legal entity selection             | Authorised Person selects the legal entity in the Buyer EBW; the session is bound to it                                  |
| 2    | Payment initiation                 | Authorised Person scans the code with the EUDI Wallet; the wallet initiates the payment with the PSP                     |
| 3    | Payment authorisation              | PSP requests SCA from the EUDI Wallet; Authorised Person presents SCA (PIN or biometric)                                 |
| 4    | Legal entity payment authorisation | PSP checks the mandate against the Buyer EBW (PoA, scope: card, limit: x), then initiates settlement with the Buyer Bank |
| 5    | Settlement and notification        | Buyer Bank settles with Seller Bank; Buyer and Seller are notified                                                       |
| 6    | Invoice and eReceipt               | Seller sends the eInvoice and issues the eReceipt to the Buyer EBW                                                       |

- Inputs: Buyer EBW with SR and PoA; Authorised Person's EUDI Wallet with PID and SCA attestation.
- Outputs: settled card payment; eInvoice and eReceipt in the Buyer EBW.
- Errors: code scan failure, SCA failure, or missing or insufficient PoA. Payment is not settled.

## Sequence diagram

```mermaid
sequenceDiagram
  box Seller side
    participant Seller
    participant SellerBank as Seller Bank
  end
  box Buyer side
    actor AuthPerson as Authorised Person
    participant EUDI as EUDI Wallet
    participant Buyer as Buyer EBW
    participant BuyerBank as Buyer Bank
  end
  participant PSP

  note over Seller, PSP: Step 0: Trigger (deferred invoice)
  Seller ->> AuthPerson: Request payment and present the payment code

  note over Seller, PSP: Step 1: Legal entity selection
  AuthPerson ->> Buyer: Select the legal entity
  Buyer ->> Buyer: Bind session to the legal entity
  Buyer -->> AuthPerson: Redirect to payment

  note over Seller, PSP: Step 2: Payment initiation (card)
  AuthPerson ->> EUDI: Scan the payment code
  EUDI ->> PSP: Initiate card payment

  note over Seller, PSP: Step 3: Payment authorisation (SCA)
  PSP ->> EUDI: Request SCA
  AuthPerson ->> EUDI: Present SCA (PIN or biometric)
  EUDI -->> PSP: SCA result

  note over Seller, PSP: Step 4: Legal entity authorisation
  PSP <<->> Buyer: Check mandate (PoA, scope: card, limit: x)
  PSP ->> BuyerBank: Initiate settlement

  note over Seller, PSP: Step 5: Settlement and notification
  BuyerBank <<->> SellerBank: Payment settlement
  BuyerBank -->> Buyer: Settlement confirmation
  SellerBank -->> Seller: Settlement notification

  note over Seller, PSP: Step 6: Invoice and eReceipt
  Seller ->> Buyer: Send eInvoice (direct or indirect)
  Seller ->> Buyer: Issue eReceipt attestation (direct or indirect)
```
