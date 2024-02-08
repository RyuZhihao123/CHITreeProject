# CHI24_DeepTreeSketch




This is the official repository of paper "DeepTreeSketch: Neural Graph Prediction for Faithful 3D Tree Modeling from Sketches. [Zhihao Liu](https://ryuzhihao123.github.io/), et al., ACM CHI, 2024".

If interested, you could also check my [homepage](https://ryuzhihao123.github.io/) for my other projects and codes. ^_^

In current stage, **we first mainly shared our dataset** [[download link]](https://github.com/RyuZhihao123/CHI_DeepTreeSketch/) to provide more information to address some concerns, the entire **source codes** will be released right after some cleaning-ups and final official acceptance.


## 1. Tree Dataset
In the very beginning, we implemented a very comprehensive **Parametric l-system algorithm** for creating diverse high-quality 3D tree models automatically as the training dataset. 
This algorithm contributes the majority (approx. 90%) of our training set, while the rest are the real-world trees reconstructed from point clouds and images.

**$\bullet$** **Dataset Link:** Please download our dataset of tree skeletons through this [[download link]](https://github.com/RyuZhihao123/CHI_DeepTreeSketch/).


### (a) Basic information about our L-system algorithm:

**$\bullet$** **Note that, apart from our CHI submission, ``my implemented algorithm`` has also been used by several top-tier ``SIGGRAPH-level papers``** to help generate the training dataset of 3D trees. For example: 

<!--
**$\bullet$** ${\color{magenta}\text{\normalsize \textbf{Note that}, apart from our CHI submission, }}$ **``my implemented algorithm``**${\color{magenta}\text{ has been also used}}$ ${\color{magenta}\text{by a few Top-tier papers}}$ ${\color{magenta}\text{to generate the training dataset of 3D trees, }}$
${\color{magenta}\text{including several recent }}$**``SIGGRAPH-level``** ${\color{magenta}\text{papers. For example:}}$
-->


> **TreePartNet: Neural Decomposition of Point Clouds for 3D Tree Reconstruction.**
>
> **SIGGRAPH Asia 2021** (ACM Transactions on Graphics). [[Paper]](https://dl.acm.org/doi/abs/10.1145/3478513.3480486) 

${\color{magenta}\text{Please see their}}$ **``Acknowledgement section``** ${\color{magenta}\text{for some proof that their authors used my codes or data in their paper:}}$

<div align=center>
<img src="https://github.com/RyuZhihao123/CHI_DeepTreeSketch/blob/main/Figures/0-ack.png" width = "700" alt="ack" title="dasdasdsa title" align=center />
<br/><center><b>Fig. 1. Several SIGGRAPH-level papers also borrowed my tree modeling algorithm to synthesize 3D tree dataset, due to the strong capability of my implementation.</b></center>
</div>
<br/>

**$\bullet$** In this algorithm, each species corresponds to one predefined string-based grammar set (a collection of production rules) which biologically defines a series of self-similar substructures of plants. 
The algorithm works as a parallel rewriting system to recursively expand each symbol into a longer production rule to iteratively form the tree structures.
We can obtain any number of different tree variants of the same species by adjusting parameters and randomly selecting the production rules per iteration.

Nowadays, due to the strong capability of parametric L-system, this algorithm has become one of the most popular approach to generate realistic 3D tree models for games or movies. 
And it has formed a huge algorithm set that contains many variants with unique features.

Considering that the Parametric L-system is not the main focus of our paper, and is a quite complicated algorithm framework that cannot be briefly summarized in a short manner, please refer to these relevant papers or articles for more details on its mechanism: 
[[Wikipedia]](https://en.wikipedia.org/wiki/L-system)
[[Prusinkiewicz et al. 96]](http://algorithmicbotany.org/papers/sigcourse.2003/2-1-lsystems.pdf) 
[[Sun et al. 09]](https://www.researchgate.net/publication/216337877_Intelligent_Tree_Modeling_Based_on_L-system) 
[[Lee et al. 23]](https://dl.acm.org/doi/full/10.1145/3627101?casa_token=VqUTDXPJQSsAAAAA%3A2D6naUDWtbzLoSAaVBqApxomg1W_MQ0gEagUY7c30HFNU8Tiua9iYI1N1RRhpf8E3t7vvF1OsSmE5w)
[[Prusinkiewicz et al. 12]](https://scholar.google.ca/citations?view_op=view_citation&hl=en&user=pjH7e8IAAAAJ&citation_for_view=pjH7e8IAAAAJ:TIZ-Mc8IlK0C) 
[[ZZZ et al.]](https://link.springer.com/book/10.1007/978-1-4757-1428-9).


### (b) How to use our synthesized dataset:

In our CHI submission, we synthesized a large tree dataset with 12 different species in total. 
Here are some examples in our dataset:

<div align=center>
<img src="https://github.com/RyuZhihao123/CHI_DeepTreeSketch/blob/main/Figures/1-tree-exps-1.png" width = "700" alt="ack" align=center />
</div>

<br/>

Since our proposed neural network (TGP-Net) is designed to process the tree skeletons, we mainly store the branching structures (skeletons) in the dataset, to help reduce the memory footprint.

- In our dataset, **each ``.skel`` file** records the full branching structure of a 3D tree skeleton, and corresponds to one training sample. The **``.skel`` file** is organized in JSON format, thus you can use any JSON loader to easilly decode its structure. 

     Below, we use a simple example to explain the data format in detail:
```c
{type="header", name="tree_0001.skel", species_id = 6, treenode_num = 1234, leaf_num = 1971},

// Tree nodes (total count=1234):
{type: "treenode", node_id: 0, pos: [0.000, 0.000, 0.000],  parent_id: -1, children_ids: [1], radius: 0.027861, branch_id: 0},
{type: "treenode", node_id: 1, pos: [0.000, 0.148, 0.000],  parent_id: 0, children_ids: [2, 3], radius: 0.025100, branch_id: 0},
{type: "treenode", node_id: 2, pos: [-0.004, 0.278, 0.002], parent_id: 1, children_ids: [4, 5, 6], radius: 0.020372, branch_id: 0},
{type: "treenode", node_id: 3, pos: [-0.002, 0.407, 0.012], parent_id: 2, children_ids: [7, 8], radius: 0.018353, branch_id: 1},
{type: "treenode", node_id: 4, pos: [0.034, 0.368, -0.025], parent_id: 2, children_ids: [9, 10, 11], radius: 0.016534, branch_id: 2},
......
// All the leaves (total count=1971):
{type: "leaf", leaf_id: 0, pos: [-0.269, 0.894, 0.244],  orientation: [-0.861, 0.506, 0.040], size_scale: 0.041084},
{type: "leaf", leaf_id: 1, pos: [-0.030, 0.686, -0.012], orientation: [-0.576, -0.749, -0.325], size_scale: 0.042160},
```

- The first row with **``type="treenode"``** summarizes the overall information of this tree sample, such as, its species and the number of tree nodes, etc.

- Each row with **``type="treenode"``** represents one single tree node, recording its necessary attributes such as: *coordinate* and *edge connections*. 

    - ``node_id``: The index of this node. It starts from 0.
    - ``pos``: The global 3D position of this node. In our dataset, the height of all the trees are normalized to 1.0 in advance.
    - ``parent_id``: The index of the parent tree node of the current node.
    - ``children_ids``: The index of all the children nodes of the current node. It's an array since one tree node may have multiple children nodes.
    - ``radius``: The branch radius at this node.
    - ``branch_id``: The index of the long branch that this node belongs to. (not used in this project.)


- The data file also additionally contains the information on leaves.
The rows with **``type="leaf"``** are all the leaves of this tree, recording its orientation and other attributes. 
Note that, our proposed TGP-Net doesn't use these leaf information in practice. But you can freely use them in your own project if needed. ^_^



## 2. Codes and Software:

In current stage, we first mainly shared our dataset [[link]](https://github.com/RyuZhihao123/CHI_DeepTreeSketch/) to provide more information to address some concerns, the entire source codes will be released right after some cleaning ups and the final official acceptance.


Additionally, as a bonus, we are now working on a **Online-version software** (Web version using Javascript + WebGL) as well, which will enable people from all over the world to freely explore our modeling system at any time. 
Thus, we are currently trying to configure our neural network (TGP-Net) to **permanently** run on a GPU workstation with public accessible IP address. Ideally, this online system will be also launched approximately in April (basically after UIST's deadline).


<div align=center>
<img src="https://github.com/RyuZhihao123/CHI_DeepTreeSketch/blob/main/Figures/2-system.png" width = "400" alt="ack" align=center />
</div>


