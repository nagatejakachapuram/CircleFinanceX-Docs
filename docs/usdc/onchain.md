# USDC Integration

USDC is a **stablecoin pegged to the US dollar**, implemented as an **ERC-20 token** on Ethereum and multiple other chains.  
CircleX Finance uses USDC for **all investment transactions**, including **real estate investments**, **index fund purchases**, **treasury investments**, and **cross-chain transfers** via CCTP V2.

---

## Why USDC?

- **Stability:** Pegged 1:1 to USD, minimizing volatility.
- **Liquidity:** Widely used across major DeFi ecosystems.
- **Multi-chain Support:** Available on Ethereum, Base, Polygon, Solana, and more.
- **CCTP V2 Support:** Native cross-chain transfers via Circle's protocol.
- **Compliance:** Regulatory-compliant stablecoin with audit trails.

---

## Supported Networks

CircleX Finance supports USDC across multiple blockchain networks:

### Ethereum Mainnet

- **USDC Address**: `0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48`
- **Network ID**: 1
- **Native Token**: ETH
- **Status**: ✅ Fully Supported

### Base

- **USDC Address**: `0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913`
- **Network ID**: 8453
- **Native Token**: ETH
- **Status**: ✅ Fully Supported

### Polygon

- **USDC Address**: `0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174`
- **Network ID**: 137
- **Native Token**: MATIC
- **Status**: ✅ Fully Supported

### Solana

- **USDC Address**: `EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v`
- **Network ID**: 101
- **Native Token**: SOL
- **Status**: ✅ Fully Supported

---

## CCTP V2 Integration

### What is CCTP V2?

Circle's Cross-Chain Transfer Protocol (CCTP) V2 enables:

- **Native USDC Transfers**: No wrapped tokens or synthetic assets
- **Cross-Chain Bridging**: Transfer USDC between supported networks
- **Circle Backing**: Maintains Circle's full backing throughout transfer
- **Fast Transfers**: Typically completes in 10-15 minutes

### CCTP V2 Process

1. **Burn USDC**: USDC is burned on source chain
2. **Attestation**: Circle generates cryptographic attestation
3. **Mint USDC**: USDC is minted on destination chain
4. **Complete Transfer**: User receives USDC on destination chain

### CCTP V2 Benefits

- **No Bridge Risk**: No smart contract bridge vulnerabilities
- **Native USDC**: Always receive native USDC
- **Circle Backed**: Maintains Circle's backing and redemption
- **Regulatory Compliance**: Compliant with financial regulations

---

## Smart Contract Integration

### ERC-20 Interface

CircleX Finance uses the standard **IERC20 interface** for USDC integration:

```solidity
interface IERC20 {
    function totalSupply() external view returns (uint256);
    function balanceOf(address account) external view returns (uint256);
    function transfer(address to, uint256 amount) external returns (bool);
    function allowance(address owner, address spender) external view returns (uint256);
    function approve(address spender, uint256 amount) external returns (bool);
    function transferFrom(address from, address to, uint256 amount) external returns (bool);
}
```

### USDC Contract Integration

```solidity
// USDC contract addresses by network
mapping(uint256 => address) public usdcAddresses;

constructor() {
    usdcAddresses[1] = 0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48; // Ethereum
    usdcAddresses[8453] = 0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913; // Base
    usdcAddresses[137] = 0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174; // Polygon
    usdcAddresses[101] = 0xEPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v; // Solana
}

function getUSDCAddress(uint256 networkId) external view returns (address) {
    return usdcAddresses[networkId];
}
```

---

## Investment Transactions

### Real Estate Investments

```solidity
function investInProperty(uint256 propertyId, uint256 amount) external {
    IERC20 usdc = IERC20(usdcAddresses[block.chainid]);

    // Transfer USDC from investor to contract
    require(usdc.transferFrom(msg.sender, address(this), amount), "USDC transfer failed");

    // Calculate shares based on investment amount
    uint256 shares = calculateShares(propertyId, amount);

    // Mint property shares to investor
    _mint(msg.sender, propertyId, shares);

    emit PropertyInvestment(msg.sender, propertyId, amount, shares);
}
```

### Index Fund Investments

```solidity
function investInFund(uint256 fundId, uint256 amount) external {
    IERC20 usdc = IERC20(usdcAddresses[block.chainid]);

    // Transfer USDC from investor to contract
    require(usdc.transferFrom(msg.sender, address(this), amount), "USDC transfer failed");

    // Calculate fund shares based on investment amount
    uint256 shares = calculateFundShares(fundId, amount);

    // Mint fund shares to investor
    _mintFundShares(msg.sender, fundId, shares);

    emit FundInvestment(msg.sender, fundId, amount, shares);
}
```

### Treasury Investments

```solidity
function investInTreasury(uint256 treasuryId, uint256 amount) external {
    IERC20 usdc = IERC20(usdcAddresses[block.chainid]);

    // Transfer USDC from investor to contract
    require(usdc.transferFrom(msg.sender, address(this), amount), "USDC transfer failed");

    // Calculate treasury securities based on investment amount
    uint256 securities = calculateTreasurySecurities(treasuryId, amount);

    // Mint treasury securities to investor
    _mintTreasurySecurities(msg.sender, treasuryId, securities);

    emit TreasuryInvestment(msg.sender, treasuryId, amount, securities);
}
```

---

## Income Distribution

### Rental Income Distribution

```solidity
function distributeRentalIncome(uint256 propertyId, address[] calldata investors, uint256[] calldata amounts) external onlyOwner {
    IERC20 usdc = IERC20(usdcAddresses[block.chainid]);

    require(investors.length == amounts.length, "Array length mismatch");

    for (uint256 i = 0; i < investors.length; i++) {
        require(usdc.transfer(investors[i], amounts[i]), "Rental distribution failed");
        emit RentalDistribution(investors[i], propertyId, amounts[i]);
    }
}
```

### Dividend Distribution

```solidity
function distributeDividends(uint256 fundId, address[] calldata investors, uint256[] calldata amounts) external onlyOwner {
    IERC20 usdc = IERC20(usdcAddresses[block.chainid]);

    require(investors.length == amounts.length, "Array length mismatch");

    for (uint256 i = 0; i < investors.length; i++) {
        require(usdc.transfer(investors[i], amounts[i]), "Dividend distribution failed");
        emit DividendDistribution(investors[i], fundId, amounts[i]);
    }
}
```

### Interest Distribution

```solidity
function distributeInterest(uint256 treasuryId, address[] calldata investors, uint256[] calldata amounts) external onlyOwner {
    IERC20 usdc = IERC20(usdcAddresses[block.chainid]);

    require(investors.length == amounts.length, "Array length mismatch");

    for (uint256 i = 0; i < investors.length; i++) {
        require(usdc.transfer(investors[i], amounts[i]), "Interest distribution failed");
        emit InterestDistribution(investors[i], treasuryId, amounts[i]);
    }
}
```

---

## Cross-Chain Transfers

### CCTP V2 Integration

```solidity
interface ICCTP {
    function depositForBurn(uint256 amount, uint32 destinationDomain, bytes32 mintRecipient, address burnToken) external;
    function receiveMessage(bytes calldata message, bytes calldata attestation) external;
}

function initiateCrossChainTransfer(uint256 amount, uint32 destinationDomain, bytes32 mintRecipient) external {
    IERC20 usdc = IERC20(usdcAddresses[block.chainid]);
    ICCTP cctp = ICCTP(cctpAddresses[block.chainid]);

    // Transfer USDC from user to contract
    require(usdc.transferFrom(msg.sender, address(this), amount), "USDC transfer failed");

    // Approve CCTP to burn USDC
    require(usdc.approve(address(cctp), amount), "USDC approval failed");

    // Initiate cross-chain transfer
    cctp.depositForBurn(amount, destinationDomain, mintRecipient, address(usdc));

    emit CrossChainTransferInitiated(msg.sender, amount, destinationDomain);
}
```

---

## Multi-Chain Portfolio Management

### Portfolio Aggregation

```solidity
struct PortfolioData {
    uint256 totalValue;
    uint256 realEstateValue;
    uint256 fundValue;
    uint256 treasuryValue;
    uint256[] networkValues;
}

function getPortfolioValue(address investor) external view returns (PortfolioData memory) {
    PortfolioData memory portfolio;

    // Aggregate values across all networks
    for (uint256 i = 0; i < supportedNetworks.length; i++) {
        uint256 networkId = supportedNetworks[i];
        uint256 networkValue = getNetworkPortfolioValue(investor, networkId);
        portfolio.networkValues.push(networkValue);
        portfolio.totalValue += networkValue;
    }

    return portfolio;
}
```

### Cross-Chain Balance Tracking

```solidity
mapping(address => mapping(uint256 => uint256)) public crossChainBalances;

function updateCrossChainBalance(address investor, uint256 networkId, uint256 balance) external onlyOwner {
    crossChainBalances[investor][networkId] = balance;
    emit CrossChainBalanceUpdated(investor, networkId, balance);
}

function getTotalUSDCBalance(address investor) external view returns (uint256) {
    uint256 totalBalance = 0;

    for (uint256 i = 0; i < supportedNetworks.length; i++) {
        totalBalance += crossChainBalances[investor][supportedNetworks[i]];
    }

    return totalBalance;
}
```

---

## Security Considerations

### Access Control

```solidity
modifier onlyVerifiedInvestor() {
    require(kycVerified[msg.sender], "KYC verification required");
    require(onchainIdExists[msg.sender], "OnchainID required");
    _;
}

modifier onlyOwner() {
    require(msg.sender == owner, "Only owner");
    _;
}
```

### Reentrancy Protection

```solidity
import "@openzeppelin/contracts/security/ReentrancyGuard.sol";

contract CircleXFinance is ReentrancyGuard {
    function investInProperty(uint256 propertyId, uint256 amount) external nonReentrant onlyVerifiedInvestor {
        // Investment logic
    }
}
```

### Input Validation

```solidity
function investInProperty(uint256 propertyId, uint256 amount) external {
    require(propertyId > 0, "Invalid property ID");
    require(amount > 0, "Amount must be greater than 0");
    require(amount >= minimumInvestment, "Below minimum investment");
    require(amount <= maximumInvestment, "Above maximum investment");

    // Investment logic
}
```

---

## Gas Optimization

### Batch Operations

```solidity
function batchInvest(uint256[] calldata propertyIds, uint256[] calldata amounts) external {
    require(propertyIds.length == amounts.length, "Array length mismatch");

    uint256 totalAmount = 0;
    for (uint256 i = 0; i < amounts.length; i++) {
        totalAmount += amounts[i];
    }

    IERC20 usdc = IERC20(usdcAddresses[block.chainid]);
    require(usdc.transferFrom(msg.sender, address(this), totalAmount), "USDC transfer failed");

    for (uint256 i = 0; i < propertyIds.length; i++) {
        _processInvestment(propertyIds[i], amounts[i]);
    }
}
```

### Gas-Efficient Transfers

```solidity
function distributeIncome(address[] calldata investors, uint256[] calldata amounts) external {
    IERC20 usdc = IERC20(usdcAddresses[block.chainid]);

    // Calculate total amount first
    uint256 totalAmount = 0;
    for (uint256 i = 0; i < amounts.length; i++) {
        totalAmount += amounts[i];
    }

    // Single approval for total amount
    require(usdc.approve(address(this), totalAmount), "Approval failed");

    // Batch transfers
    for (uint256 i = 0; i < investors.length; i++) {
        require(usdc.transferFrom(address(this), investors[i], amounts[i]), "Transfer failed");
    }
}
```

---

## Best Practices

### Error Handling

```solidity
function investInProperty(uint256 propertyId, uint256 amount) external {
    try this._processInvestment(propertyId, amount) {
        emit InvestmentSuccess(msg.sender, propertyId, amount);
    } catch Error(string memory reason) {
        emit InvestmentFailed(msg.sender, propertyId, amount, reason);
        revert(reason);
    } catch {
        emit InvestmentFailed(msg.sender, propertyId, amount, "Unknown error");
        revert("Investment failed");
    }
}
```

### Event Logging

```solidity
event InvestmentMade(address indexed investor, uint256 indexed propertyId, uint256 amount, uint256 shares);
event IncomeDistributed(address indexed investor, uint256 amount, string incomeType);
event CrossChainTransfer(address indexed investor, uint256 amount, uint32 destinationDomain);

function investInProperty(uint256 propertyId, uint256 amount) external {
    // Investment logic

    emit InvestmentMade(msg.sender, propertyId, amount, shares);
}
```

---

## Troubleshooting

### Common Issues

#### USDC Transfer Failed

- **Insufficient Balance**: Ensure sufficient USDC balance
- **Insufficient Allowance**: Check USDC allowance
- **Contract Paused**: Check if contract is paused
- **Network Issues**: Verify network connectivity

#### Cross-Chain Transfer Issues

- **CCTP Service**: Check CCTP service status
- **Attestation Delays**: Wait for attestation generation
- **Network Congestion**: Try during lower activity
- **Gas Issues**: Ensure sufficient gas for transactions

### Support Resources

- 📧 **Email Support**: [support@circlex.finance](mailto:support@circlex.finance)
- 💬 **Discord Community**: [Join our Discord](https://discord.gg/circlexfinance)
- 📖 **Documentation**: Comprehensive guides and FAQs
- 🐦 **Twitter**: [@circlexfinance](https://twitter.com/circlexfinance)

---

## Next Steps

After understanding USDC integration:

1. **Review Smart Contracts**: Examine CircleX Finance smart contracts
2. **Test Integration**: Test USDC integration in development
3. **Implement Features**: Implement USDC features in your application
4. **Monitor Performance**: Monitor USDC transaction performance

---

**Ready to integrate?** [View our smart contracts](https://github.com/nagatejakachapuram/Circle-Finance) and start building with CircleX Finance!
