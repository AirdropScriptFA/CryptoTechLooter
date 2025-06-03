# Gensyn RL Swarm Setup Guide (Linux / Mac)

---

## 🖥️ Session Management

```bash
screen -ls
```

```bash
screen -r num
```

```bash
# Stop your node
ctrl + c
```

```bash
screen -S gensyn -X quit
```

```bash
rm -rf rl-swarm
```

---

## 🔄 Basic Update and Sudo Installation

```bash
sudo apt update
```

```bash
sudo apt install -y sudo
```

---

## 📦 Install Required Dependencies

```bash
sudo apt update
```

```bash
sudo apt install -y python3 python3-venv python3-pip curl wget screen git lsof nano unzip iproute2 build-essential gcc g++
```

---

## ⚙️ Install CUDA

```bash
[ -f cuda.sh ] && rm cuda.sh
```

```bash
curl -o cuda.sh https://raw.githubusercontent.com/zunxbt/gensyn-testnet/main/cuda.sh
```

```bash
chmod +x cuda.sh
```

```bash
. ./cuda.sh
```

---

## 🧰 Install Node, Yarn, Python, etc.

```bash
sudo apt update
```

```bash
sudo apt install -y python3 python3-venv python3-pip curl wget screen git lsof
```

```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
```

```bash
sudo apt update
```

```bash
sudo apt install -y nodejs
```

```bash
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
```

```bash
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
```

```bash
sudo apt update
```

```bash
sudo apt install -y yarn
```

---

## 📋 Check Versions

```bash
node -v
```

```bash
npm -v
```

```bash
yarn -v
```

```bash
python3 --version
```

---

## 🧪 Start Gensyn Session

```bash
screen -S gensyn
```

---

## 🧬 Clone RL Swarm Repo

```bash
git clone https://github.com/gensyn-ai/rl-swarm.git
```

```bash
cd rl-swarm
```

---

## 🐍 Set Up Python Virtual Environment

```bash
python3 -m venv .venv
```

```bash
source .venv/bin/activate
```

---

## 📦 Install Modal Dependencies

```bash
cd modal-login
```

```bash
yarn install
```

```bash
yarn upgrade
```

```bash
yarn add next@latest
```

```bash
yarn add viem@latest
```

```bash
cd ..
```

---

## 📌 Reset and Checkout Specific Tag

```bash
git reset --hard
```

```bash
git pull origin main
```

```bash
git checkout tags/v0.4.3
```

---

## ✏️ Edit Config File

```bash
nano hivemind_exp/configs/mac/grpo-qwen-2.5-0.5b-deepseek-r1.yaml
```

After editing, press `Ctrl + X`, then `Y`, then `Enter` to save.

---

## ▶️ Run RL Swarm

```bash
RL_SWARM_UNSLOTH=False ./run_rl_swarm.sh
```

---

## 🌐 Expose Local Port (Optional)

```bash
sudo npm install -g localtunnel
```

```bash
lt --port 3000
```

Password is your IP address.

---

## 💾 Backup Swarm Data

```bash
[ -f backup.sh ] && rm backup.sh
```

```bash
curl -sSL -O https://raw.githubusercontent.com/AbhiEBA/gensyn1/main/backup.sh
```

```bash
chmod +x backup.sh
```

```bash
./backup.sh
```

---

## 🧠 W&B Account Prompt After Training

When prompted by `wandb`, *choose*:

```text
(3) Don't visualize my results
```
