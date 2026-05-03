# Bitcoin Wallet Mining Rewards Setup Guide

## Overview
This guide helps you set up the Bitcoin Wallet app to receive and manage mining rewards from your mining operations.

---

## Phase 1: Build & Install the Wallet

### Prerequisites
- Ubuntu 22.04 LTS (or similar Linux)
- Git
- Java 11 SDK
- Gradle 4.4-6.9.x
- Android device with USB debugging enabled

### Installation Steps

```bash
# 1. Install dependencies
sudo apt install git gradle openjdk-11-jdk

# 2. Setup Android SDK
mkdir ~/android-sdk
export ANDROID_HOME=~/android-sdk
# Download Android SDK Tools from: https://developer.android.com/studio/index.html#command-tools
# Extract to $ANDROID_HOME/

# 3. Clone repository
git clone -b main https://github.com/Percival1997/bitcoin-wallet.git
cd bitcoin-wallet

# 4. Build development version (Testnet - for testing first)
gradle clean test :wallet:assembleDevDebug

# Output: wallet/build/outputs/apk/dev/debug/bitcoin-wallet-dev-debug.apk
```

### Install on Android Device

```bash
# Enable USB debugging on your Android device first!
gradle :wallet:installDevDebug
```

---

## Phase 2: Generate Your Mining Reward Address

### In the Wallet App:

1. **Open Bitcoin Wallet** on your Android device
2. **Tap "Request coins"** button
3. **Your Bitcoin address will display** (looks like: `1A1z7agoat4R...`)
4. **Screenshot or copy** this address

### Address Examples:
- **Mainnet address**: `1G2Y2jP5YFZ5RGk2PXaeWwbeA5y1ZtFhoL` (real Bitcoin)
- **Testnet address**: Starts with `m` or `n` (test coins only)

---

## Phase 3: Test with Testnet (IMPORTANT FIRST STEP!)

### Why Test First?
- Testnet uses free test Bitcoin
- No real money risk
- Verify your setup works
- Confirm wallet receives funds correctly

### Get Test Bitcoin:
1. Copy your Testnet address from the dev wallet
2. Visit a testnet faucet: https://testnet-faucet.mempool.co/
3. Paste your address and request test coins
4. Wait 5-10 minutes
5. Check wallet balance

### Verify Transaction:
- Open wallet app
- You should see incoming transaction
- Balance updates automatically
- Explore the app features

---

## Phase 4: Setup for Mainnet Mining

### Build Production Version:

```bash
# Build production version (real Bitcoin)
gradle clean test :wallet:assembleProdRelease

# Output: wallet/build/outputs/apk/prod/release/bitcoin-wallet-prod-release-unsigned.apk

# Note: Unsigned APK needs signing before installation
# For development, you can sign with your debug key or create a release key
```

### Get Your Mainnet Address:

1. Install production version on separate Android device (or factory reset test device)
2. Open Bitcoin Wallet
3. Tap "Request coins"
4. **Copy your Mainnet address** (starts with `1` or `3`)
5. **Save this address securely** - you'll use it for mining rewards

---

## Phase 5: Connect to Mining Pool

### Popular Mining Pools:
- **Slush Pool**: https://slushpool.com/
- **F2Pool**: https://www.f2pool.com/
- **AntPool**: https://www.antpool.com/
- **Braiins Pool**: https://braiins.com/pool

### Mining Pool Setup:

1. **Create account** on your chosen mining pool
2. **Add your Bitcoin address** as payout address:
   - Pool settings → Payout address
   - Paste your Mainnet wallet address
3. **Configure your mining hardware**:
   - ASIC miner (Antminer S19 Pro, etc.)
   - Mining software (cgminer, sgminer, etc.)
4. **Start mining**
5. **Pool sends rewards** to your wallet address

### Example Pool Configuration:
```
Payout Address: [Your Mainnet Address from Wallet]
Payout Threshold: 0.001 BTC (or pool's minimum)
Confirmation: Your wallet will receive funds automatically
```

---

## Phase 6: Monitor Mining Rewards

### In Wallet App:

1. **Open Bitcoin Wallet**
2. **Home screen shows total balance**
3. **Transaction history** shows all incoming mining rewards
4. **Each reward** appears as incoming transaction
5. **Balance updates** automatically

### Wallet Storage:
- **Mainnet file**: `/data/data/de.schildbach.wallet/files/wallet-protobuf`
- **Automatic backups**: `/data/data/de.schildbach.wallet/files/key-backup-protobuf`
- **Manual backups**: Export to Google Drive anytime

---

## Phase 7: Distributing Rewards to Community

### Once You Have Mining Rewards:

1. **Tap "Send coins"** in wallet
2. **Enter recipient's Bitcoin address**
3. **Enter amount to send**
4. **Confirm transaction**
5. **Blockchain confirms** (usually 10-30 minutes)

### For Your 100-Person Community:
```
Option 1: Manual Distribution
- Send individual transactions
- Transparent, but time-consuming

Option 2: Batch Payments
- Send multiple transactions in series
- Document all distributions

Option 3: Smart Contract/Script
- Automate payments (advanced)
- Use Bitcoin scripting
```

---

## Important Security Notes

⚠️ **CRITICAL:**
- **NEVER share your private keys**
- **BACKUP your wallet regularly**
- **Test on Testnet first**
- **Use strong device password**
- **Enable USB debugging only when needed**
- **Keep Android device updated**

### Backup Locations:
- Automatic: `/data/data/de.schildbach.wallet/files/key-backup-protobuf`
- Manual: Export through wallet settings to Google Drive
- Recovery guide: See `wallet/README.recover.md`

---

## Troubleshooting

### Mining rewards not appearing?
1. Check your address is correct in pool settings
2. Wait 1-2 block confirmations (~10-20 minutes)
3. Verify on blockchain explorer: https://blockchain.com/
4. Check pool dashboard for payment status

### Wallet not receiving transactions?
1. Ensure you're on Mainnet (not Testnet)
2. Verify address is correct
3. Check device has internet connection
4. Restart wallet app

### Build errors?
1. Ensure Java 11 is installed: `java -version`
2. Update Gradle: `gradle wrapper --gradle-version 6.9`
3. Clear build cache: `gradle clean`
4. Check Android SDK is properly configured

---

## Next Steps

1. ✅ Build wallet (dev version - Testnet)
2. ✅ Test with testnet coins
3. ✅ Build wallet (production version - Mainnet)
4. ✅ Get your Mainnet address
5. ✅ Setup mining pool account
6. ✅ Configure payout address to your wallet
7. ✅ Start mining
8. ✅ Monitor rewards in wallet
9. ✅ Plan community distribution
10. ✅ Execute distribution to 100-person community

---

## Resources

- **Bitcoin Wallet Project**: https://github.com/bitcoin-wallet/bitcoin-wallet
- **Blockchain Explorer**: https://blockchain.com/
- **Testnet Faucet**: https://testnet-faucet.mempool.co/
- **bitcoinj Documentation**: https://bitcoinj.org/
- **Mining Hardware**: https://www.asicminervalue.com/

---

## Questions?

For issues specific to:
- **Wallet app**: Check wallet/README.md
- **Mining setup**: Consult your pool's documentation
- **Bitcoin basics**: Visit https://bitcoin.org/

Good luck with your mining operation! 🚀⛏️

