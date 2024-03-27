+++
title = "BTB Mining"
weight = 40
[extra]
anchor = "mine"
bg-color = "red"
+++

BTB miners are required to install and run a BitBi Node alongside mine software for BTB mining.

The following sections will provide a step-by-step guide on installing and configuring the mine software.

### System Requirements

The BitBi mine software is compatible with Linux operating systems. It necessitates a 64-bit OS with a minimum of 3GB RAM and 100GB of available disk space. The software is optimized for multi-core processors and performs efficiently with a minimum of 2 cores.

### Installation

To download the mine software, click on this [Download Link](/download/miner/1.0.1/bitbi-miner.zip).

After the software is downloaded, extract the tarball and execute the `./mined` binary. Here's an example command to run the mine software:

```bash
./minerd -o http://[rpcuser]:[rpcpassword]@127.0.0.1:9800 --coinbase-addr=[your reward receive address] --coinbase-sig=[any identifier] -t 1
```

The software will then commence mining BTB.

Please note the following:

- `rpcuser` and `rpcpassword`: are the credentials required to access the BitBi Node RPC API. You can locate these credentials in the `~/.bitbi/bitbi.conf` file or obtain them from the BitBi node running command line using the `-rpcuser` and `-rpcpassword` options. If you don't have the credentials, you can create them in the `~/.bitbi/bitbi.conf` file or add the credentials to the BitBi node running command line with the `-rpcuser` and `-rpcpassword` options, followed by restarting the BitBi node.

- `your reward receive address`: represents the address where you wish to receive the mining rewards. You can generate a new address using our wallets.

- `any identifier` is an identifier for the coinbase transaction. You can use any string as the identifier.

For more information about the mine software, you can run `./minerd --help` to view the available options.