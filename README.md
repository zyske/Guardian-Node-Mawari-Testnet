# 🚀 Mawari Guardian Node — Testnet Setup Guide

Run your **Mawari Guardian Node** on a VPS and join the decentralized network!  
Follow the simple steps below 👇  

---

## 🧠 Recommended VPS Specs

| Component | Minimum | Recommended |
|------------|----------|--------------|
| CPU | 1 Core | 2+ Cores |
| RAM | 8 GB | 8 GB or higher |
| Storage | 10 GB | 20 GB+ SSD |

📘 **Official Docs:** [docs.mawari.net](https://docs.mawari.net/decentralized-infrastructure-offering-dio/operating-the-guardian-node-testnet)  
💧 **Testnet Faucet:** [hub.testnet.mawari.net](https://hub.testnet.mawari.net/)  
🎨 **Mint Guardian Node NFTs:** [testnet.mawari.net/mint](https://testnet.mawari.net/mint)

---

## ⚙️ Run Mawari Guardian Node on VPS

### 1️⃣ Update the System
\`\`\`bash
sudo apt update && sudo apt upgrade -y
\`\`\`

### 2️⃣ Install Docker
```bash
sudo apt install docker.io -y
```
### 3️⃣ Enable and Start Docker Service
\`\`\`bash
sudo systemctl enable docker
sudo systemctl start docker
\`\`\`

### 4️⃣ Add User to Docker Group
\`\`\`bash
sudo usermod -aG docker \$USER
\`\`\`

### 5️⃣ Run Mawari Node
\`\`\`bash
mkdir -p ~/mawari && \
docker run --pull always -d \
  --name mawari-guardian \
  -v ~/mawari:/app/cache \
  -e OWNERS_ALLOWLIST=YourWalletAddress \
  us-east4-docker.pkg.dev/mawarinetwork-dev/mwr-net-d-car-uses4-public-docker-registry-e62e/mawari-node:latest
\`\`\`

> 📝 Replace \`YourWalletAddress\` with your **own wallet address**.

---

### 6️⃣ Check Logs
\`\`\`bash
docker logs -f mawari-guardian
\`\`\`

### 7️⃣ Get Your Burner Address
\`\`\`bash
sudo cat ~/mawari/flohive-cache.json | grep -i "address"
sudo cat ~/mawari/flohive-cache.json | grep -i "privateKey"
\`\`\`

> ⚠️ **Never share your private key.** Only use the \`Burner Address\` for delegation.

---

### 8️⃣ Delegate Your Guardian NFTs
- Go to [testnet.mawari.net/mint](https://testnet.mawari.net/mint)  
- Mint **3 Guardian NFTs** using **Metamask**  
- Delegate them to your **Burner Address**

### 9️⃣ Send 1 MAWARI Token to Your Burner Address

---

## 🔁 Helper Commands

**Check all logs**
\`\`\`bash
docker logs -f mawari-guardian
\`\`\`

**Check active containers**
\`\`\`bash
docker ps -a
\`\`\`

**Restart container (keep Burner Address)**
\`\`\`bash
sudo docker restart mawari-guardian
\`\`\`

**Stop & remove container (keep Burner Address)**
\`\`\`bash
sudo docker stop mawari-guardian
sudo docker rm mawari-guardian
\`\`\`

**Delete cache folder (removes Burner Address)**
\`\`\`bash
sudo rm -rf ~/mawari
\`\`\`

---

## 🧩 Important Notes

- If delegation status = **pending**, try using a **new wallet**.  
- Always use **Metamask** for minting and deployment (not other wallets).  
- You can run multiple nodes if your VPS specs allow,  
  but the method is **not published for security reasons.**

---

