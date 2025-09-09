# Buying Shares with USDC

This guide explains how verified investors can **purchase fractional ownership shares** of tokenized properties using **USDC** on CircleX Finance across multiple blockchain networks.

---

## Prerequisites

Before buying shares, ensure you have:

- ✅ **Connected Wallet**: Active wallet connection
- ✅ **KYC Verified**: Completed identity verification
- ✅ **OnchainID Created**: Decentralized identity set up
- ✅ **USDC Balance**: Sufficient USDC on your chosen network

---

## Step-by-Step Process

### 1. Browse Available Properties

- Visit the **CircleX Finance Dashboard** at [circlefinancex.vercel.app](https://circlefinancex.vercel.app/) to view tokenized properties
- Each listing shows:
  - **Property Details**: Location, size, type, and features
  - **Investment Metrics**: APY, rental frequency, token price
  - **Compliance Status**: USDC-only, ERC-3643 compliant
  - **Network Support**: Available blockchain networks

### 2. Select Property and Network

- **Choose Property**: Select the property you want to invest in
- **Select Network**: Choose your preferred blockchain network
- **Review Details**: Review property information and investment terms
- **Check Availability**: Verify shares are available for purchase

### 3. Approve USDC Spending

Before buying shares, you must **approve** the property contract to spend your USDC:

```solidity
IERC20(usdc).approve(propertyContract, amount);
```

- **`usdc`** – The USDC token address on your chosen network
- **`propertyContract`** – The property's smart contract address
- **`amount`** – The USDC amount you intend to invest

### 4. Buy Shares

Once approved, call `buyShares()` on the property contract:

```solidity
function buyShares(uint256 amount) external onlyVerifiedInvestor {
    IERC20 usdc = IERC20(usdcAddresses[block.chainid]);

    // Transfer USDC from investor to contract
    require(usdc.transferFrom(msg.sender, address(this), amount), "USDC transfer failed");

    // Calculate shares based on current property value
    uint256 shares = calculateShares(amount);

    // Mint ownership tokens to investor
    _mint(msg.sender, shares);

    emit SharesPurchased(msg.sender, amount, shares);
}
```

- **`amount`** – The USDC amount to invest
- **`shares`** – The number of ownership tokens issued
- **`onlyVerifiedInvestor`** – Ensures only KYC-verified investors can invest

### 5. Receive Ownership Tokens

After successful purchase, you receive **ownership tokens** representing your fractional stake:

- **Token Storage**: Tokens stored in your wallet
- **Ownership Tracking**: Track your fractional ownership
- **Income Rights**: Entitlement to proportional rental income
- **Transfer Rights**: Ability to transfer or sell shares

---

## Multi-Chain Investment

### Supported Networks

#### Ethereum Mainnet

- **USDC Address**: `0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48`
- **Gas Token**: ETH
- **Status**: ✅ Fully Supported

#### Base

- **USDC Address**: `0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913`
- **Gas Token**: ETH
- **Status**: ✅ Fully Supported

#### Polygon

- **USDC Address**: `0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174`
- **Gas Token**: MATIC
- **Status**: ✅ Fully Supported

#### Solana

- **USDC Address**: `EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v`
- **Gas Token**: SOL
- **Status**: ✅ Fully Supported

### Cross-Chain Investment

#### Using CCTP V2 Bridge

1. **Transfer USDC**: Use CCTP V2 to transfer USDC to desired network
2. **Invest on Network**: Purchase property shares on chosen network
3. **Unified Portfolio**: View all investments in unified portfolio

#### Network Selection

- **Ethereum**: Highest security, highest gas costs
- **Base**: Low gas costs, fast transactions
- **Polygon**: Very low gas costs, good ecosystem
- **Solana**: Fastest transactions, lowest fees

---

## Investment Examples

### Example 1: Ethereum Mainnet Investment

```solidity
// USDC Contract Address
address constant USDC = 0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48;

// Property Contract Address
address constant PROPERTY = 0x1234...5678;

// Investment Amount
uint256 amount = 1000 * 10**6; // 1000 USDC (6 decimals)

// Step 1: Approve USDC spending
IERC20(USDC).approve(PROPERTY, amount);

// Step 2: Buy shares
PropertyContract(PROPERTY).buyShares(amount);
```

### Example 2: Base Network Investment

```solidity
// USDC Contract Address on Base
address constant USDC_BASE = 0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913;

// Property Contract Address on Base
address constant PROPERTY_BASE = 0xABCD...EFGH;

// Investment Amount
uint256 amount = 500 * 10**6; // 500 USDC

// Step 1: Approve USDC spending
IERC20(USDC_BASE).approve(PROPERTY_BASE, amount);

// Step 2: Buy shares
PropertyContract(PROPERTY_BASE).buyShares(amount);
```

---

## Compliance and Security

### ERC-3643 Compliance

CircleX Finance uses **ERC-3643** for compliance:

- **Identity Verification**: Only verified investors can invest
- **Access Control**: Granular permission management
- **Audit Trails**: Complete transaction history
- **Regulatory Compliance**: Built-in compliance features

### OnchainID Integration

- **Identity Verification**: OnchainID required for all investments
- **Claim Validation**: KYC claims verified on-chain
- **Permission Management**: Role-based access control
- **Privacy Protection**: Minimal data storage on-chain

---

## Investment Limits

### Minimum Investment

- **Real Estate**: $100 USDC minimum
- **Index Funds**: $50 USDC minimum
- **Treasuries**: $25 USDC minimum

### Maximum Investment

- **Per Property**: $100,000 USDC maximum
- **Daily Limit**: $500,000 USDC maximum
- **Monthly Limit**: $2,000,000 USDC maximum

### KYC-Based Limits

- **Basic KYC**: Standard investment limits
- **Enhanced KYC**: Higher investment limits
- **Institutional KYC**: Highest investment limits

---

## Transaction Fees

### Network Fees

- **Ethereum**: $5-20 gas fees
- **Base**: $0.01-0.05 gas fees
- **Polygon**: $0.01-0.05 gas fees
- **Solana**: $0.001-0.01 gas fees

### Platform Fees

- **Investment Fee**: 0.5% of investment amount
- **Management Fee**: 1% annually
- **Performance Fee**: 10% of profits (if applicable)

---

## Portfolio Management

### Unified Portfolio View

- **Cross-Chain Balance**: View all investments across networks
- **Performance Tracking**: Track performance across all investments
- **Income Aggregation**: Aggregate income from all sources
- **Risk Management**: Manage risk across all investments

### Investment Tracking

- **Transaction History**: Complete transaction history
- **Performance Metrics**: Real-time performance tracking
- **Income Tracking**: Track rental income and distributions
- **Tax Reporting**: Generate tax reports

---

## Best Practices

### Investment Strategy

- **Diversification**: Invest across multiple properties
- **Risk Management**: Consider risk-return profile
- **Liquidity Planning**: Plan for liquidity needs
- **Long-term Perspective**: Think long-term

### Security Practices

- **Secure Wallets**: Use secure wallet solutions
- **Private Key Security**: Keep private keys secure
- **Transaction Verification**: Verify all transactions
- **Regular Monitoring**: Monitor investments regularly

---

## Troubleshooting

### Common Issues

#### Investment Failed

- **Insufficient Balance**: Ensure sufficient USDC balance
- **Gas Issues**: Check gas fees and limits
- **KYC Issues**: Verify KYC verification status
- **Network Issues**: Check network connectivity

#### Transaction Delays

- **Network Congestion**: Try during lower activity
- **Gas Estimation**: Use higher gas estimates
- **Network Issues**: Check network status
- **Retry Transaction**: Attempt transaction again

### Support Resources

- 📧 **Email Support**: [support@circlex.finance](mailto:support@circlex.finance)
- 💬 **Discord Community**: [Join our Discord](https://discord.gg/circlexfinance)
- 📖 **Documentation**: Comprehensive guides and FAQs
- 🐦 **Twitter**: [@circlexfinance](https://twitter.com/circlexfinance)

---

## Next Steps

After buying shares:

1. **Monitor Performance**: Track your investment performance
2. **Receive Income**: Start receiving rental income
3. **Manage Portfolio**: Manage your investment portfolio
4. **Plan Future Investments**: Plan additional investments

---

**Ready to invest?** [Browse available properties](https://circlefinancex.vercel.app/) and start building your tokenized real estate portfolio!
