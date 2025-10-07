# Mawari Guardian Node - Testnet

Guide to running the **Mawari Guardian Node** on Testnet.

---

## Recommended VPS Specifications
- 1 Core CPU
- 8 GB RAM
- 10 GB Storage  
> Higher specs are better

---

## Official Documentation
[Operating the Guardian Node Testnet](https://docs.mawari.net/decentralized-infrastructure-offering-dio/operating-the-guardian-node-testnet)

---

## Testnet Faucet
Request testnet tokens for your address using Chrome:  
[Hub Testnet Mawari](https://hub.testnet.mawari.net/)

---

## Mint Mawari Guardian Node NFTs
Go to the NFT minting page using **Metamask** only:  
[Testnet Minting](https://testnet.mawari.net/mint)  
Mint **3 NFTs**.

---

## Run Node on VPS

1. **Update the system:**
```sudo apt update && sudo apt upgrade -y```

2. **Install Docker:**
```sudo apt install docker.io -y```

3. **Enable and start Docker service:**
```sudo systemctl enable docker
sudo systemctl start docker```

4. **Add your user to the Docker group:**
```sudo usermod -aG docker $USER```

5. **Run Mawari Node:**
```mkdir -p ~/mawari && \
docker run --pull always -d \
  --name mawari-guardian \
  -v ~/mawari:/app/cache \
  -e OWNERS_ALLOWLIST=YourWalletAddress \
  us-east4-docker.pkg.dev/mawarinetwork-dev/mwr-net-d-car-uses4-public-docker-registry-e62e/mawari-node:latest```

> Replace YourWalletAddress with your wallet address

6. **Check logs:**
```docker logs -f mawari-guardian```

7. ** Copy your Burner Address from the logs:**
```sudo cat ~/mawari/flohive-cache.json | grep -i "address"```
```sudo cat ~/mawari/flohive-cache.json | grep -i "privateKey"```

> Do NOT share your private key. Only copy the Burner Address.

8. Delegate your Mawari Guardian NFTs to your Burner Address.

9. Send 1 Mawari token to your Burner Address.


---

Helper Commands

**Check all logs:**
```docker logs -f mawari-guardian```

**Check active containers:**
```docker ps -a```

**Restart container without deleting Burner Address:**
```sudo docker restart mawari-guardian```

**Stop and remove container without deleting Burner Address:**
```sudo docker stop mawari-guardian
sudo docker rm mawari-guardian```

**Remove cache directory including Burner Address:**
```sudo rm -rf ~/mawari```


---

Important Notes

If delegation status is pending, use a new wallet.
Always use Metamask / Metamask extension for minting and deploying.
Running multiple nodes is possible if VPS specs allow, but the method is not published for security reasons.

