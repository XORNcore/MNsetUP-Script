# ![XORN Coin](https://xorn.cc/img/logo.svg)

Use this instructions to install the wallet,  and setup single masternode on Windows machine (HOT wallet/s).


## Table of Content
* [1. Desktop Wallet Preparation](#1-desktop-wallet-preparation-)
* [2. Masternode Setup](#2-masternode-setup-)
	* [2.1 Send the coins to your wallet](#21-send-the-coins-to-your-wallet)
	* [2.2 VPS setup](#22-vps-setup)
	* [2.3 Automatic Masternode Setup](#23-automatic-masternode-setup)
	* [2.4 Add masternode on the desktop wallet](#24-add-masternode-on-the-desktop-wallet)
* [3. FAQ](#3-faq)
* [4. The last and the most important step](#4-the-last-and-the-most-important-step)

## 1. Desktop Wallet Preparation

### 1.1 Setup the wallet
a. Download the [wallet](https://github.com/XORNcore/XORN/releases/tag/Wallet_Windows)
b. Start the wallet and wait for the sync. (30min to 1h depending on the number of the connections)
	
## 2. Masternode Setup

### 2.1 Send the coins to your wallet. Open Console (Tools => Debug console)
a. Create a new address. 
# ![Step1](https://i.imgur.com/kkmZBZY.png)
b. Send exactly 10000.00 coins to the generated address. (Send all coins in one transaction, fees should be paid additionally on top on 10k amount)
# ![Step2](https://i.imgur.com/aqJotsA.png)
# ![Step2.1](https://i.imgur.com/69KgSVu.png)
c. Wait for the at least 1 confirmation of the transaction.
d. Generate a new masternode private key by running the following command in wallet debug console `masternode genkey`.
# ![Step3](https://i.imgur.com/RjzraGy.png)
e. Take txID of collateral transaction by running the following command in wallet debug console `masternode outputs`. 
# ![Step4](https://i.imgur.com/d1bQcrn.png)
f. Do not close console, or copy results to any place.

### 2.2 VPS setup
a. Register on [Vultr](https://www.vultr.com/?ref=7401843) 

OR

[DigitalOcean](https://digitalocean.com) (do not forget verify your e-mail)

b. Send some money to your account to deploy a server. 
c. Recommended server configuration:  
- OS: Ubuntu 16.04
- Memory: 1GB
- Storage: 10GB minimum free space

### 2.3 Automatic Masternode Setup
a. Download [putty](https://the.earth.li/~sgtatham/putty/latest/w64/putty-64bit-0.70-installer.msi)
b. Start putty and login as root user. (Root password and server ip address are on your VPS management page)
c. Recommended to run following command before starting the installation script `apt-get update && apt-get upgrade`
d. To start the installation, paste this command and answer the questions:
```
wget -q https://raw.githubusercontent.com/XORNcore/MNsetUP-Script/master/install_user_xorn.sh
bash install_user_xorn.sh
```
e.  After script finished , copy "string for masternode.conf".

### 2.4 Add masternode on the desktop wallet

a. Go to XORN base folder (`C:\Users\[your account folder]\AppData\Roaming\XORN` for Windows 7 desktops)
b. Open 'masternode.conf' file in text editor (note pad for example for Windows users).
c. Add new line and paste the string copied from "string for masternode.conf" (output of installation script run on VPS)
   
  It will look like: 
  MN1 IP:12311 masternodeprivkey 10K desposit transaction id. 'masternode outputs' 10K desposit transaction index. 'masternode outputs'
   
  For example: 
  `MN1 192.168.1.1:12311 93HaYBVUCYjEMeeH1Y4sBGLALQZE1Yc1K64xiqgX37tGBDQL8Xg 2bcd3c84c84f87eaa86e4e56834c92927a07f9e18718810b92e0d0324456a67c 0`

  Label: `MN1`
  IP Address and port: `192.168.1.1:12311`
  Private key: `93HaYBVUCYjEMeeH1Y4sBGLALQZE1Yc1K64xiqgX37tGBDQL8Xg`
  Transaction ID: `629dc27b721f57c97550868cac9f7e41049d12cce8ac344732b7f74a9fc81815`
  Output index:  `0`

  You can also create it yourself by Copying your masternode private key, transaction id and transaction index from step 2.1.d and 2.1.e

d. Save file (masternode.conf)
e. Restart wallet.
f. You must wait 15 confirmations of collateral transaction (10000.00 XORN)
g. Go to tab Masternodes in your wallet and press 'Start missing' button.
# ![Step5](https://i.imgur.com/5mzOTGM.png)


Congratulations!!
Your MN is now started!!   
	

## 3. FAQ


1. How can I get my masternode rewards transfered to other address?
	1.1 Enable coin control feature in your wallet (Settings => Options => Display => Display coin control feature)
	1.2 Go to send tab
        1.3 Press the button `Open Coin Control`
	1.4 Select from the input list button only the inputs with amounts different of MN collateral (10000.00)
	1.5 Click OK
	1.6 You can send selected amount to any valid XORN address.
	1.7 Note: DO NOT EVER Transfer XORN from that original 10k deposit or you'll break your Masternode.

2. What is the password for the tritt account on VPS?
	- There is no default password. When you create a user it does not have a password.

3. I get the following error: "Could not allocate vin".
	- Make sure your wallet fully synced and UNLOCKED.

4. How many masternodes can I run using one IP/server?
	- The limit is only the memory. One masternode requires 150-300MB RAM. A server with 1GB memory can run 3 masternodes. Each XORN MN requires own public IP, so you will need additional IP address(es) to run multiple XORN MNs on same server.

5. I got stuck. Can you help me?
	- Try to get help from the community and remember to get help only in public channels. Look for our moderators first!
		- [XORN-team Discord](https://discord.gg/cBm7Ctr)
		- [https://bitcointalk.org/index.php?topic=4701106.0 ](https://bitcointalk.org/index.php?topic=4701106.0)
