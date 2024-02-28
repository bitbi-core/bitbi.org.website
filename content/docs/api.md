+++
title = "API references"
weight = 30
[extra]
anchor = "api"
multicolumn = true
bg-color = "white"
+++

### Consensus level APIs

| Library          | Description                                                                           | API Reference                      | Source code                                                                                              |
|------------------|---------------------------------------------------------------------------------------|------------------------------------|----------------------------------------------------------------------------------------------------------|
| Commit-verify    | Commit-verify cryptographic schemes and multi-protocol commitments (LNPBP-4 standard) | <https://docs.rs/commit_verify>    | [LNP-BP/commit_verify](https://github.com/LNP-BP/client_side_validation/tree/master/commit_verify)       |
| Single-use-seals | Single-use-seals abstract APIs                                                        | <https://docs.rs/single_use_seals> | [LNP-BP/single_use_seals](https://github.com/LNP-BP/client_side_validation/tree/master/single_use_seals) |
| BP DBC           | Deterministic bitcoin commitments on bitcoin protocol                                 | <https://docs.rs/bp-dbc>           | [BP-WG/bp-dbc](https://github.com/BP-WG/bp-core/tree/master/dbc)                                         | 
| BP Seals         | Single-use-seals with bitcoin protocol                                                | <https://docs.rs/bp-seals>         | [BP-WG/bp-seals](https://github.com/BP-WG/bp-core/tree/master/seals)                                     | 
| BTB Core         | Main consensus code for BTB                                                           | <https://docs.rs/btb-core>         | [BTB-WG/btb-core](https://github.com/BTB-WG/btb-core)                                                    |

### Integration level APIs

| Library          | Description                                                                                   | API Reference                   | Source code                                                            |
|------------------|-----------------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------|
| BTB Standard Lib | BTB standard library for working with smart contracts on the lowest level                     | <https://docs.rs/btb-std>       | [BTB-WG/btb-std](https://github.com/BTB-WG/btb-wallet/tree/master/std) |
| BTB Wallet Lib   | Wallet-integration library for WASM apps providing BTB invoices and PSBT functionality        | <https://docs.rs/btb-wallet>    | [BTB-WG/btb-wallet](https://github.com/BTB-WG/btb-wallet)              |
| BTB Lib          | High-level BTB integration library for mobile & desktop apps providing FS-based stash storage | <https://docs.rs/btb-contracts> | [BTB-WG/btb](https://github.com/BTB-WG/btb)                            |
