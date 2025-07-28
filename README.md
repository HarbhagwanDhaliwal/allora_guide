````markdown
# 🧠 Allora Topic Creation Guide

Welcome! This guide helps you set up your environment and create a **Topic** on the Allora Network using the latest CLI tools.

> ⚠️ **Note:** Topic creation is currently **permissioned** on testnet.  
> You'll see this error if not whitelisted:
>
> ```
> failed to execute message; message index: 0: not permitted to create topic
> ```

Once Allora goes **permissionless** on mainnet, you'll be able to create topics freely.

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
````

### 2. Install Allora CLI

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
allorad keys add mywallet
```

### Recover an Existing Wallet

```bash
allorad keys add mywallet --recover
```

### List All Wallets

```bash
allorad keys list
```

---

## 💧 Request Testnet Tokens

Visit the faucet and enter your wallet address to get testnet tokens:
👉 [https://faucet.testnet.allora.network/](https://faucet.testnet.allora.network/)

---

## 📌 Create a Topic (Once Permissionless)

### Sample Command

```bash
allorad tx emissions create-topic \
YOUR_WALLET_ADDRESS \
"ETH Price Prediction in 24 hours" \
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
true \
true \
--from YOUR_WALLET_NAME \
--node https://rpc.ankr.com/allora_testnet \
--chain-id allora-testnet-1 \
--fees 2000000uallo
```

### Parameters

```text
[creator]                    Your wallet address
[metadata]                   Topic name/description
[loss_method]                e.g. "mse"
[epoch_length]               In seconds
[ground_truth_lag]           Delay for verifying truth
[worker_submission_window]   Window size for worker
[p_norm]                     Prediction norm
[alpha_regret]               Used in sorting reputers
[allow_negative]             true/false
[epsilon]                    Exploration factor
[merit_sortition_alpha]      Merit sorting weight
[active_inferer_quantile]    Inferer threshold
[active_forecaster_quantile] Forecaster threshold
[active_reputer_quantile]    Reputer threshold
[enable_worker_whitelist]    true/false
[enable_reputer_whitelist]   true/false
```

---

## 💸 Fund Your Topic

Once the topic is created, fund it so that workers can be paid for inferences:

```bash
allorad tx emissions fund-topic \
YOUR_WALLET_ADDRESS \
TOPIC_ID \
1000000uallo \
"inference funds" \
--from YOUR_WALLET_NAME \
--node https://rpc.ankr.com/allora_testnet \
--chain-id allora-testnet-1 \
--fees 200000uallo
```

---

## ✅ Whitelist Workers and Reputers

If your topic uses **whitelists**, you need to manually add the allowed addresses.

### Add a Worker

```bash
allorad tx emissions add-to-topic-worker-whitelist \
YOUR_WALLET_ADDRESS \
WORKER_ADDRESS \
TOPIC_ID \
--from YOUR_WALLET_NAME \
--node https://rpc.ankr.com/allora_testnet \
--chain-id allora-testnet-1 \
--fees 200000uallo
```

### Add a Reputer

```bash
allorad tx emissions add-to-topic-reputer-whitelist \
YOUR_WALLET_ADDRESS \
REPUTER_ADDRESS \
TOPIC_ID \
--from YOUR_WALLET_NAME \
--node https://rpc.ankr.com/allora_testnet \
--chain-id allora-testnet-1 \
--fees 200000uallo
```

---

## 🧪 Try Other Useful Commands

Here are a couple of handy commands you can explore:

* **Register a worker or reputer:**

```bash
allorad tx emissions register ...
```

* **Delegate stake to a reputer:**

```bash
allorad tx emissions delegate-stake ...
```

Explore more using:

```bash
allorad tx emissions -h
```

---

## 📣 Final Words

You're now fully equipped to launch and manage your own topic on the Allora network. Stay tuned for the mainnet launch when topic creation becomes permissionless!

```

---

