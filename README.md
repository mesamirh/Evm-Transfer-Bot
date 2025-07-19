# 🤖 Evm-Transfer Bot

A real-time Ethereum token monitoring and auto-transfer bot that automatically detects incoming ERC-20 tokens and transfers them to a specified recipient address.

## ✨ Features

- **24/7 Real-time Monitoring** - Continuously monitors your wallet for incoming ERC-20 token transfers
- **Automatic Token Transfer** - Automatically transfers detected tokens after a configurable delay
- **Token Information Display** - Shows token name, symbol, and formatted balance
- **Custom Token Support** - Monitor specific token contracts manually
- **Error Recovery** - Auto-restarts on errors with intelligent retry logic
- **Heartbeat Monitoring** - Regular status updates to confirm the bot is active
- **Duplicate Prevention** - Ensures each transaction is processed only once

## 🚀 How It Works

1. **Monitoring**: The bot listens for ERC-20 Transfer events where your wallet is the recipient
2. **Detection**: When an incoming token is detected, it immediately shows token details
3. **Delay**: Waits for the configured time period (1 minute by default)
4. **Transfer**: Automatically transfers the entire token balance to your specified recipient address
5. **Confirmation**: Provides transaction hash and success confirmation

## 📋 Prerequisites

- Node.js (v16 or higher)
- An Ethereum wallet private key
- Access to an Ethereum RPC provider
- A recipient wallet address for token transfers

## 🛠️ Installation

1. **Clone or download the project files**

   ```bash
   git clone https://github.com/mesamirh/Evm-Transfer-Bot.git
   cd Evm-Transfer-Bot
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Configure environment variables:**
   Create a `.env` file in the project root:
   ```env
   PRIVATE_KEY=your_private_key_here
   RPC_URL=https://eth1.lava.build
   RECIPIENT_ADDRESS=0xYourRecipientAddressHere
   CUSTOM_TOKENS=0xTokenAddress1,0xTokenAddress2,0xTokenAddress3
   ```

## ⚙️ Configuration

### Required Environment Variables

| Variable            | Description                                   | Example                         |
| ------------------- | --------------------------------------------- | ------------------------------- |
| `PRIVATE_KEY`       | Your wallet's private key (without 0x prefix) | `5dc578f0c46add36290e2cd2...`   |
| `RPC_URL`           | Ethereum RPC endpoint                         | `https://eth1.lava.build`       |
| `RECIPIENT_ADDRESS` | Address to send tokens to                     | `0x742d35Cc6Ab6B3c4848b866C...` |

### Optional Environment Variables

| Variable        | Description                                        | Default |
| --------------- | -------------------------------------------------- | ------- |
| `CUSTOM_TOKENS` | Comma-separated list of token addresses to monitor | Empty   |

## 🏃‍♂️ Usage

1. **Start the bot:**

   ```bash
   node main.js
   ```

2. **Expected output:**

   ```
   🤖 Auto-Transfer Bot Started
   📍 Monitoring wallet: 0x67b25dcf85301a786a225f1d89dd48fb7a0d602e
   📤 Auto-transfer to: 0xYourRecipientAddress
   ⚡ Transfer delay: 1 minute

   🔍 Monitoring for incoming tokens...
   Press Ctrl+C to stop

   ✅ Bot is now running 24/7...
   ```

3. **When tokens are received:**
   ```
   📨 Incoming token detected:
      Token: 0xA0b86a33E6441b8F73EaacD6D2A5b8cDaE92cf7B
      TxHash: 0x123abc...
      Wrapped Bitcoin (WBTC)
   ⏱️  Waiting 1 minute before auto-transfer...
   🔄 Transferring 0.001 WBTC (Wrapped Bitcoin)...
   ✅ Transferred 0.001 WBTC!
      TxHash: 0x456def...
   ```

## 🔧 Customization

### Change Transfer Delay

To modify the transfer delay, edit the timeout value in `main.js`:

```javascript
// Wait 1 minute before transferring (60000ms)
await new Promise((resolve) => setTimeout(resolve, 60000));
```

### Add Custom Tokens

Add token contract addresses to your `.env` file:

```env
CUSTOM_TOKENS=0xA0b86a33E6441b8F73EaacD6D2A5b8cDaE92cf7B,0xdAC17F958D2ee523a2206206994597C13D831ec7
```

## 🛡️ Security Features

- **Anti-debugging protection** - Prevents analysis in debugging environments
- **Environment validation** - Ensures all required variables are present
- **Error handling** - Graceful error recovery and restart mechanisms
- **Transaction deduplication** - Prevents processing the same transaction multiple times

## ⚠️ Important Notes

- **Private Key Security**: Never share your private key or commit it to version control
- **Test First**: Test on testnet before using on mainnet
- **Gas Fees**: Ensure the monitored wallet has sufficient ETH for gas fees
- **RPC Limits**: Some RPC providers have rate limits; adjust accordingly
- **Network**: This bot is configured for Ethereum mainnet by default

## 📊 Monitoring & Logs

The bot provides several types of status updates:

- **Heartbeat**: Every 5 minutes, confirms the bot is active
- **Incoming Detection**: Immediate notification when tokens are received
- **Transfer Status**: Success/failure status for each transfer attempt
- **Error Logs**: Detailed error information for troubleshooting

## 🔄 Auto-Recovery

The bot includes automatic recovery mechanisms:

- **Auto-restart**: Restarts after 30 seconds if a fatal error occurs
- **Connection Recovery**: Handles RPC connection issues gracefully
- **State Management**: Maintains processed transaction history to prevent duplicates

## 🛑 Stopping the Bot

To stop the bot, press `Ctrl+C` in the terminal. The bot will shut down gracefully.

## 📝 Dependencies

- **ethers** - Ethereum interaction library
- **dotenv** - Environment variable management
- **chalk** - Terminal color output
- **ora** - Loading spinners
- **node-fetch** - HTTP requests

## 🐛 Troubleshooting

### Common Issues

1. **"Missing environment variables"**

   - Ensure your `.env` file contains all required variables

2. **"Failed to connect to RPC"**

   - Check your `RPC_URL` and internet connection

3. **"Insufficient funds for gas"**

   - Ensure your wallet has enough ETH for transaction fees

4. **Bot stops unexpectedly**
   - Check console logs for error messages
   - The bot should auto-restart after 30 seconds

### Support

For issues or questions, review the console logs for detailed error information.
