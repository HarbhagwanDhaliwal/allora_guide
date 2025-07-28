# 🧠 Allora Topic Creation Guide

Welcome to the Allora Network! This guide walks you through setting up your environment and creating a **Topic** using the latest CLI tools.

> ⚠️ **Current Limitations:**  
> Topic creation is **permissioned** during testnet phase. If not whitelisted, you'll encounter:  
> `failed to execute message; message index: 0: not permitted to create topic`  
> This restriction will be lifted when Allora goes **permissionless** on mainnet.

---

## 🛠️ Installation Guide

### 1. Install Go (v1.22.4)
```bash
sudo rm -rf /usr/local/go
curl -L https://go.dev/dl/go1.22.4.linux-amd64.tar.gz | sudo tar -xzf - -C /usr/local
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile
echo 'export PATH=$PATH:$(go env GOPATH)/bin' >> $HOME/.bash_profile
source $HOME/.bash_profile
go version
```

### 2. Install Allora CLI (v0.12.1)
```bash
git clone https://github.com/allora-network/allora-chain.git
cd allora-chain
git checkout v0.12.1
make all
allorad version
```

---

## 🔐 Wallet Management

| Command | Description |
|---------|-------------|
| `allorad keys add mywallet` | Create new wallet |
| `allorad keys add mywallet --recover` | Recover existing wallet |
| `allorad keys list` | View all wallets |

**Get Testnet Tokens:**  
👉 [Allora Testnet Faucet](https://faucet.testnet.allora.network/)

---

## 🚀 Topic Creation (Post-Permissionless)

### Basic Command Structure
```bash
allorad tx emissions create-topic \
  [creator_address] \
  "[topic_description]" \
  [loss_method] \
  [epoch_length] \
  [ground_truth_lag] \
  [parameters...] \
  --from [your_wallet] \
  --node https://rpc.ankr.com/allora_testnet \
  --chain-id allora-testnet-1 \
  --fees 2000000uallo
```

### Key Parameters Explained
| Parameter | Example Value | Purpose |
|-----------|---------------|---------|
| `metadata` | "ETH Price Prediction" | Human-readable description |
| `loss_method` | "mse" | Mean Squared Error metric |
| `epoch_length` | 3600 | Epoch duration in seconds |
| `p_norm` | 3 | Prediction norm value |
| `epsilon` | 0.001 | Exploration factor |

---

## 💰 Funding Your Topic
```bash
allorad tx emissions fund-topic \
  [your_address] \
  [topic_id] \
  1000000uallo \
  "inference funds" \
  --from [your_wallet] \
  --node https://rpc.ankr.com/allora_testnet \
  --chain-id allora-testnet-1 \
  --fees 200000uallo
```

---

## 📝 Whitelist Management

### Add Worker
```bash
allorad tx emissions add-to-topic-worker-whitelist \
  [your_address] \
  [worker_address] \
  [topic_id] \
  [standard_flags...]
```

### Add Reputer
```bash
allorad tx emissions add-to-topic-reputer-whitelist \
  [your_address] \
  [reputer_address] \
  [topic_id] \
  [standard_flags...]
```

---

## 🔍 Useful Commands Cheat Sheet

```bash
# Register participant
allorad tx emissions register [participant_type] [address] [topic_id]

# Delegate stake
allorad tx emissions delegate-stake [delegator] [reputer] [amount]

# Get help
allorad tx emissions -h
```

---
