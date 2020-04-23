# 18-BLOCKCHAIN

First, you need to download and open the MyCrypto app. 

Create a new wallet using the tab on the left. 

Choose Generate a wallet and use the Mnemonic Phrase. The app will generate a unique phrase and you need to store it in a safe place. Once you have confirmed your phrase, you will need to use it again in the future to access your wallet. 

Choose an address to unlock, and copy it. 
Then change your network, and select "Ropsten".
Then request some free test tokens, using the following website: https://faucet.ropsten.be

Good job, now you've successfully set up your crypto wallet. We will use this to create the transactions.

---

Now we need to create our genesis blocks. 
Open a new terminal window, navigate to the Blockchain-Tools folder and type ./puppeth.

**pic 001**

Type a name for your network, then type 2 to configure new genesis, and then 1 to create a new genesis from scratch. 


Type 1 to pick the Proof of Work consensus engine to use. 

NOW, copy and paste an address from your Ethereum wallet in Mycrypto (but remove 0x)

Hit "enter" until you reach the Chain ID prompt. Make up a number to use as chain ID.

**pic 002**
---

Now we need to export the genesis config. 

In the puppeth prompt, navigate to the "Manage existing genisis" by typing 2 and hitting enter. Type 2 again.

This will export the .json files, but we only need the one without the suffixes.

Now create 2 nodes to build the chain. 
Exit puppeth (Ctrl+C)

Create the first node's data directory using geth:
geth account new --datadir node1

copy the node 1 key into its keystore file. 

Initialize the nodes with the genesis blocks.

./geth init yournetworkname.json --datadir node1

do the same for node 2:

./geth init yournetworkname.json datadir node2

---

Getting the chain going

launch the first node using geth --datadir node1 --mine minterthreads 1

**pic 003**

now find the address (enode://).

Open a new git bash, and:
geth --datadir node2 --port 30304 --rpc --bootnodes "enode://(insert the enode here)" --ipcdisable

Now your chain is running.
 **pic 004**
---

Now we need to make some transactions on our chain. 
Open up Mycrypto and get the private key of the ETH address we used (on the Kovan network)

Use the mnemonic phrase to unlock the wallet, and select the ETH address to pre-fund the chain. Click on "Wallet info", and click on the eye icon next to "Private Key".

Click "Change Network" at the bottom left. Click "Add Custom Node" and then add the custom network info from the genesis. 

The chain id must match what we used earlier. 

Use http://127.0.0.1:8545 as the URL. Double check that the network is selected and connected.

