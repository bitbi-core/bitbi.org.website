+++
title = "BTB full node"
weight = 10
[extra]
multicolumn = true
anchor = "wallets"
bg-color = "green"
+++

BTB full node is like bitcoin full node, it is a software that fully validates transactions and blocks. Almost all full nodes also help the network by accepting transactions and blocks from other full nodes, validating those transactions and blocks, and then relaying them to further full nodes.

## Why run a full node?

Running a full node is the only way to use BTB in a trustless way. You will know for sure that all the rules of BTB are being followed, for example that no BTB are spent not belonging to the owner, that no BTB were spent twice, that no inflation happens outside of the schedule and that all the rules needed to make the system secure are followed. Full nodes are currently the most private way to use BTB, with nobody else learning which BTB belong to you.

Additionally:

* if you are a developer, running a full node is the best way to test your applications with the BTB network. It will help you to understand the BTB network and how it works.
* if you want to mine BTB, you need a full node to provide rpc interface to your mining software.

## How to run a full node?

To run a full node, you need to install the BTB Core software. You can download the software from the [Download Links](/download/bitbi/26.101.0/bitbi-26.101.0-x86_64-linux-gnu.tar.gz).

After downloading the software, you need to extract the tarball and run the `./bin/bitbid` binary. The software will start syncing with the network and will download the blockchain data. This process can take a few hours to a few days depending on your internet connection speed. 

For advanced `bitbid` options, you can run `./bin/bitbid --help` to see the available options.

By default, the software will create a directory `~/.bitbi` to store the blockchain data and configuration files. You can change the data directory by passing the `--datadir` option to the `bitbid` binary.

## How to connect to the full node?

The full node provides a JSON-RPC interface that you can use to interact with the node. The default port for the JSON-RPC interface is `9800`. You can connect to the full node using the `bitbi-cli` tool that comes with the BTB Core software.
