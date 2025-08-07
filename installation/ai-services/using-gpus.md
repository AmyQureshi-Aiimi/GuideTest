# Using GPUs

To use GPUs for enrichment steps and model service providers, you need to export your service registration config and set the device parameter.

### For 'device':

* -1 is CPU and 0 is the first GPU.
* 'cpu' is CPU and 'cuda:0' is the first GPU.

### For 'device\_str'

* 'cpu' is CPU and 'cuda:0' is the first GPU.
