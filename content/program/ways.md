+++
weight = 30
title = "Ways to program BTB"
[extra]
bg-color = "purple"
multicolumn = true
+++

Today, there are two main ways for programming BTB smart contracts: using
rust-based BTB domain-specific language and with a specially-designed functional
smart contract language named **Contractum**. Unlike many other blockchain-based
smart contract systems, BTB also allows to create contracts without writing any
code at all – even for complex contracts like NFTs, identities, DAOs etc.

* ### Zero-code contracts

  Because of the use of contract schemata, most of BTB contract types can be
  issued without writing even a line of code. All you need is to find a schema
  and use command-line tools or GUI-based wallets to issue your contract.

  <a href="/power-user/#issue" class="button button-secondary">Issue a contract with no code</a>

* ### BTB Rust DSL

  The simplest way of creating a new BTB schema or interface is to use Rust. 
  You can directly compile arbitrary rust data to be part of BTB contract state,
  and you use macro-based DSL to define new schemata and interfaces. You can 
  export contracts, schema or interface into a binary form – or save them as 
  Base65-armored text for further distribution.

  <a href="/program/rust" class="button button-secondary">Program BTB in Rust</a>

* ### Contractum

  Contractum is the forthcoming declarative language for writing safe and
  easy-to-audit smart contracts for BTB. Contractum is being under an active
  development and we plan to have it released by the end of the year. Today
  you may preview how writing BTB contracts in Contractum may look like in a
  future.

  <a href="/program/contractum" class="button button-secondary">Preview Contractum</a>
