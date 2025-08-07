# Tika Agent

The Tika agent converts documents from their native format to a text representation.&#x20;

> Tika is an open-source component licenced under the Apache Licence. It supports a myriad of file formats. [See their site for more information.](https://tika.apache.org/)

It is most efficient to co-host a Tika agent on each enrichment server. The Tika agent can be intense on CPU utilisation and memory consumption. It works closely with the enrichment agent and the need to ship the binary file is inherently network intensive.&#x20;

The Tika code base includes timeout and long running process protection. This provides robust stability protection during the conversion process.
