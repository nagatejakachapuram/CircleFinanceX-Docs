# Rental Income Distribution

Each tokenized property on Circle Pay generates **rental income**, which is **distributed in USDC** to all investors based on their ownership percentage.

---

## How It Works

1. **Rent Collection**

   - Property managers collect rent from tenants off-chain.
   - The collected rent is converted to **USDC** and deposited into the property contract.

2. **On-Chain Distribution**

   - The contract calculates each investor’s share of the total rental income based on their token holdings.
   - Payments are distributed **proportionally** to all token holders.

3. **Automatic Payouts**
   - Investors receive their share of rent **directly into their wallets** as USDC.

---

## Pro-Rata Calculation

The rental income per investor is determined by:

```

Investor Payout = (Investor Shares / Total Shares) × Total Rent Collected

```

**Example:**

- **Total Rent Collected:** 10,000 USDC
- **Total Shares:** 100,000
- **Investor A’s Shares:** 5,000 (5%)
- **Investor A’s Payout:** 500 USDC

---

## Smart Contract Logic

```solidity
function distributeRent(
    address[] calldata investors,
    uint256[] calldata amounts
) external onlyOwner {
    require(investors.length == amounts.length, "Array length mismatch");
    for (uint i = 0; i < investors.length; i++) {
        require(usdc.transfer(investors[i], amounts[i]), "USDC transfer failed");
    }
}
```

- **`investors`** – Array of investor addresses
- **`amounts`** – Corresponding rent amounts in USDC

---

**Next:** [Maintenance Fees](maintenance_fees.md)
