+++
title = "BTB in Rust"
sort_by = "weight"
[extra]
multicolumn = true
+++

**NB: Work in progress – the chapter is not fully written yet and lack
explanation details for the code. <br/>Please contribute at
[our GitHub](https://github.com/BTB-WG/btb-dev.com).**

We will start with showing how a simple RGB20 contract can be written in Rust
using pre-existing schema and no advanced functionality. The rest of the
chapter will guide you through adding more and more customization to it, which
will require creating a custom state data types, writing validation scripts
for them, packing them into a new schema – and providing a custom interface
to this schema.

- <a href="#basics" class="button button-secondary">Writing simple contract</a>
- <a href="#state" class="button button-secondary">Creating custom state</a>
- <a href="#scripts" class="button button-secondary">Scripting validation</a>

* <a href="#schema" class="button button-secondary">Creating custom schema</a>
* <a href="#interface" class="button button-secondary">Doing custom interface</a>
* <a href="#iimpl" class="button button-secondary">Implementing interface</a>

Sample project providing the source code from this chapter can be found in
[examples directory of BTB smart contract compiler repository](https://github.com/BTB-WG/btb-schemata/blob/master/examples/rgb20.rs).
