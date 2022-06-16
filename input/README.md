# Datasets
This directory contains example datasets.
It can also be used to store new input data files.
There are currently very small toy datasets and one real dataset.

## File formats
### Node file
Node files include a header row and rows providing attributes for each node.
The first column is for the node identifier and has the header value `NODEID`.
All other columns specify additional node attributes such as prizes.
For example:
```
NODEID	prize	sources	targets
A	1.0		True
B	3.3	True	
C	2.5		True
D	1.9	True	True
```

A secondary format provides only a list of node identifiers, as in the example `sources.txt`.
This format may be deprecated.

### Edge file
Edge files do not include a header row.
Each row lists the two nodes that are connected with an undirected edge and a weight for that edge.
Directed edges are not currently supported.
The weights are typically in the range [0,1] with 1 being the highest confidence for the edge.

For example:
```
A	B	0.98
B	C	0.77
```

## Toy datasets
The following files are very small toy datasets used to illustrate the supported file formats
- `alternative-network.txt`
- `alternative-targets.txt`
- `network.txt`
- `node-prizes.txt`
- `sources.txt`
- `targets.txt`

## Epidermal growth factor receptor (EGFR)
This dataset represents protein phosphorylation changes in response to epidermal growth factor (EGF) treatment.
The network includes protein-protein interactions from [iRefIndex](http://irefindex.org/) and kinase-substrate interactions from [PhosphoSitePlus](http://www.phosphosite.org/).
The files are originally from the [Temporal Pathway Synthesizer (TPS)](https://github.com/koksal/tps) repository.
They have been lightly modified for SPRAS by lowering one edge weight that was greater than 1, removing a PSEUDONODE prize, and converting all edges to undirected edges.
All proteins with phosphorylation-based prizes are also labeled as targets.
The only source is EGF.

If you use any of the input files `tps-egfr-prizes.txt` or `phosphosite-irefindex13.0-uniprot.txt`, reference the publication

[Synthesizing Signaling Pathways from Temporal Phosphoproteomic Data](https://doi.org/10.1016/j.celrep.2018.08.085).
Ali Sinan K�ksal, Kirsten Beck, Dylan R. Cronin, Aaron McKenna, Nathan D. Camp, Saurabh Srivastava, Matthew E. MacGilvray, Rastislav Bod�k, Alejandro Wolf-Yadlin, Ernest Fraenkel, Jasmin Fisher, Anthony Gitter.
*Cell Reports* 24(13):3607-3618 2018.

If you use the network file `phosphosite-irefindex13.0-uniprot.txt`, also reference iRefIndex and PhosphoSitePlus.
The TPS [publication](https://doi.org/10.1016/j.celrep.2018.08.085) describes how the network data and protein prizes were prepared.
