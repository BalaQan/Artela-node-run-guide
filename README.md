# Artela-node-run-guide

The Artela Blockchain is an advanced Layer 1 (L1) network that enables developers to implement user-defined native extensions and develop high-performance decentralized applications (dApps).
It surpasses EVM-equivalence with superior extensibility and inter-domain interoperability.

 (So go back to work)

*Min Hardware Requirement:
4x core CPU
8GB RAM
100GB storage (SSD or NVME)

*Recommended Hardware Requirement:
8x CPU
16GB RAM
1TB storage (SSD or NVME)

#First, run the script with the following command:

  wget https://raw.githubusercontent.com/freshe4qa/artela/main/artela.sh && chmod +x artela.sh && ./artela.sh

#Enter the number 1 and click enter.
#Select one name for your node and click enter.
#Wait for the installation to finish.
#Now enter the number 2 and click enter.
#Write emportant information such as address and private key.
#Now enter the number 4 and click enter to exit.

*Enter the following command:

   source $HOME/.bash_profile
  
   artelad status 2>&1 | jq .SyncInfo
   
#Whenever your node is synced, It means (Catching Up = False) and every Blocks synced with network block then You can go to the next step!
#You can check your node status here: https://betanet-scan.artela.network/

#Enter the following command to check:

  artelad status 2>&1 | jq .SyncInfo

#If the movement to the front of the blocks is slow, restart the node with the following command:

  sudo systemctl restart artelad

#The blocks should now be synced!

#Now, with the following command and replacing the Artela wallet address, Get the EVM wallet address in EIP 55 format and copy it.

  artelad debug addr <YOUR_ART_ADDRESS>  

#Now, Enter Discord and recive faucet.

  https://discord.com/invite/artela

#Click the command below to check the balance(Instead of $ARTELA_WALLET_ADDRESS, put the wallet address that we created in the first step):

  artelad query bank balances $ARTELA_WALLET_ADDRESS   

#To get private key for import to Metamask, just type the following command:

  artelad keys unsafe-export-eth-key wallet

#For add Artela network, enter the following information in your Metamask:

Network Name: Artela Testnet
New RPC URL: https://betanet-rpc1.artela.network
ChainID: 11822
Symbol: ART
Block Explorer URL: https://betanet-scan.artela.network/

#Check that the node is sync with the following command:
  
  artelad status 2>&1 | jq .SyncInfo

### Constructed by Validor ###

#Enter the code below:

artelad tx staking create-validator \
--amount="100000000000000000uart" \
--pubkey=$(artelad tendermint show-validator) \
--moniker="Validator_name" \
--website="Website_name" \
--details="there is no gravity here" \
--security-contact "" \
--identity "your-keybase-id" \
--commission-rate="0.10" \
--commission-max-rate="0.20" \
--commission-max-change-rate="0.01" \
--min-self-delegation="1" \
--gas="200000" \
--chain-id="artela_11822-1" \
--from=wallet \
--node tcp://localhost:26657 \
-y

#Press y and enter

#Note down the "hash" and validator details(name and address , ...)

#If there is an error, use the following code:

artelad tx staking edit-validator \
--new-moniker "Validator-name" \
--identity "" \
--details "artela node" \
--website "Your-Website" \
--security-contact "" \
--chain-id artela_11822-1 \
--from wallet \
--gas-adjustment 1.5 \
--gas auto \
--gas-prices 0.025uart \
-y

#Take a backup of these two files and keep them in place:

  ~/.artelad/config/node_key.json
  ~/.artelad/config/priv_validator_key.json

#Enter the following command to delegate to yourself: 

artelad tx staking delegate $(artelad keys show wallet --bech val -a) 1000000000000000000uart --from wallet --chain-id artela_11822-1 --gas-adjustment 1.5 --gas auto --gas-prices 0.025uart -y
