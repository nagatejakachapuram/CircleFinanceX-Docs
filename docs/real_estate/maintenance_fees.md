# Maintenance Fees

Every property on Circle Pay incurs **ongoing maintenance costs** such as repairs, utilities, and management fees.  
These expenses are **shared among investors** based on their ownership percentage and are settled in **USDC**.

---

## How It Works

### 1. Fee Announcement

- Property managers announce the **maintenance cost per share** at regular intervals (e.g., monthly).
- This cost is published on-chain so investors can review it before payments are due.

### 2. Payment Options

Investors can settle maintenance fees in two ways:

#### **a) Direct Payment**

Investors proactively pay their share using USDC:

```solidity
function payMaintenance(uint256 amount) external {
    require(usdc.transferFrom(msg.sender, address(this), amount), "USDC transfer failed");
}
```

#### **b) Automatic Deduction**

If investors fail to pay directly, the system **deducts the maintenance fee from their rental income** before distribution:

```solidity
function deductMaintenance(address investor, uint256 fee) internal {
    // Adjust the investor's net rental payout
    uint256 netPayout = pendingRent[investor] - fee;
    pendingRent[investor] = netPayout > 0 ? netPayout : 0;
}
```

---

## Pro-Rata Fee Calculation

```
Investor Fee = (Investor Shares / Total Shares) × Total Maintenance Cost
```

**Example:**

- **Total Maintenance Cost:** 2,000 USDC
- **Total Shares:** 100,000
- **Investor A’s Shares:** 5,000 (5%)
- **Investor A’s Fee:** 100 USDC

If unpaid, **100 USDC will be deducted from Investor A’s rent payout**.

---

**Next:** [USDC On-Chain Integration](../usdc/onchain.md)
