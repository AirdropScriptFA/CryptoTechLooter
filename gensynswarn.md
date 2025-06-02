<div align="center">
  <div style="display: flex; align-items: center;">
    <img src="https://raw.githubusercontent.com/AirdropScriptFA/CryptoTechLooter/796c2e77cdef9dbd6d7ced6fc1aab995e640a153/IMG_20250518_151850_367.jpg" alt="CryptoTechLooter Logo" width="100" style="margin-right: 20px;"/>
    <div>
      <b>This Codes/Software Is Shared By <a href="https://t.me/cryptotechlooter">Crypto Tech Looter</a></b>
    </div>
  </div>
</div>

<div align="center">

# 💻 Gensyn-ai-Rl-Swarm_Guide {Mac/Linux} 💻

</div>


# Device/System Requirements 🖥️

![image](https://github.com/user-attachments/assets/4fbf23bb-846c-4def-be24-157c51fa0b4e)



* Open Your Vps

```
ssh username@ip
```

# Pre-Requirements 🛠

# Install Python and Other Tools

* For **Linux/Wsl**

```
sudo apt update && sudo apt install -y python3 python3-venv python3-pip curl wget screen git lsof

```

* **For Mac**

```
brew install python
```

Check Version

```
python3 --version
```


# Install Node.js , npm & yarn

* For **Linux/Wsl**

```
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - && sudo apt update && sudo apt install -y nodejs
```

* Install Yarn (linux)

```
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
```

```
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list > /dev/null
```

```
sudo apt update && sudo apt install -y yarn
```


* For **Mac**

```
brew install node && corepack enable && npm install -g yarn
```

* Check version **(Linux/Mac)**

```
node -v
```
```
npm -v
```

```
yarn -v
```


<div align="center">

# 👨🏻‍💻 Start The Node (Linux/Mac) 

</div>


* 1️⃣ Clone RL-SWARM Repo

```
git clone https://github.com/gensyn-ai/rl-swarm.git
```


* 2️⃣ Create a screen session **(vps)**

```
screen -S gensyn
````

* 3️⃣ Navigate to rl-swarm

```
cd rl-swarm
```

* 4️⃣ Create & Activate a Virtual Environment

```
python3 -m venv .venv
source .venv/bin/activate
```

* 5️⃣ Install Left-over dependencies

```
cd modal-login
```

```
yarn install
```

```
yarn upgrade &&  yarn add next@latest &&  yarn add viem@latest
```

* 6️⃣ Run the swarm Node 🚀

```
cd ..
```

```
./run_rl_swarm.sh
```

- After Running the Above command it will promt `Would you like to connect to the Testnet? [Y/n]` Enter `Y`

- After than it will promt `>> Which swarm would you like to join (Math (A) or Math Hard (B))? [A/b]`  Enter   `a`

- After than it will promt `>> How many parameters (in billions)? [0.5, 1.5, 7, 32, 72]`    

👇See below and Choose the model Depends on Your System! 

<pre>
- Qwen 2.5 0.5B                - Recommended 4GB RAM, (1GB DOWNLOAD)
- Qwen 2.5 1.5B                - Recommended 8GB RAM, (4GB DOWNLOAD)
- Qwen 2.5 7B                  - Recommended 16GB RAM, (15GB DOWNLOAD)
- Qwen 2.5 32B (4 bit)         - Recommended 50GB RAM, (35GB DOWNLOAD)
- Qwen 2.5 72B (4 bit)         - Recommended 100GB RAM, (70GB DOWNLOAD)
</pre>
    
- After that A web Pop-Up will appear, It will ask u to Login ( if no web pop-up then u have to paste this on ur brower `http://localhost:3000/` 


- Now Login With Your Email Id, Enter OTP and back to ur Terminal/Wsl? **( VPS users check FAQ1 )**


- Now U can see A `ORG_ID` On ur Terminal..Save it!


* Now It will promt `Would you like to push models you train in the RL swarm to the Hugging Face Hub? [y/N]` Enter `N`

* After that it will ask u to select 3 choices related to `W&B Account` just enter `3` - wandb: (3) (Don't visualize my results )

* If u have to see your node's details or logs on WANDB WEB then u can choose 1 and enter your api key there, so it will sync your node to wandb web!

![image](https://github.com/user-attachments/assets/e31345ce-c66c-45b1-a861-e3cc96308544)


![image](https://github.com/user-attachments/assets/c700e3ce-64b6-4bfb-86c4-fd2f2050c88d)



Here we go🚀

Its Done ✅

It will Generate Logs Soon🙌


* Detach from `screen session` **(vps)**

Use `Ctrl + A` and then press `D`

* Attach to gensyn Screen to see Logs

```
screen -r gensyn
```



<div align="center">

#  🛠 FAQ & Troubleshoot 🛠

</div>


# 1️⃣ How to Login or access  http://localhost:3000/ in VPS? 📶

* Open a new Terminal and login ur vps 

* Allow Incoming connection on VPS

```
sudo apt install ufw -y
sudo ufw allow 22
sudo ufw allow 3000/tcp
```

* Enable ufw

```
sudo ufw enable
```

* Install cloudflared on the VPS

```
wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
````

```
sudo dpkg -i cloudflared-linux-amd64.deb
```

* Check version

```
cloudflared --version
```

* Make sure your Node is running on port 3000 in Previous Screen

* Run the tunnel command

```
cloudflared tunnel --url http://localhost:3000
```

* Access the Link from your local machine

    
    ![image](https://github.com/user-attachments/assets/c5bdfec5-123d-4625-8da8-f46269700950)

* Now follow Login!
 
* Done!✅



# 2️⃣ Solution of OOM errors on MacBook (Memory/Cpu limit)

* Open -
 ```
nano ~/.zshrc
```

* Paste in the file

```
export PYTORCH_MPS_HIGH_WATERMARK_RATIO=0.0
export PYTORCH_ENABLE_MPS_FALLBACK=1
```
* Reload with

```
  source ~/.zshrc
```

# 3️⃣ How to get the Node Name?

* Check the image below to get your Node id!

![image](https://github.com/user-attachments/assets/728c6401-75c8-43b4-973c-e9d515c4b453)

# 4️⃣ Save your `swarm.pem` file (for future login)

* open a wsl window 

* If U have to copy this file to your local machine from VPS then Run this command from your local Terminal--

```
scp USERNAME@YOUR_IP:~/rl-swarm/swarm.pem ~/swarm.pem
```

It will save here in ur Terminal's Root Directory!


# 5️⃣ How To start the Next Day (Local Pc)

*
 ```
  cd rl-swarm
 ```

*
 ```
  python3 -m venv .venv
```

*
```
source .venv/bin/activate
```

*
```
./run_rl_swarm.sh
```



# 6️⃣ Solution of >> Shutting Down trainer.. at the starting of node!

❗❗This solution is not for whoes who have the terminated error after the login process!

![image](https://github.com/user-attachments/assets/ac617699-77ce-4bae-8083-1c134386bb47)


* install pino-pretty

```
yarn add -D pino-pretty
```

* Make changes

```
rm -rf $HOME/rl-swarm/modal-login/app/layout.tsx
```

```
curl -o $HOME/rl-swarm/modal-login/app/layout.tsx https://raw.githubusercontent.com/Mayankgg01/Gensyn-ai-Rl-Swarm_Guide/main/rl-swarm/modal-login/app/layout.tsx
```


* Now follow the process of starting the node.

❗❗IMP: if ur node got terminate after the login, Then just Restart your node:


<div align="center">

# 📈 Upgrade to new release (v0.4.3) {Mac/Linux} 

</div>

* Go to gensyn screen (Vps)

```
screen -r gensyn
```

* Stop your node by `ctrl+c` if u are on gensyn screen (Vps)

* Move to rl-swarm directory
```
cd rl-swarm
```

* Pull the latest release 


```
git switch main
git reset --hard
git clean -fd
git pull origin main
```


* Start the swarm Node 🚀

```
./run_rl_swarm.sh
```

* All set, As You guys alraedy know what to do next! No need to told again! just follow the login process and select model.


Follow official Docs for more info and Errors!


> 💬 For questions or help, feel free to reach out to the community or open an issue.
