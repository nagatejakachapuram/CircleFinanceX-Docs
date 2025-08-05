# Buying Shares with USDC

This guide explains how investors can **purchase fractional ownership shares** of tokenized properties using **USDC** on the Circle Pay platform.

---

## Step-by-Step Process

### 1. Browse Available Properties

- Visit the **Circle Pay Dashboard** to view a list of tokenized properties.
- Each listing shows:
  - Property details (location, size, yield estimate)
  - Share price in **USDC**
  - Total available shares

---

### 2. Approve USDC Spending

Before buying shares, the investor must **approve** the property contract to spend their USDC.

```solidity
IERC20(usdc).approve(propertyContract, amount);
```

- **`usdc`** – The address of the USDC token contract
- **`propertyContract`** – The address of the property’s smart contract
- **`amount`** – The number of USDC tokens the user intends to invest

---

### 3. Buy Shares

Once approved, the investor calls `buyShares()` on the property contract:

```solidity
function buyShares(uint256 amount) external {
    require(usdc.transferFrom(msg.sender, address(this), amount), "USDC transfer failed");
    uint256 shares = calculateShares(amount);
    _mint(msg.sender, shares); // Mint ownership tokens
}
```

- **`amount`** – The amount of USDC to invest
- **`shares`** – The number of ownership tokens issued (calculated by the contract)

---

### 4. Receive Ownership Tokens

- After a successful purchase, the contract **mints ownership tokens** representing the investor’s fractional stake in the property.
- These tokens are stored in the investor’s wallet and can be used to:

  - Track ownership
  - Claim rental income
  - Sell or transfer shares (if secondary markets are supported)

---

## Example (Ethereum Mainnet)

- **USDC Token Address:**
  `0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48`
- **Property Contract Address (example):**
  `0x1234...5678`

---

**Next:** [Rental Income](rental_income.md)
