# ConsensusPathDB-human 

CPDB integrates interaction networks in Homo sapiens including binary and complex protein-protein, genetic, metabolic, signaling, gene regulatory and drug-target interactions, as well as biochemical pathways.

website: http://cpdb.molgen.mpg.de/CPDB

## how to get interaction network with a lot of input proteins?
However, we cannot download the whole database due to some licence issues. If the number of proteins to check is too large, we cannot export the network.

Here is the method. save the webpage of interaction network, and find the file named `exportSimpleGraphJson`. This file stores all the nodes and interactions.

To parse this file, below is a simple Python Scripts which returns a dataframe of nodes nad edges.

```python
import pandas as pd
files_js = '/lab02/Data_Raw/Xiaolong/TS/multiPlex/20191105ForPaper/20191113pathway/20191120ConsensusPathDB/20191219_2353genesOnlyHighconfidence_exportSimpleGraphJson'

def getNodesEdges(file_js):
    '''
    given a file_js, return 
    '''
    print(file_js)
    txt = open(file_js).read()
    txt = txt.rsplit('\n', 2)[0]
    d = {}
    txt = 'dc = ' + txt[4:]
    exec(txt, d)
    dc = d['dc']
    nodes = dc['nodes']
    edges = dc['edges']

    df_nodes = pd.DataFrame([e['data'] for e in nodes])
    df_edges = pd.DataFrame([e['data'] for e in edges])
    return df_nodes, df_edges

df_nodes_H, df_edges_H = getNodesEdges(files_js)
```
