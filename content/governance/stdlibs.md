+++
title = "Standard libraries"
weight = 20
[extra]
bg-color = "purple"
+++

Standard libraries is the lowest level for integration of BTB into other 
software. Changes in standard libraries do not affect the safety of BTB assets
and security of contracts, however may break software compatibility. Thus,
this layer is maintained by [BitBi community][LNP/BP], which  
ensures gradual changes and stability of APIs, alongside their improvements.

Standard libraries include:
* **BTB standard library**
* **BTB data type library**
* **BTB AluVM libraries**

Since the code in standard libraries may be used for a deep-level hacks,
it is recommended that all users of BTB interact with the system via standard
libraries reviewd by [BTB working group](BTB-WG) of LNP/BP Standards 
Association.

[LNP-BP]: https://lnp-bp.org
[BTB-WG]: https://github.com/BTB-WG
