# KYC & OnchainID Setup

This comprehensive guide covers the **KYC (Know Your Customer)** verification process and **OnchainID** creation, which are mandatory requirements for accessing CircleX Finance's investment features.

---

## Overview

CircleX Finance implements a **compliance-first architecture** that requires:

1. **KYC Verification** - Identity verification with cryptographic signature
2. **OnchainID Creation** - Decentralized identity management
3. **Claim Integration** - Adding KYC claims to your on-chain identity

Without completing all three steps, you cannot access any investment features on the platform.

---

## KYC Verification Process

### What is KYC?

Know Your Customer (KYC) is a regulatory requirement that:

- **Verifies your identity** using government-issued documents
- **Ensures compliance** with anti-money laundering (AML) regulations
- **Provides cryptographic proof** of verification
- **Enables access** to regulated financial services

### Required Documents

You'll need to provide:

#### Primary Identification

- **Passport** (preferred) - International travel document
- **Driver's License** - Government-issued photo ID
- **National ID Card** - Government-issued identification

#### Secondary Verification

- **Proof of Address** - Utility bill, bank statement, or government correspondence
- **Selfie Verification** - Live photo for identity matching
- **Additional Documents** - May be requested based on jurisdiction

### KYC Process Steps

#### 1. Document Upload

- **Clear Photos**: Ensure all documents are clearly visible
- **Valid Information**: All information must be current and accurate
- **Format Requirements**: JPG, PNG, or PDF formats accepted
- **File Size**: Maximum 10MB per document

#### 2. Identity Verification

- **Document Validation**: Automated verification of document authenticity
- **Information Matching**: Cross-reference provided information
- **Liveness Detection**: Verify the selfie is from a live person
- **Facial Recognition**: Match selfie with ID photo

#### 3. Background Checks

- **Sanctions Screening**: Check against international sanctions lists
- **PEP Screening**: Politically Exposed Person verification
- **Adverse Media**: Review for negative news or associations
- **Risk Assessment**: Evaluate overall risk profile

#### 4. Approval Process

- **Automated Review**: Initial automated verification
- **Manual Review**: Human verification for complex cases
- **Approval Notification**: Email confirmation of verification status
- **Cryptographic Signature**: Generate verification proof

---

## OnchainID Creation

### What is OnchainID?

OnchainID is a **decentralized identity system** that:

- **Stores verified claims** on the blockchain
- **Enables privacy-preserving** verification
- **Integrates with ERC-3643** compliance framework
- **Manages access control** for investment features

### OnchainID Architecture

#### Identity Contract

- **Unique Address**: Each identity has a unique smart contract address
- **Claim Storage**: Stores verified claims and attestations
- **Access Control**: Manages permissions and access rights
- **Recovery Mechanisms**: Backup and recovery options

#### Claim Structure

```solidity
struct Claim {
    uint256 topic;           // Claim type (KYC, AML, etc.)
    uint256 scheme;          // Verification scheme
    address issuer;          // Claim issuer address
    uint256 signature;       // Cryptographic signature
    bytes data;              // Claim data
    string uri;              // Additional data URI
}
```

### Creating Your OnchainID

#### 1. Navigate to OnchainID

- **Access Point**: Available after KYC approval
- **Deployment Interface**: User-friendly deployment process
- **Gas Estimation**: Automatic gas fee calculation

#### 2. Deploy Identity Contract

- **Contract Creation**: Deploy your unique identity contract
- **Gas Payment**: Pay network fees for deployment
- **Verification**: Confirm successful deployment
- **Address Generation**: Receive your unique identity address

#### 3. Configure Recovery

- **Recovery Addresses**: Set up backup recovery addresses
- **Recovery Threshold**: Configure required confirmations
- **Time Delays**: Set recovery time delays for security
- **Testing**: Verify recovery mechanisms work correctly

#### 4. Verify Deployment

- **Contract Verification**: Confirm contract is properly deployed
- **Functionality Test**: Test basic identity functions
- **Access Verification**: Ensure you can manage your identity
- **Backup Storage**: Securely store recovery information

---

## Adding KYC Claims

### Claim Integration Process

#### 1. Navigate to Claims

- **Claims Section**: Access the claims management interface
- **Add Claim**: Select "Add KYC Claim" option
- **Verification**: Confirm your KYC status

#### 2. Submit KYC Claim

- **Claim Data**: Submit your KYC verification data
- **Cryptographic Proof**: Include verification signature
- **Issuer Information**: Specify claim issuer details
- **Expiration Date**: Set claim validity period

#### 3. Verify Claim Addition

- **On-Chain Verification**: Confirm claim is stored on-chain
- **Access Testing**: Test that claims enable feature access
- **Status Confirmation**: Verify claim status is active
- **Integration Complete**: Confirm full integration

### Claim Structure

```solidity
// KYC Claim Example
{
    topic: 1,                    // KYC claim type
    scheme: 1,                   // ECDSA signature scheme
    issuer: 0x...,              // CircleX Finance issuer address
    signature: 0x...,           // Cryptographic signature
    data: "KYC_VERIFIED",       // Claim data
    uri: "https://..."          // Additional verification data
}
```

---

## Access Control Integration

### ERC-3643 Compliance

CircleX Finance uses **ERC-3643** for access control:

- **Identity Verification**: Required for all investment features
- **Claim Validation**: On-chain verification of KYC status
- **Permission Management**: Granular access control
- **Compliance Reporting**: Audit-ready access logs

### Feature Access Matrix

| Feature               | KYC Required | OnchainID Required | Claim Required |
| --------------------- | ------------ | ------------------ | -------------- |
| Browse Properties     | ❌           | ❌                 | ❌             |
| View Property Details | ❌           | ❌                 | ❌             |
| Invest in Real Estate | ✅           | ✅                 | ✅             |
| Index Fund Investment | ✅           | ✅                 | ✅             |
| Treasury Investment   | ✅           | ✅                 | ✅             |
| CCTP V2 Bridge        | ✅           | ✅                 | ✅             |
| Portfolio Management  | ✅           | ✅                 | ✅             |

---

## Security Considerations

### Privacy Protection

- **Minimal Data Storage**: Only essential data is stored on-chain
- **Encrypted Claims**: Sensitive information is encrypted
- **Selective Disclosure**: Share only necessary information
- **Data Retention**: Clear data retention policies

### Recovery Mechanisms

- **Backup Recovery**: Multiple recovery addresses
- **Time Delays**: Security delays for recovery actions
- **Multi-Signature**: Optional multi-sig recovery
- **Emergency Procedures**: Clear emergency recovery process

### Best Practices

- **Secure Storage**: Safely store recovery information
- **Regular Backups**: Maintain current backups
- **Access Monitoring**: Monitor identity access
- **Update Procedures**: Keep recovery information current

---

## Troubleshooting

### Common Issues

#### KYC Verification Failed

- **Document Quality**: Ensure documents are clear and readable
- **Information Accuracy**: Verify all information is correct
- **Document Validity**: Ensure documents are current and valid
- **Contact Support**: Reach out for manual review

#### OnchainID Deployment Failed

- **Gas Fees**: Ensure sufficient ETH for gas
- **Network Congestion**: Try during lower activity periods
- **Wallet Issues**: Check wallet connectivity and permissions
- **Retry Process**: Attempt deployment again

#### Claims Not Adding

- **KYC Status**: Verify KYC is fully approved
- **OnchainID Status**: Confirm OnchainID is properly deployed
- **Network Issues**: Check network connectivity
- **Contact Support**: Reach out for technical assistance

### Support Resources

- 📧 **Email Support**: [support@circlex.finance](mailto:support@circlex.finance)
- 💬 **Discord Community**: [Join our Discord](https://discord.gg/circlexfinance)
- 📖 **Documentation**: Comprehensive guides and FAQs
- 🐦 **Twitter**: [@circlexfinance](https://twitter.com/circlexfinance)

---

## Next Steps

After completing KYC and OnchainID setup:

1. **Explore Investment Options**: Browse available properties and funds
2. **Set Up Portfolio**: Configure your investment preferences
3. **Start Investing**: Begin building your tokenized portfolio
4. **Monitor Performance**: Track your investments and returns

---

**Ready to complete your verification?** [Start the KYC process](https://circlefinancex.vercel.app/) and unlock access to CircleX Finance's investment features!
