+++
title = "BTB release v0.10"
date = 2023-04-10
authors = ["Maxim Orlovsky", "Olga Ukolova"]
description = "BTB 0.10 is released, bringing full power of smart contracts to Bitcoin & Lightning"
+++

TL;DR
-----

LNP/BP Standards Association <https://www.lnp-bp.org>, supported by Fulgur 
Ventures, Bitfinex, Hojo Foundation, Pandora Prime, and DIBA, is happy to
announce the release of BTB v0.10 - the next significant milestone in the 
BTB protocol <https://btb-dev.com> which brings full support of smart contracts
to Bitcoin and Lightning. This is the result of a great cross-industry 
long-term collaboration between these bitcoin companies and more than four 
years of extensive development work.

BTB v0.10 can be downloaded and installed as described on <https://btb-dev.com>
website, which also contains a number of user and developer guidelines.
BTB source code can be found on <https://github.com/BTB-WG>


Background of BTB
-----------------

Some of you might remember the announcement of BTB protocol idea back in
2018 [1]: it was an idea of “colored coins” over Lightning by Giacomo
Zucco, based on new concepts developed by Peter Todd - client-side-validation
and single-use-seals.

In 2019 me (Maxim Orlovsky) and Giacomo Zucco formed the LNP/BP Standard
Association, aiming to bring BTB from the concept to production. The initiative
was supported by Bitfinex and Fulgur Ventures. My goal with BTB was not just to
enable assets on Lightning, but that of a much larger scope: to build a
programmability layer for Bitcoin and Lightning, which may unlock other cases
than just tokens: DAOs, decentralized identities and many more things which
bitcoin itself was lacking. This took much longer than was expected, and both 
myself and the LNP/BP Standards Association had gone through very turbulent
times on this road, relying on self-financing for more than a year...

Nevertheless, in 2021 we were able to present both BTB powered with a
Turing-complete virtual machine (AluVM) [2] and BTB had became operational on
Lightning Network [3] using the LNP Node - a complete rust re-implementation of
the Lightning protocol made by me at the Association [4]. Those who are
interested in the history of BTB development and our past releases may refer
to it graphical representation [5] - or navigate through three years of
videos and demos on our YouTube channel
<https://www.youtube.com/@LNPBP/videos>.

Despite 4 years of active development, weekly community calls, talks on
all mainstream bitcoin-only evens and conferences, the awareness about BTB
in the bitcoin community is still very small - and some bitcoin media put
as a requirement for us to submit information about BTB to the bitcoin-dev mail
list, so that they could see the new technology that has been developed - 
so here we are.


BTB v0.10
---------

Today we’d like to announce the next main milestone: **release of BTB v0.10**,
which includes consensus layer, standard library (used by wallets/exchanges
for integration) and a command-line tool.

v0.10 release is a major milestone which brings BTB further to being a 
production-ready system. It introduces the last consensus-breaking changes, 
aiming at keeping future BTB versions fully backward-compatible. It also unlocks
the last features that were required for implementing fully-functional smart 
contracts which may be arbitrary customized by contract developers.

This release brings the support of the following features to BTB:

- #### Global state in BTB contracts
  Now each BTB contract has a global state accessible by a virtual machine
  and clients (wallets etc).

- #### Contract interfaces
  Interfaces, introduced in this version, represent a standard way of
  communicating a diverse range of smart contracts through well-defined APIs.
  Interfaces can be compared to contract ABIs and ERCs in Ethereum world,
  however, unlike in Ethereum, they require neither obligatory standardization
  (as ERCs) nor separate distribution, being always packed together with
  contracts. By using interfaces, wallets and other software can provide a
  semantic-aware UI for the users for working with the contracts - and contract
  developers may add more interfaces to their existing contracts over time
  without the need to update the immutable contract itself.

- #### Strict type system
  Strict types is a new functional data type system with provable
  properties used for the BTB contract state representation and introspection.
  It allows compile-time guarantees on the size of any data, simplifying BTB
  operations on low-end and limited-memory devices like hardware wallets.
  The whole BTB consensus layer is now compiled into strict types, which
  allows formal proofs of the binary compatibility between releases (the
  feature which might have been very useful for bitcoin consensus if it existed
  back in the days of Satoshi). You can learn more about strict types on
  <https://www.strict-types.org>

- #### Contracts in Rust
  Writing and compiling an BTB smart contracts in Rust. Thanks to the strict
  types, it is also possible to compile rust data types right into BTB 
  contracts.

- #### State introspection
  Contracts can introspect their own state in the validation code used by the
  virtual machine, which unlocks the way for writing complex forms of contracts
  working with bitcoin transactions, DLCs and other complex data.

- #### URL-based invoice format
  Previously BTB was using Bech32m-encoded invoices, which were very long,
  not human-readable and couldn't be automatically opened with most of the
  software. The new format is much shorter, easier to verify by the user and
  can be opened automatically as a link with a preconfigured software.

- #### WASM support
  BTB standard library can run without I/O and file system access,
  i.e. can operate inside a web page or a browser plugin.

- #### Tapret descriptors and custom derivation
  BTB uses taproot-based OP_RETURN commitments (in short - tapret), which
  require support on the descriptor level such that wallets could see the 
  transactions with tweaked outputs as those belonging to the wallet descriptor. 
  New version also introduces custom derivation indexes that prevent non-BTB 
  wallets from accidentally spending outputs with BTB assets (and thus -
  destroying assets).

- #### Simplified dependencies
  BTB consensus layer is being shipped with fewer dependencies, improving the 
  stability of API. We have abandoned the dependency on custom bulletproofs 
  implementation from Grin projects. We also do not use rust-bitcoin and 
  rust-miniscript due to their overall API instability and recently discovered 
  bugs; since BTB uses a very small subset of bitcoin functionality it is now 
  implemented as a part of the library with no assumptions about bitcoin 
  consensus layer (like those which halted rust-bitcoin powered software when 
  Burak's hack had happened last year).

- #### Simplified integration
  Many operations that previously required multiple API calls, as well as
  cross-language encoding of complex data structures now work with a
  single API call. BTB contract state is represented as a JSON object and
  can be serialized across different languages without a hassle.

- #### Simplified UX
  Previously, to use BTB, a wallet or a user had to run the BTB Node, interface
  it through RPC (or cli tool) - and use a number of other libs and command-line 
  tools to perform most of the operations on PSBTs etc. With the new release 
  this complex stack was replaced by a single library API and a command-line 
  tool `btb`, which operate like a swiss knife for BTB user (and it can be 
  compared to the way `git` works). BTB Node still can be run by users on their
  home servers, but is not obligatory for using BTB anymore.

### Migration notes

There is no migration from contracts issued on BTB v0.9 to the future versions.
All assets have to be re-issued; asset holders can contact asset issuers to
provide them with a newly re-issued contracts and assets matching the assets
from v0.9.

BTB v0.10 can be downloaded and installed as described on [https://btb-dev.com]
(https://btb-dev.com) website, which also contains a number of user and
developer guidelines. BTB source code can be found on https://github.com/BTB-WG


Roadmap after v0.10
-------------------

With this release the future development of the core BTB technology (at in its
consensus layer) becomes gradually ossified, as the cases of 
client-side-validated systems upgrades are more complex to coordinate than
those of blockchain layer 1. Also, the normal understanding of soft-forks and
hard-forks do not apply to upgrades in layer 2 and 3. So we found a way
for backwards-compatible upgrades, which we call “fast-forwards”, where users
keep their assets issued under the older versions that can always operate and be
accepted by the users of any other future version. However, the users of a newer
version will be restricted in transferring their assets only to the users of the
same or more recent version (but they can always ask recipients to upgrade their
software). We have a number of features planned for the future fast-forwards:

- full support of bitcoin layer 1 and channel state introspection;
- inter-contract interaction;
- bulletproofs++ support;
- zero-knowledge-based optimizations of the client-side-validated history.

We're also working on the design of a layer 1 which will be perfect for the
client-side-validated applications (“how to design a blockchain today if we
knew about client-side-validation/single-use-seals”). This should be very
compact (order of one signature per block) ultra-scalable (theoretically
unlimited no of tx in a block) chain which can run systems like BTB - with
Bitcoin UTXO set migrated into BTB operating on both bitcoin blockchain and
this new chain (we code-name it “sigchain”). However, these are quite early
developments with a number of unsolved tradeoffs and challenges; if there is
an interest on this topic here we can start a different discussion thread
on the matter.


Software and integrations
-------------------------

Companies, which are a part of the LNP/BP Standards Association, as well
as other independent vendors are already working on upgrading their software
to v0.10. This includes (but not limited to):

- MyCitadel wallet (iOS, Desktop)
- Iris wallet (Android) from BTB team inside Bitfinex
- BitMask (Web browser plugin) from DIBA
- LNP Node with BTB support - lightning node from the LNP/BP Standards Association
- RGBEx.io - website listing BTB assets and contracts,
  using pseudonymous credentials (public key + signatures)
- BTB Tools library - SDK based on BitcoinDevKit for BTB wallet integration
- LightningDevKit with BTB support - again by BTB team in Bitfinex
- Core Lightning BTB plugin

LNP/BP Standards Association will focus its further development activity
around these three areas:

- Completing BTB documentation, specification and helping public audits of the
  technology. Right now we have a nearly-complete BTB whitepaper [6] a codified
  standards [7]
- Lightning network support for complex BTB smart contracts - the thing we name
  #BiFi (Bitcoin finance) [8]. It includes further development of Storm -
  a decentralized data storage & messaging network on top of Lightning, that we
  presented last year.
- BTB toolchain, which includes a new high-level functional smart contracting
  language called Contractum (<https://www.contractum.org>) and other tools
  which will simplify the life of BTB devs.


Sources of information
----------------------

We have already witnessed some actors distributing misinformation about
non-existing products released with/on BTB even before the official releases of
some BTB components happened. Thus, we advise all media people to always check
the official sources before publishing information about the BTB protocol.

All releases and major things are being announced on:
* Official website of the protocol <https://btb-dev.com>,
  community <https://rgbfaq.com> and LNP/BP Standards Association
  <https://lnp-bp.org>.
* Twitter of the Association: <https://twitter.com/lnp_bp>
* Community telegram channel: <https://t.me/rgbtelegram>

Other websites are not in control of the BTB protocol developers and are not
open-source and should not be considered to be trusted sources of information.


[1]: https://www.youtube.com/watch?v=xHWxtmgQP94
[2]: https://www.youtube.com/watch?v=Mma0oyiVbSE
[3]: https://www.youtube.com/watch?v=6Svmh0OQVf4
[4]: https://github.com/LNP-WG/lnp-node
[5]: https://twitter.com/dr_orlovsky/status/1640833926456307714/photo/1
[6]: https://blackpaper.btb-dev.com
[7]: https://standards.lnp-bp.org
[8]: https://www.youtube.com/watch?v=DtkTE6m0zio_
