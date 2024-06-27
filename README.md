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
