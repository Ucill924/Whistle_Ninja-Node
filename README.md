# Whistle Node Setup Tutorial

Complete guide to running a Whistle Node and earning rewards.

## 📋 Server Requirements

### Minimum Requirements
- **CPU**: 4 Core
- **RAM**: 8 GB
- **Storage**: 20 GB SSD
- **OS**: Ubuntu 24.04 / Debian 12
- **Location**: Europe or US (recommended)

### Supported VPS Providers
- Contabo
- Hetzner
- DigitalOcean
- Vultr
- AWS / GCP (other options)

## 💰 Required Assets

| Asset | Amount | Estimated Cost ||
| $WHISTLE Token | 100 WHISTLE | ~$1 |

**Token Address**: `6Hb2xgEhyN9iVVH3cgSxYjfN774ExzgiCftwiWdjpump`

> ⚠️ **Note**: Tokens can be unstaked anytime with no lock period.

## 🚀 Setup Guide

### Step 1: Stake Tokens

1. Visit [https://earn.whistle.ninja/](https://earn.whistle.ninja/)
2. Connect your Solana wallet
3. Stake 100 WHISTLE to register your node
4. Save your wallet address for node setup

### Step 2: VPS Setup

#### 2.1 Update Dependencies
```bash
sudo apt update && sudo apt upgrade -y
```

#### 2.2 Install Node.js
```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs
```

Verify installation:
```bash
node --version
npm --version
```

#### 2.3 Install PM2
```bash
sudo npm install -g pm2
```

#### 2.4 Install WebSocket Library
```bash
npm install -g ws
```

### Step 3: Setup Whistle Node

#### 3.1 Create Whistle Folder
```bash
mkdir -p ~/whistle
cd ~/whistle
```

#### 3.2 Download Node Script
```bash
curl -sL earn.whistle.ninja/node.js -o node.js
```

#### 3.3 Run Node

Replace `your_wallet_address` with your Solana wallet address:
```bash
WALLET=<your_wallet_address> pm2 start node.js --name whistle
```

**Example**:
```bash
WALLET=7XaB3Cd4Ef5Gh6Ij7Kl8Mn9Op0Qr1St2Uv3Wx4Yz5 pm2 start node.js --name whistle
```

#### 3.4 Save & Enable Auto-Start
```bash
pm2 save
pm2 startup
```

Run the command that appears after `pm2 startup` (usually starts with `sudo env PATH=...`)

## 📊 Monitoring Node

### Check Node Status
```bash
pm2 status
```

### Check Logs
```bash
pm2 logs whistle --lines 30
```

For live monitoring:
```bash
pm2 logs whistle
```

### Management Commands

| Command | Description |
|---------|-------------|
| `pm2 restart whistle` | Restart node |
| `pm2 stop whistle` | Stop node |
| `pm2 delete whistle` | Remove node from PM2 |
| `pm2 monit` | Real-time monitoring dashboard |

## 💡 Tips & Troubleshooting

### Optimizing Rewards

- Keep your node online 24/7
- More requests processed = more rewards
- Monitor logs regularly to ensure node is running properly

### Common Issues

**Node won't start / Missing ws module**:
```bash
npm install -g ws
pm2 restart whistle
```

**Check error logs**:
```bash
pm2 logs whistle --err
```

**Update node script**:
```bash
cd ~/whistle
pm2 stop whistle
curl -sL earn.whistle.ninja/node.js -o node.js
pm2 restart whistle
```

**Check firewall** (if needed):
```bash
sudo ufw status
sudo ufw allow 22/tcp
```

## 🔐 Security Best Practices

1. **Never share your wallet private key**
2. Use SSH key authentication
3. Update system regularly
4. Backup wallet address and configuration
5. Monitor server activity routinely

## 📈 Monitoring Rewards

Check your rewards and node status on the dashboard:
[https://earn.whistle.ninja/](https://earn.whistle.ninja/)

## ❓ Support

- Website: [https://whistle.ninja/](https://whistle.ninja/)
- Dashboard: [https://earn.whistle.ninja/](https://earn.whistle.ninja/)

---

**Disclaimer**: Make sure you understand crypto investment risks. Do your own research (DYOR) before staking tokens.
