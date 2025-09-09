# Wallet Connection Guide

This guide covers how to connect your wallet to CircleX Finance and the supported wallet types.

---

## Supported Wallets

CircleX Finance supports a wide range of wallet types to ensure accessibility for all users:

### Browser Extension Wallets

- **MetaMask** - Most popular Ethereum wallet
- **Coinbase Wallet** - User-friendly wallet with built-in DEX
- **Brave Wallet** - Built into Brave browser
- **Trust Wallet** - Multi-chain wallet with DeFi features

### Mobile Wallets

- **WalletConnect** - Universal mobile wallet connector
- **MetaMask Mobile** - Mobile version of MetaMask
- **Trust Wallet Mobile** - Mobile app with DeFi integration
- **Coinbase Wallet Mobile** - Mobile version of Coinbase Wallet

### Hardware Wallets

- **Ledger** - Hardware security for maximum protection
- **Trezor** - Open-source hardware wallet
- **KeepKey** - Hardware wallet with large display

### Other Wallets

- **Rainbow** - Beautiful, user-friendly wallet
- **Argent** - Smart wallet with social recovery
- **Gnosis Safe** - Multi-signature wallet for teams

---

## Connection Process

### Step 1: Access the Platform

1. **Visit CircleX Finance**: Go to [circlefinancex.vercel.app](https://circlefinancex.vercel.app/)
2. **Click "Connect Wallet"**: Located in the top-right corner
3. **Select Wallet Type**: Choose from the supported options

### Step 2: Authorize Connection

#### For Browser Extensions

1. **Wallet Popup**: Your wallet extension will open
2. **Review Permissions**: Check what CircleX Finance is requesting
3. **Approve Connection**: Click "Connect" or "Approve"
4. **Select Account**: Choose which account to connect (if multiple)

#### For Mobile Wallets

1. **QR Code**: Scan the displayed QR code with your mobile wallet
2. **Wallet App**: Open your wallet app and scan
3. **Approve Connection**: Confirm the connection in your wallet
4. **Return to Browser**: You'll be redirected back to the platform

#### For Hardware Wallets

1. **Select Hardware Wallet**: Choose your hardware wallet type
2. **Connect Device**: Ensure your device is connected and unlocked
3. **Select Account**: Choose the account to connect
4. **Confirm on Device**: Approve the connection on your hardware wallet

### Step 3: Verify Connection

After successful connection, you should see:

- ✅ **Wallet Address**: Your wallet address displayed in the interface
- ✅ **Network Status**: Confirmation you're on a supported network
- ✅ **Connection Status**: "Connected" indicator in the UI

---

## Supported Networks

CircleX Finance supports USDC across multiple blockchain networks:

### Ethereum Mainnet

- **Network ID**: 1
- **USDC Address**: `0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48`
- **RPC URL**: `https://mainnet.infura.io/v3/YOUR_PROJECT_ID`
- **Block Explorer**: [Etherscan](https://etherscan.io)

### Base

- **Network ID**: 8453
- **USDC Address**: `0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913`
- **RPC URL**: `https://mainnet.base.org`
- **Block Explorer**: [BaseScan](https://basescan.org)

### Polygon

- **Network ID**: 137
- **USDC Address**: `0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174`
- **RPC URL**: `https://polygon-rpc.com`
- **Block Explorer**: [PolygonScan](https://polygonscan.com)

### Solana

- **Network ID**: 101
- **USDC Address**: `EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v`
- **RPC URL**: `https://api.mainnet-beta.solana.com`
- **Block Explorer**: [Solscan](https://solscan.io)

---

## Network Switching

### Automatic Network Detection

CircleX Finance automatically detects your current network and:

- **Shows Network Status**: Displays current network in the UI
- **Suggests Switching**: Prompts to switch if on unsupported network
- **Provides Instructions**: Guides you through network switching

### Manual Network Switching

#### For MetaMask

1. **Click Network**: Click on the network name in MetaMask
2. **Select Network**: Choose the desired network from the list
3. **Add Custom Network**: If not listed, add the network manually
4. **Confirm Switch**: Approve the network switch

#### For Other Wallets

1. **Wallet Settings**: Open your wallet settings
2. **Network Management**: Navigate to network settings
3. **Add Network**: Add CircleX Finance supported networks
4. **Switch Network**: Select the desired network

### Adding Custom Networks

If your wallet doesn't have CircleX Finance networks pre-configured:

#### Ethereum Mainnet

```
Network Name: Ethereum Mainnet
RPC URL: https://mainnet.infura.io/v3/YOUR_PROJECT_ID
Chain ID: 1
Currency Symbol: ETH
Block Explorer: https://etherscan.io
```

#### Base

```
Network Name: Base
RPC URL: https://mainnet.base.org
Chain ID: 8453
Currency Symbol: ETH
Block Explorer: https://basescan.org
```

#### Polygon

```
Network Name: Polygon
RPC URL: https://polygon-rpc.com
Chain ID: 137
Currency Symbol: MATIC
Block Explorer: https://polygonscan.com
```

---

## Security Best Practices

### Wallet Security

- **Use Hardware Wallets**: For large amounts, use hardware wallets
- **Keep Private Keys Safe**: Never share your private keys
- **Enable 2FA**: Use two-factor authentication where available
- **Regular Updates**: Keep your wallet software updated

### Connection Security

- **Verify Website**: Always ensure you're on the correct website
- **Check Permissions**: Review what permissions you're granting
- **Disconnect When Done**: Disconnect your wallet when not using the platform
- **Monitor Transactions**: Regularly check your transaction history

### Network Security

- **Use Official RPCs**: Only use official RPC endpoints
- **Verify Network Details**: Double-check network information before adding
- **Test with Small Amounts**: Test new networks with small amounts first
- **Keep Network Info**: Save network configuration for future use

---

## Troubleshooting

### Common Issues

#### Wallet Not Detected

- **Check Extension**: Ensure wallet extension is installed and enabled
- **Refresh Page**: Try refreshing the browser page
- **Clear Cache**: Clear browser cache and cookies
- **Restart Browser**: Close and reopen your browser

#### Connection Failed

- **Check Network**: Ensure you're on a supported network
- **Wallet Unlocked**: Make sure your wallet is unlocked
- **Permissions**: Check if you've granted necessary permissions
- **Try Different Wallet**: Test with a different wallet type

#### Transaction Failed

- **Insufficient Gas**: Ensure you have enough ETH for gas fees
- **Network Congestion**: Try during lower activity periods
- **Wallet Issues**: Check wallet connectivity and status
- **Retry Transaction**: Attempt the transaction again

#### Network Issues

- **RPC Problems**: Try switching to a different RPC endpoint
- **Network Outage**: Check if the network is experiencing issues
- **Wallet Settings**: Verify network configuration in wallet
- **Contact Support**: Reach out for technical assistance

### Support Resources

- 📧 **Email Support**: [support@circlex.finance](mailto:support@circlex.finance)
- 💬 **Discord Community**: [Join our Discord](https://discord.gg/circlexfinance)
- 📖 **Documentation**: Comprehensive guides and FAQs
- 🐦 **Twitter**: [@circlexfinance](https://twitter.com/circlexfinance)

---

## Next Steps

After successfully connecting your wallet:

1. **Complete KYC**: Start the identity verification process
2. **Create OnchainID**: Set up your decentralized identity
3. **Explore Features**: Browse available investment options
4. **Start Investing**: Begin building your tokenized portfolio

---

**Ready to connect?** [Connect your wallet now](https://circlefinancex.vercel.app/) and start your journey with CircleX Finance!
