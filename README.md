# 🧠 Allora Topic Creation Guide

Welcome! This repository walks you through setting up your environment and preparing to create a **Topic** on the Allora Network. It also includes a reference for using the topic creation command.

> ⚠️ **Important:** Topic creation is currently **permissioned** on the testnet and will only become fully **permissionless** after mainnet launch.  
> If you attempt to create a topic now, you may encounter:
>
> ```
> failed to execute message; message index: 0: not permitted to create topic
> ```

---

## 🚀 Install Allora CLI (v0.12.1)

### 1. Install Go (v1.22.4)

```bash
sudo rm -rf /usr/local/go
curl -L https://go.dev/dl/go1.22.4.linux-amd64.tar.gz | sudo tar -xzf - -C /usr/local
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile
echo 'export PATH=$PATH:$(go env GOPATH)/bin' >> $HOME/.bash_profile
source $HOME/.bash_profile
go version
```

### 2. Install the Allora CLI

```bash
git clone https://github.com/allora-network/allora-chain.git
cd allora-chain
git checkout v0.12.1
make all
allorad version
```

---

## 🔐 Wallet Setup

### Create a New Wallet

```bash
allorad keys add testkey
```

### Recover an Existing Wallet

```bash
allorad keys add <wallet_name> --recover
```

### List All Wallets

```bash
allorad keys list
```

---

## 💧 Request Testnet Tokens

Use the official faucet to request testnet tokens:  
👉 [https://faucet.testnet.allora.network/](https://faucet.testnet.allora.network/)

---

## 📌 Create a Topic (Once Permissionless)

### Example Command

```bash
allorad tx emissions create-topic \
"YOUR_WALLET_ADDRESS" \
"ETH Price Prediction (Encrypted) in 24 hours" \
"mse" \
3600 \
0 \
3 \
3 \
1 \
true \
0.001 \
0.1 \
0.25 \
0.25 \
0.25 \
false \
false \
--node https://rpc.ankr.com/allora_testnet \
--chain-id allora-testnet-1 \
--fees 2000000uallo
```

### Command Syntax Breakdown

```bash
allorad tx emissions create-topic \
[creator] \
[metadata] \
[loss_method] \
[epoch_length] \
[ground_truth_lag] \
[worker_submission_window] \
[p_norm] \
[alpha_regret] \
[allow_negative] \
[epsilon] \
[merit_sortition_alpha] \
[active_inferer_quantile] \
[active_forecaster_quantile] \
[active_reputer_quantile] \
[enable_worker_whitelist] \
[enable_reputer_whitelist] \
[flags...]
```

---

## 👋 Stay Ready for Mainnet

You're now ready to create your first topic as soon as Allora enables permissionless access on mainnet.  

---
