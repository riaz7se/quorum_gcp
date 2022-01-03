# Quorum on Google Cloud Console VM


- https://consensys.net/docs/goquorum/en/latest/tutorials/quorum-dev-quickstart/using-the-quickstart/
```
  $ sudo apt update
  $ sudo apt install docker.io
  $ sudo groupadd docker
  $ sudo usermod -aG docker $USER
```
Restart VM

### Install NodeJs
  $ curl -sL https://deb.nodesource.com/setup_14.x | sudo bash -
  $ sudo apt-get install -y nodejs
  $ sudo apt-get install gcc g++ make
  
  
### Yarn Install
  $ curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | gpg --dearmor | sudo tee /usr/share/keyrings/yarnkey.gpg >/dev/null
  $ echo "deb [signed-by=/usr/share/keyrings/yarnkey.gpg] https://dl.yarnpkg.com/debian stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
  $ sudo apt-get update && sudo apt-get install yarn

### Quorum Quickstart

#### Permission 
  sudo chown -R $USER ~/.npm
  sudo chown -R $USER /usr/lib/node_modules
  sudo chown -R $USER /usr/local/lib/node_modules
  sudo chown -R $USER /usr/bin/

  npm install -g quorum-dev-quickstart


  cd network
  ./run.sh
  
#### Gives CLient version  
  curl -X POST --data '{"jsonrpc":"2.0","method":"web3_clientVersion","params":[],"id":1}' -H 'Content-Type: application/json' http://<gcp_ext_ip>:8545

### sd
  curl -X POST --data '{"jsonrpc":"2.0","method":"net_peerCount","params":[],"id":1}' -H 'Content-Type: application/json'  http://34.125.116.147:8545
  
#### Most recent block nuber
  curl -X POST --data '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}' -H 'Content-Type: application/json' http://34.125.116.147:8545
  
  
### Install Web3
  npm install web3
 
### deploy the private transaction
  cd smart_contracts
  npm install
  node scripts/private_tx.js
  
Creating contract...
Waiting for transaction to be mined ...
Getting contractAddress from txHash:  {
  blockHash: '0xacb70865f5f9b3ed96ea108eca138bb47a4fe0ee0a93d78bf60ac656e8f74318',
  blockNumber: 1060,
  contractAddress: '0x38Fef9ccf460A4d296f8327eBF7A9DfbD9135709',
  cumulativeGasUsed: 0,
  from: '0xf0e2db6c8dc6c681bb5d6ad121a107f300e9b2b5',
  gasUsed: 0,
  isPrivacyMarkerTransaction: false,
  logs: [],
  logsBloom: '0x0000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000',
  status: true,
  to: null,
  transactionHash: '0xfd6a88e908bd9a916dafb1c865283c0c7dedd14a850676776c45d6e41b12213e',
  transactionIndex: 0
}

eth.getTransaction('0xfd6a88e908bd9a916dafb1c865283c0c7dedd14a850676776c45d6e41b12213e')

### Check in all 3 nodes
```
var address = "0x38Fef9ccf460A4d296f8327eBF7A9DfbD9135709"
var abi = [{"constant":true,"inputs":[],"name":"storedData","outputs":[{"name":"","type":"uint256"}],"payable":false,"type":"function"},{"constant":false,"inputs":[{"name":"x","type":"uint256"}],"name":"set","outputs":[],"payable":false,"type":"function"},{"constant":true,"inputs":[],"name":"get","outputs":[{"name":"retVal","type":"uint256"}],"payable":false,"type":"function"},{"inputs":[{"name":"initVal","type":"uint256"}],"type":"constructor"}];
var private = eth.contract(abi).at(address)
private.get()  

#### send Transactio to Member3
private.set(200,{from:eth.accounts[0],privateFor:["1iTZde/ndBHvzhcl7V68x44Vx7pl8nwx9LqnM/AfJUg="]});

### Check in all 3 nodes
private.get()
```

### Use Cakeshop
## Second node’s public key & Address. Execute below command
```
riaz7se@quorum-vm-1:~/quorum-test-network/network$ ./attach.sh 2
Attempting to connect to member2quorum
Welcome to the Geth JavaScript console!
instance: Geth/node7-/v1.9.25-stable-919800f0(quorum-v21.10.0)/linux-amd64/go1.15.6
coinbase: 0xe090a28b8a9d0a69ec259cb745036d5d1030e3ea
at block: 2326 (Fri Dec 24 2021 02:49:38 GMT+0000 (UTC))
 datadir: /data/dd
 modules: admin:1.0 debug:1.0 eth:1.0 istanbul:1.0 miner:1.0 net:1.0 personal:1.0 quorumExtension:1.0 rpc:1.0 txpool:1.0 web3:1.0
```
### Use Coinbase as Private for
Private For: 0xe090a28b8a9d0a69ec259cb745036d5d1030e3ea

##### Adding Network to MetaMask
In Metamask add network. Give below details
IP: gcp_ext_ip:
Port: JSON-RPC port
JSON-RPC HTTP service endpoint                 : http://localhost:8545

Name: <Any unique Name>
New RPC URL: http://34.125.116.147:8545
Chain ID: 0x539
<execute below command in any Quorum node 
> eth.chainId()
"0x539"

### Add Account to Metamask
##### In Metamask, -> import Account -> Select Private key. Paste 0x8f2a55949038a9610f50fb23b5883af3b4ecb3c3bb792cbcefbd1542c692be63
#### Above Private Key copied from GoQuorum..Test Account 1 (address 0xfe3b557e8fb62b89f4916b721be55ceb828dbd73)


### Other commands

### Find installed Etheeum
dpkg -l ethereum
sudo dpkg -S ethereum
