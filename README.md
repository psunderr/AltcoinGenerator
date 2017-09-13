# Altcoin Generator
Easiest way to create your own cryptocurrency.

## What does this script do?

This script is an experiment to generate new cryptocurrencies (altcoins) based on litecoin.
It will help you creating a git repository with minimal required changes to start your new coin and blockchain.

## What do I have to do?

You need to make sure you have at least docker and git installed.
The other requirements will be installed automatically in a docker container by the script.

Simply open the script and edit the first variables to match your coin requirements (total supply, coin unit, coin name, tcp ports..)
Then simply run the script like this:

```
bash altcoin_generator.sh
```

## What will happen then?

The script will perform a couple of actions:

  * Create a docker image ready to build and run your new coin nodes
  * Clone GenesisH0 and mine the genesis blocks of main, test and regtest networks in the container (this might take a lot of time)
  * Clone litecoin
  * Rename files and replace variables in litecoin code (genesis hashes, merkle tree hashes, tcp ports, coin name, supply...)
  * Build your new coin
  * Run 4 docker nodes with your coin daemon and connect each other.
    * A directory mapped for each node will be created: miner2, miner3, miner4, miner5. They contain data and configuration of each independent node.
  
## What can I do next?

You can first check if your nodes are running and then ask them to generate some blocks.
Instructions on how to do it will be printed once the script execution is done.

## Is there anything I must be aware of?

Yes.

  * This is a very simple script to help you bootstrap. More changes will be needed to launch a cryptocurrency for real.
  * You have to manually change the pictures in mycoin/share/pixmaps.
  * You will need change the checkpoints in mycoin/src/chainparams.cpp.
  * Consider adding a seed node and add it to src/chainparams.cpp as well.
    * Currently all seeds are getting disabled.
  * The script connects to the regression test network by default. This is a special network that will let you mine new blocks almost instantly (nice for testing). To launch the nodes in the main network, simply leave the CHAIN variable empty.
  
## I think something went wrong!

Then you can just remove all directories that were created by the script and start all over again.

## Can I help the project?
Sure. You can either submit patches, or make a donation if you found this project useful:

LTC: Lcaey9FP2zdu4C9TSVffDG1DuKh78yCDYT
BTC: 1BB44xSWSHwgM2AMP7MScqk2CALuo6A6UY
