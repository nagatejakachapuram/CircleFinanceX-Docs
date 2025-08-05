# USDC Off-Chain Integration (Circle API)

While Circle Pay primarily operates **on-chain** using USDC as an ERC-20 token, some workflows may require **off-chain integrations** — such as **fiat deposits, bank withdrawals, or card payments**.

For these cases, Circle provides a set of **REST APIs** that extend USDC usability beyond blockchain transactions.

---

## When to Use Circle APIs

- **Fiat On-Ramps:** Let users deposit USD (via ACH, wire transfer, or card) and convert it to USDC.
- **Fiat Off-Ramps:** Allow investors to withdraw their earnings back to a bank account.
- **Card Payments:** Enable property share purchases directly with credit/debit cards.
- **Business Integrations:** Automate treasury workflows using Circle’s settlement infrastructure.

---

## Key APIs

| API Name         | Purpose                                                |
| ---------------- | ------------------------------------------------------ |
| **Payments API** | Accept card or bank payments and convert them to USDC. |
| **Payouts API**  | Send funds from Circle Pay to bank accounts or cards.  |
| **Wallets API**  | Manage custodial wallets for users (if needed).        |

### Reference:

[Circle API Documentation](https://developers.circle.com/)

---

## Example Use Case: Withdraw Earnings

1. Investor requests withdrawal of rental income.
2. Circle Pay converts on-chain USDC to fiat via Circle API.
3. Funds are sent directly to the investor’s linked bank account.

---

## Notes

- Off-chain APIs are **optional** and mainly for enabling fiat ramps.
- For purely on-chain operations (buying shares, rent payouts, fees), **ERC-20 USDC integration is sufficient**.
