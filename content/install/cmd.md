+++
title = "BTB command-line tool"
weight = 10
[extra]
anchor = "cmd"
bg-color = "green"
+++

The main command-line tool to work with BTB smart contracts is `btb`. It is written
in Rust programming language and is open-sourced under Apache 2.0 license.
The tool provides complete BTB functionality locally, not requiring any node
or server connection outside of Electrum server.

You can install the tool from crates repository or build from sources, located
on [GitHub](https://github.com/BTB-WG/btb).

### Prerequisites

Before installing `btb` in either way, you need to install components used in
its build process.

First, you need to install [cargo](https://doc.rust-lang.org/cargo/).
Minimum supported rust compiler version (MSRV): 1.66, rust 2021 edition.

Next, you need to install developer components, which are OS-specific:

* Linux
  ```
  sudo apt update
  sudo apt install -y build-essential cmake pkg-config
  ```

* MacOS
  ```
  brew install cmake pkg-config
  ```

* Windows: download and install the latest [Visual Studio Redistributable](https://visualstudio.microsoft.com/downloads/)


### Installing from crates.io

```
$ cargo install btb-contracts --all-features
```

Before the final BTB release it might be required to specify concrete 
pre-release version as an argument:

```
$ cargo install btb-contracts --all-features --version 0.10.0
```


### Building from source

By building from the master tip you can get the latest nightly version of
`btb`. Otherwise, you can check [one of our release tags](https://github.com/BTB-WG/btb/tags).

```console
$ git clone https://github.com/BTB-WG/btb
$ cd btb
$ cargo install --path . --all-features
```
