# CHI24_DeepTreeSketch




This is the official repository of paper "DeepTreeSketch: Neural Graph Prediction for Faithful 3D Tree Modeling from Sketches. [Zhihao Liu](https://ryuzhihao123.github.io/), et al., ACM CHI, 2024".

If interested, you could also check my [homepage](https://ryuzhihao123.github.io/) for my other projects and codes. ^_^

In current stage, we first mainly shared our dataset [[link]](https://vcc.tech/research/2021/TreePartNet) to provide more information to address some concerns, the entire source codes will be released right after the final acceptance (now is with conditional acceptance).


## 1. Tree Dataset
In the very beginning, we implemented a very comprehensive **Parametric l-system algorithm** for creating diverse high-quality 3D tree models automatically as the training dataset. 
This algorithm contributes the majority (approx. 90%) of our training set, while the rest are the real-world trees reconstructed from point clouds and images.

**Dataset Link:** Please download our dataset of tree skeletons through this [[link]](https://vcc.tech/research/2021/TreePartNet)  (password: xyz)

### (a) Basic information on our L-system algorithm:

**$\bullet$** ${\color{red}\text{Note that, apart from our CHI submission, }}$ **``my implemented algorithm``**${\color{red}\text{ has been also used}}$ ${\color{red}\text{by a few Top-tier papers}}$ ${\color{red}\text{to generate training dataset, }}$
${\color{red}\text{including several recent }}$ **``SIGGRAPH-level``** ${\color{red}\text{papers. For example:}}$


> **TreePartNet: Neural Decomposition of Point Clouds for 3D Tree Reconstruction.**
>
> **SIGGRAPH Asia 2021** (ACM Transactions on Graphics). [[Paper]](https://dl.acm.org/doi/abs/10.1145/3478513.3480486) 

${\color{red}\text{Please see their}}$ **``Acknowledgement section``** ${\color{red}\text{for some proof that their authors borrowed my codes and data in their paper:}}$

<div align=center>
<img src="https://github.com/RyuZhihao123/CHI_DeepTreeSketch/blob/main/Figures/0-ack.png" width = "700" alt="ack" align=center />
</div>
<br/><br/>

**$\bullet$** In this algorithm, each species corresponds to one predefined string-based grammar set (a collection of production rules) which biologically defines a series of self-similar substructures of plants. 
The algorithm works as a parallel rewriting system to recursively expand each symbol into a longer production rule to iteratively form the tree structures.
We can obtain any number of different tree variants of the same species by adjusting parameters and randomly selecting the production rules per iteration. 

Since the Parametric L-system is a quite complicated algorithm that cannot be briefly summarized in a short manner, please refer to these relevant papers for more details on its mechanism:
[[XXX et al.]](https://vcc.tech/research/2021/TreePartNet)  [[YYY et al.]](https://vcc.tech/research/2021/TreePartNet) [[ZZZ et al.]](https://vcc.tech/research/2021/TreePartNet) 


### (b) Format of our synthesized data:

In our CHI submission, we synthesized a large tree dataset with 12 different species in total. 
Here are some examples in our dataset:

<div align=center>
<img src="https://github.com/RyuZhihao123/CHI_DeepTreeSketch/blob/main/Figures/1-tree-exps-1.png" width = "700" alt="ack" align=center />
</div>

<br/>

Since our proposed neural network (TGP-Net) is designed to process the tree skeletons, we mainly store the branching structures (skeletons) in the dataset, to help reduce the memory footprint.

In our dataset, **each ``.skel`` file** records the full branching structure of a 3D tree skeleton, and corresponds to one training sample. The ``.skel`` file is organized in JSON format, thus you can use any JSON loader to easilly decode its structure. 

Below is a simple example used to explain the data format:
```c
// Tree nodes (total count=xyz):
{type: "treenode", node_id: 0, pos: [0.000, 0.000, 0.000], branch_id: 0, parent_id: -1, children_ids: [1]},
{type: "treenode", node_id: 1, pos: [0.001, 0.012, 0.002], branch_id: 0, parent_id: 0, children_ids: [2, 3]},
{type: "treenode", node_id: 2, pos: [-0.004, 0.180, 0.000], branch_id: 0, parent_id: 1, children_ids: [4, ]},
{type: "treenode", node_id: 3, pos: [-0.023, 0.262, 0.00], branch_id: 0, parent_id: 2, children_ids: [5]},
{type: "treenode", node_id: 3, pos: [-0.023, 0.262, 0.00], branch_id: 0, parent_id: 2, children_ids: [5]},
......
// All the leaves (total count=xyz):
{type: "leaf", leaf_id: 0, parent_node_id: 72, pos: [0.321, 0.682, 0.407], orientation: []},
{type: "leaf", leaf_id: 1, parent_node_id: 76, pos: [0.321, 0.682, 0.407], orientation: []},
```

Here, each row with **``type="treenode"``** represents one single tree node, recording its necessary attributes such as: *coordinate* and *edge connections*. 

- ``node_id``: The index of this node. It starts from 0.
- ``pos``: The global 3D position of this node. In our dataset, the height of all the trees are normalized to 1.0 in advance.
- ``branch_id``: The index of the long branch that this node belongs to. (not used in this project.)
- ``parent_id``: The index of the parent tree node of the current node.
- ``children_ids``: The index of all the children nodes of the current node. It's an array since one tree node may have multiple children nodes.

The data file also additionally contains the information on leaves.
The rows with **``type="leaf"``** are all the leaves of this tree, recording the tree node ID which it attraches to, and orientation, etc. 
Note that, our proposed TGP-Net doesn't use these leaf information. But you can freely use them in your own project if needed. ^_^


## 2. Codes and Software:

**The full source code** will be released after the final official acceptance.

Additionally, now we are also working on a **Online-version software** that enables people from all over the world to freely explore our modeling system at any time. 
Currently, we are trying to configure our neural network (TGP-Net) to run on a machine with public accessible IP address permanently. Ideally, this online system will be also uploaded to some Software/Game Stores (e.g., Steam or XBox) for free experience, approximately in April (around after UIST's deadline).


<div align=center>
<img src="https://github.com/RyuZhihao123/CHI_DeepTreeSketch/blob/main/Figures/2-system.png" width = "700" alt="ack" align=center />
</div>


