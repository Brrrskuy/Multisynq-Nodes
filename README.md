# Multisynq Synqchronizer Nodes

- Buy VPS di : [t.me/skuycloud](t.me/skuycloud)
- Trakteer buat buy Kopi : https://trakteer.id/brrrskuy/tip `<---`

## First Join : Connect Phantom Wallet ##
`--->`[Join Multisynq Synqchronize Nodes in here](https://startsynqing.com/?ref=2746e7-ek7ufp)

Input code: `drinktheblue`

# 1. Install Docker & Dependencies
  Install Packages
  ```
  sudo apt-get update && sudo apt-get upgrade -y && sudo apt install curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip -y
  ```
  Install Docker
  ```
  curl -fsSL https://get.docker.com | sh
  ```
# 2. Install Nodejs v20+
  ```
  curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - && sudo apt install -y nodejs
  ```
# 3. Install Synqchronize (Universal)
  ```
  npm install -g synchronizer-cli
  ```
# 4. Check Package JSON (Optional)
  ```
  cat /usr/lib/node_modules/synqchronizer/package.json | jq .bin
  ```
# 5. Configure Synchronize
  ```
  synchronize init
  ```
# 6. Running your Synchronize systemd Service
  ```
  synchronize service
  ```
  ## Copy Command Script in VPS ##
  ```
  sudo cp /root/.synchronizer-cli/synchronizer-cli.service /etc/systemd/system/
  ```
  ```
  sudo systemctl daemon-reload
  sudo systemctl enable synchronizer-cli
  sudo systemctl start synchronizer-cli
  ```
  ## Check Status ##
  ```
  sudo systemctl status synchronizer-cli
  ```
## Or Rename file (Optional) ##
  ```
  sudo mv /etc/systemd/system/synchronizer-cli.service /etc/systemd/system/synqchronizer-cli.service
  sudo systemctl daemon-reload
  sudo systemctl enable synqchronizer-cli
  sudo systemctl start synqchronizer-cli
  ```
  Jika ada error dan belum connected , ganti file ini didalamnya
  ```
  sudo nano /etc/systemd/system/synchronizer-cli.service
  ```
  Ganti menjadi ini , sisanya biarkan
  ```
  ExecStart=/usr/bin/docker run --name synchronizer-cli-service --pull always --restart unless-stopped --platform linux/amd64 cdrakep/synqchronizer:latest --depin wss://api.multisynq.io/depin
  ```
  Setelah selesai coba reload systemd dan cek statusnya
  ```
  sudo systemctl daemon-reload
  sudo systemctl restart synchronizer-cli
  ```
# 8. Access your Nodes in Website Synqchronizer Dashboard
  ## Open Port Ufw ##
  ```
  sudo ufw allow 3000/tcp
  ```
  ## Create Screen ##
  ```
  screen -S multisynq
  ```
  ```
  synchronize web
  ```
  Detached from screen `CTRL+A+D`
  
  ## Access your IP VPS
  ```
  http://YOUR_VPS_IP:3000
  ```
# 9. Monitoring Status Synqchronizer
  ```
  sudo systemctl daemon-reload
  sudo systemctl start synqchronizer-cli
  sudo systemctl status synqchronizer-cli
  ```
  ## Check logs realtime for troubleshooting
  ```
  journalctl -u synqchronizer-cli -f
  ```
# Discord Multisynq
Join Discord Claim Roles : https://discord.gg/multisynq
