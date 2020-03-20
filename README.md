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
sudo wget https://github.com/Flashgroupdevs/Linux_wallet/raw/master/Linux-Wallet-16.04/ozeetyd
```
fillout the password of your username and press enter
```bash
sudo wget https://github.com/Flashgroupdevs/Linux_wallet/raw/master/Linux-Wallet-16.04/ozeety-tx
```
```bash
sudo wget https://github.com/Flashgroupdevs/Linux_wallet/raw/master/Linux-Wallet-16.04/ozeety-cli
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
addnode=62.171.161.172
addnode=5.189.189.254
addnode=165.22.100.164
addnode=68.183.207.201
addnode=134.209.185.252
addnode=178.128.109.168
addnode=167.71.49.225
addnode=167.71.230.110
addnode=167.71.69.37
addnode=178.128.100.208
addnode=68.183.73.181
addnode=165.22.50.174
addnode=167.99.243.177
addnode=157.245.36.167
addnode=134.209.153.233
addnode=159.89.124.113
addnode=157.230.249.137
addnode=178.128.169.18
addnode=157.230.103.252
addnode=167.99.176.122
addnode=167.71.229.85
addnode=159.203.8.36
addnode=157.230.125.129
addnode=138.197.171.102
addnode=167.71.169.76
addnode=157.245.174.75
addnode=39.59.84.207
addnode=138.197.149.83
addnode=159.89.140.81
addnode=134.209.199.165
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
addnode=167.71.141.72
addnode=157.245.89.114
addnode=165.22.236.71
addnode=68.183.32.4
addnode=165.22.239.22
addnode=157.245.70.79
addnode=159.203.6.92
addnode=157.245.65.17
addnode=157.245.73.204
addnode=157.245.66.171
addnode=178.62.229.133
addnode=178.62.237.238
addnode=178.62.228.53
addnode=178.62.203.63
addnode=178.62.250.105
addnode=178.62.200.104
addnode=167.172.72.234
addnode=157.245.147.8
addnode=128.199.128.176
addnode=128.199.251.101
addnode=157.245.235.228
addnode=167.172.127.88
addnode=64.225.32.47
addnode=64.225.34.160
addnode=64.225.34.26
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
