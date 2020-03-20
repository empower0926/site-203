# Masternode Setup - Step by step guide
Requirements: 	
1.) VPS for example on vultr or AWS on Amazon Services or Digital Ocean (on digitalocean you can get bonus 50$ for 30 days)
2.) for 1 Masternode you need a wallet with 10001 OZTG Coins
Feel free to use our reflinks to signup: 
vultr:  <a href="https://www.vultr.com/?ref=7811287"><img src="https://www.vultr.com/media/banner_2.png" width="468" height="60"></a>
Feel free to use our reflinks to signup: 
DigitalOcean ( to get the Bonus of 50$ ) you can use this link: https://m.do.co/c/b5a2c6e0eeb7
## start in the wallet 
in wallet: Open Debug console: 

```bash
masternode genkey
```
<table>
<tr><td>example</td></tr>
<tr><td>7ehsxiEwmLzeT4EaCuX9v2euuYQNGSjjBKxRUTrmbdXG</td></tr>
</table>

```bash
getaccountaddress "MN1"  
```
<table>
<tr><td>example</td></tr>
<tr><td>xfdbcQmmJUUPJ9RKZfa1ariykE1z774156P</td></tr>
</table>

send exact 10000 Coins to the address (confirmation need: 15) 


# Installation: for Security use SSH on your vps!!
setup start with security on vps in putty (firewall)
```bash
sudo ufw allow 22
```
```bash
sudo ufw allow 80
```
```bash
sudo ufw allow 8386
```
```bash
sudo ufw enable
```
You will be prompted with "Yes or no". type y and press enter
```bash
sudo ufw default deny
```
start install the requirements on VPS:
```bash
sudo apt-get update
```
```bash
sudo apt-get upgrade -y
```
```bash
sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils python3 libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-test-dev libboost-thread-dev libboost-all-dev libboost-program-options-dev -y
```
```bash
sudo apt-get install libminiupnpc-dev libzmq3-dev libprotobuf-dev protobuf-compiler unzip software-properties-common -y
```
```bash
sudo add-apt-repository ppa:bitcoin/bitcoin
```
You will be prompted with "Enter". press enter
```bash
sudo apt-get update
```
add another user for security reason!:
```bash
sudo adduser yourusername
```
You will be prompted with Set a password. type a good password and press enter
again You will be prompted with rename the password. type your password and press enter
you will be prompted for some account details: press 5 times enter 
You will be prompted with "Yes or no". type y and press enter
```bash
sudo usermod -aG sudo yourusername
```
change to user 
```bash
su - yourusername
```
download the wallet-client, tx and daemon file
```bash
sudo wget https://github.com/FLASHMONILTD/GITHUB-OZEETY/raw/master/Linux-Wallet/ozeetyd
```
fillout the password of your username and press enter
```bash
sudo wget https://github.com/FLASHMONILTD/GITHUB-OZEETY/raw/master/Linux-Wallet/ozeety-tx
```
```bash
sudo wget https://github.com/FLASHMONILTD/GITHUB-OZEETY/raw/master/Linux-Wallet/ozeety-cli
```
```bash
sudo chmod +x ozeetyd
```
```bash
sudo chmod +x ozeety-tx
```
```bash
sudo chmod +x ozeety-cli
```
```bash
sudo mv ozeetyd ozeety-cli ozeety-tx /usr/bin/
```
```bash
sudo apt-get install libdb4.8-dev libdb4.8++-dev -y
```
```bash
mkdir $HOME/.ozeety
```
```bash
nano $HOME/.ozeety/ozeety.conf
```
copy this with your details in th conf. file (choose only another good password, you need your masternode genkey from wallet and the ip address of the vps server)
```bash
#----
rpcuser=rpc_ozeety
rpcpassword=chooseagoodpassword
rpcallowip=127.0.0.1
#----
listen=1
server=1
daemon=1
maxconnections=64
#----
masternode=1
masternodeprivkey=your-MASTERNODE-GENKEY-from-debugconsole
externalip= Your IP-address
addnode=167.71.66.94
addnode=159.65.60.210
addnode=167.71.72.157
addnode=167.71.79.115
addnode=167.71.72.110
addnode=165.22.224.32
addnode=167.71.138.75
addnode=134.209.98.101
addnode=167.71.117.234
addnode=134.209.117.45
addnode=165.22.8.105
addnode=134.209.209.37
addnode=165.22.137.88
addnode=134.209.50.97
addnode=157.245.75.54
addnode=134.209.86.193
addnode=174.138.23.195
addnode=165.22.59.206
addnode=167.71.69.189
addnode=68.183.1.90
addnode=167.71.5.168
addnode=178.254.40.82
addnode=178.254.29.39
addnode=178.254.28.153
addnode=178.254.12.25
addnode=167.71.75.87
addnode=167.71.138.75
addnode=68.183.196.152
addnode=165.22.75.47
addnode=68.183.204.178
addnode=157.230.106.169
addnode=142.93.151.130
addnode=209.97.176.228
addnode=167.71.48.31
addnode=165.22.228.224
addnode=178.128.47.26
addnode=104.248.148.172
addnode=104.248.163.206
addnode=68.183.45.212
addnode=178.128.231.71
addnode=167.71.208.34
addnode=68.183.2.147
addnode=134.209.94.131
addnode=68.183.10.232
addnode=142.93.225.113
addnode=142.93.237.37
addnode=104.248.80.204
addnode=167.71.79.35
addnode=165.22.193.197
addnode=104.248.87.234
addnode=165.22.106.189
addnode=157.230.40.176
addnode=178.128.59.214
addnode=206.189.156.240
addnode=206.189.145.150
addnode=104.248.150.175
addnode=165.22.247.204
addnode=157.230.247.193
addnode=165.22.100.242
addnode=209.97.164.162
addnode=167.71.216.219
#----
```
save this file by pressing CONTROL+O and press enter
close this file by pressing CONTROL+X
# start the vps server with
```bash
ozeetyd
```
if everything is fine: you get an output: ozeety server starting



### back in wallet
 
go to debug console
```bash
masternode outputs
```
<table>
<tr><td>example</td></tr>
 <tr><td>{</td></tr>
<tr><td>    "txhash": "c8ab8aa43d50cae6bf2b89b09f124bd83beaec00537884be8ec6585d1922", </td></tr>
<tr><td>     "outputidx": 1 {</td></tr>
<tr><td>   }</td></tr>
</table>
# Configure masternode.conf file (look at the example in file), reopen wallet and start masternode in debug console
<table>
<tr><td>example for masternode in masternode.conf file </td></tr>
<tr><td>mn1 IP_OF_THE_SERVER:8386 MASTERNODE_GENKEY TX_HASH TX_OUTPUTS</td></tr>
<tr><td>mn1 123.12.15.14:8386 6ehsxiEwmLzeT4EaCuX9v2euuYQNGSjjBKxRUTrmbdXG c8ab8aa43d50cae6bf2b89b09f124bd83beaec00537884be8bae6585d1922 1</td></tr>
</table>

save file, reopen wallet and start in debug console !

```bash
startmasternode alias false MN1
```
