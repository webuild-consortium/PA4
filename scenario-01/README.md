# Scenario 1: Deferred invoice, card or IBAN payment

The Seller requests payment first. The Authorised Person pays either by card through the EUDI Wallet, or by IBAN transfer from the Buyer EBW. On the card rail the PSP performs SCA against the wallet and checks the PoA mandate against the Buyer EBW. On the IBAN rail the Buyer Bank validates a token and, for high-value transactions, checks the SR and PoA mandate. After settlement the Seller delivers the eInvoice and the eReceipt. Overview and shared context: [repository README](../README.md).

## Steps

| Step | Name                               | What happens                                                                                                                                                                                                                                                                    |
| ---- | ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0    | Trigger                            | Seller requests payment and presents a payment code                                                                                                                                                                                                                             |
| 1    | Legal entity selection             | Authorised Person selects the legal entity in the Buyer EBW; the session is bound to it                                                                                                                                                                                         |
| 2    | Payment initiation                 | Card: Authorised Person scans the code with the EUDI Wallet, which initiates the payment with the PSP. IBAN: Authorised Person initiates the transfer from the Buyer EBW, which triggers payment filling at the Buyer Bank with a token                                         |
| 3    | Payment authorisation              | Card: PSP requests SCA from the EUDI Wallet; Authorised Person presents SCA (PIN or biometric). IBAN: Buyer Bank performs a token validity check, no SCA prompt                                                                                                                 |
| 4    | Legal entity payment authorisation | Card: PSP checks the mandate against the Buyer EBW (PoA, scope: card, limit: x) and initiates settlement with the Buyer Bank. IBAN standard: Buyer Bank checks the token authorisation. IBAN high-value: Buyer Bank checks the mandate (SR + PoA, scope: transaction, limit: x) |
| 5    | Settlement and notification        | Buyer Bank settles with Seller Bank; Buyer and Seller are notified                                                                                                                                                                                                              |
| 6    | Invoice and eReceipt               | Seller sends the eInvoice and issues the eReceipt to the Buyer EBW                                                                                                                                                                                                              |

- Inputs: Buyer EBW with SR and PoA; Authorised Person's EUDI Wallet with PID and SCA attestation.
- Outputs: settled payment; eInvoice and eReceipt in the Buyer EBW.
- Errors: code scan or token failure aborts before authorisation; SCA failure, invalid token, or missing or insufficient PoA or SR blocks settlement.

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

  note over Seller, PSP: Step 2: Payment initiation
  alt Card
    AuthPerson ->> EUDI: Scan the payment code
    EUDI ->> PSP: Initiate card payment
  else IBAN
    AuthPerson ->> Buyer: Initiate IBAN transfer
    Buyer ->> BuyerBank: Trigger payment filling with token
  end

  note over Seller, PSP: Step 3: Payment authorisation
  alt Card
    PSP ->> EUDI: Request SCA
    AuthPerson ->> EUDI: Present SCA (PIN or biometric)
    EUDI -->> PSP: SCA result
  else IBAN
    BuyerBank ->> BuyerBank: Token validity check (no SCA prompt)
  end

  note over Seller, PSP: Step 4: Legal entity authorisation
  alt Card
    PSP <<->> Buyer: Check mandate (PoA, scope: card, limit: x)
    PSP ->> BuyerBank: Initiate settlement
  else IBAN, standard transaction
    BuyerBank <<->> Buyer: Check token authorisation
    BuyerBank ->> BuyerBank: Initiate settlement
  else IBAN, high-value transaction
    BuyerBank <<->> Buyer: Check mandate (SR + PoA, scope: transaction, limit: x)
    BuyerBank ->> BuyerBank: Initiate settlement
  end

  note over Seller, PSP: Step 5: Settlement and notification
  BuyerBank <<->> SellerBank: Payment settlement
  BuyerBank -->> Buyer: Settlement confirmation
  SellerBank -->> Seller: Settlement notification

  note over Seller, PSP: Step 6: Invoice and eReceipt
  Seller ->> Buyer: Send eInvoice (direct or indirect)
  Seller ->> Buyer: Issue eReceipt attestation (direct or indirect)
```
