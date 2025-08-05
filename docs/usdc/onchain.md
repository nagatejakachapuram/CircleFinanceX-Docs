# USDC On-Chain Integration

USDC is a **stablecoin pegged to the US dollar**, implemented as an **ERC-20 token** on Ethereum and multiple other chains.  
On Circle Pay, USDC is used for **all property-related transactions**, including **share purchases**, **rental income payouts**, and **maintenance fee payments**.

---

## Why USDC?

- **Stability:** Pegged 1:1 to USD, minimizing volatility.
- **Liquidity:** Widely used across major DeFi ecosystems.
- **Multi-chain Support:** Available on Ethereum, Polygon, Arbitrum, Base, Optimism, Avalanche, and more.

---

## Ethereum Mainnet USDC Address

```

0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48

```

---

## Key ERC-20 Functions

To integrate USDC in smart contracts, use the **IERC20 interface**:

```solidity
IERC20 usdc = IERC20(USDC_ADDRESS);

// Approve the property contract to spend USDC on behalf of the user
usdc.approve(propertyContract, amount);

// Transfer USDC directly between addresses
usdc.transfer(to, amount);

// Transfer USDC from one user to another through an approved contract
usdc.transferFrom(from, to, amount);
```

---

## Example: Buying Shares

```solidity
function buyShares(uint256 amount) external {
    require(usdc.transferFrom(msg.sender, address(this), amount), "USDC transfer failed");
    uint256 shares = calculateShares(amount);
    _mint(msg.sender, shares); // Mint ownership tokens
}
```

---

## Example: Distributing Rent

```solidity
function distributeRent(address[] calldata investors, uint256[] calldata amounts) external onlyOwner {
    require(investors.length == amounts.length, "Mismatch");
    for (uint i = 0; i < investors.length; i++) {
        require(usdc.transfer(investors[i], amounts[i]), "Transfer failed");
    }
}
```

---

## Supported Networks

- **Ethereum Mainnet**
- **Polygon**
- **Arbitrum**
- **Optimism**
- **Base**
- **Avalanche**

---

**Next:** [USDC Off-Chain Integration](offchain.md)
