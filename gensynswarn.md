# 💻 Gensyn AI RL Swarm Guide (Mac/Linux) 💻

## 📋 Device/System Requirements
![System Requirements](https://github.com/user-attachments/assets/4fbf23bb-846c-4def-be24-157c51fa0b4e)

---

## 🚀 Getting Started

### 🔐 Open Your VPS
```bash
ssh username@ip
```

---

## 🛠 Pre-Requirements

### 🐍 Install Python and Tools

#### Linux/WSL
```bash
sudo apt update && sudo apt install -y python3 python3-venv python3-pip curl wget screen git lsof
```

#### macOS
```bash
brew install python
```

Verify Python version:
```bash
python3 --version
```

---

### 📦 Install Node.js, npm & Yarn

#### Linux/WSL
```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt update && sudo apt install -y nodejs
```

Install Yarn:
```bash
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list > /dev/null
sudo apt update && sudo apt install -y yarn
```

#### macOS
```bash
brew install node && corepack enable && npm install -g yarn
```

Verify:
```bash
node -v
npm -v
yarn -v
```

---

## 👨🏻‍💻 Start the Node (Linux/Mac)

1️⃣ Clone the RL Swarm Repository
```bash
git clone https://github.com/gensyn-ai/rl-swarm.git
```

2️⃣ Create a screen session (VPS)
```bash
screen -S gensyn
```

3️⃣ Navigate to repo
```bash
cd rl-swarm
```

4️⃣ Create & activate virtual environment
```bash
python3 -m venv .venv
source .venv/bin/activate
```

5️⃣ Install dependencies
```bash
cd modal-login
yarn install
yarn upgrade
yarn add next@latest viem@latest
```

6️⃣ Run the node
```bash
cd ..
./run_rl_swarm.sh
```

---

### 🧠 Model Selection Prompts

Choose based on your system:

| Model | RAM | Download Size |
|-------|-----|----------------|
| Qwen 2.5 0.5B | 4GB | 1GB |
| Qwen 2.5 1.5B | 8GB | 4GB |
| Qwen 2.5 7B | 16GB | 15GB |
| Qwen 2.5 32B (4bit) | 50GB | 35GB |
| Qwen 2.5 72B (4bit) | 100GB | 70GB |

Login via the local web page: `http://localhost:3000/`

✅ Save your `ORG_ID` when prompted  
❌ Choose `N` when asked about HuggingFace  
🔢 Select `(3)` for W&B (no visualization) — or `(1)` to link your account.

---

## 🖥 VPS Tips

### Detach screen:
<kbd>Ctrl</kbd> + <kbd>A</kbd> then <kbd>D</kbd>

### Reattach screen:
```bash
screen -r gensyn
```

---

## 🛠 FAQ & Troubleshooting

### 1️⃣ Login to Web UI on VPS
```bash
sudo apt install ufw -y
sudo ufw allow 22
sudo ufw allow 3000/tcp
sudo ufw enable
```

Install Cloudflared:
```bash
wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb
cloudflared --version
cloudflared tunnel --url http://localhost:3000
```

---

### 2️⃣ macOS OOM Fix

Edit `.zshrc`:
```bash
nano ~/.zshrc
```

Add:
```bash
export PYTORCH_MPS_HIGH_WATERMARK_RATIO=0.0
export PYTORCH_ENABLE_MPS_FALLBACK=1
```

Reload:
```bash
source ~/.zshrc
```

---

### 3️⃣ Get Node Name

See logs after starting node (or refer to screenshot):
![Node ID](https://github.com/user-attachments/assets/728c6401-75c8-43b4-973c-e9d515c4b453)

---

### 4️⃣ Save `swarm.pem`

```bash
scp USERNAME@YOUR_IP:~/rl-swarm/swarm.pem ~/swarm.pem
```

---

### 5️⃣ Restart Node (Local)

```bash
cd rl-swarm
python3 -m venv .venv
source .venv/bin/activate
./run_rl_swarm.sh
```

---

### 6️⃣ Fix: "Shutting Down trainer..."

```bash
yarn add -D pino-pretty
rm -rf $HOME/rl-swarm/modal-login/app/layout.tsx
curl -o $HOME/rl-swarm/modal-login/app/layout.tsx https://raw.githubusercontent.com/Mayankgg01/Gensyn-ai-Rl-Swarm_Guide/main/rl-swarm/modal-login/app/layout.tsx
```

Restart node again.

---

## 🔄 Upgrade to New Release (v0.4.3)

```bash
screen -r gensyn
# Ctrl + C to stop if running
cd rl-swarm
git switch main
git reset --hard
git clean -fd
git pull origin main
./run_rl_swarm.sh
```

---

## 📚 References

Check the [official Gensyn RL-Swarm docs](https://github.com/gensyn-ai/rl-swarm) for the latest updates.

---

> 💬 For questions or help, feel free to reach out to the community or open an issue.
