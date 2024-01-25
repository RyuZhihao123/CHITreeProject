# CHI24_DeepTreeSketch

This is the official repository of paper "DeepTreeSketch: Neural Graph Prediction for Faithful 3D Tree Modeling from Sketches. [Zhihao Liu](https://ryuzhihao123.github.io/), et al., ACM CHI, 2024".

If interested, please check my [homepage](https://ryuzhihao123.github.io/) for my other projects and codes.

In this stage we first shared our tree dataset to provide more information to address some concerns, the full source codes will be released right after the final acceptance.

## 1. Tree Dataset
In the very beginning, we implemented a very comprehensive **Parametric l-system algorithm** for creating diverse high-quality 3D tree models automatically as the training dataset. 
This algorithm contributes the majority (approx. 90%) of our training set, while the rest are the real-world trees reconstructed from point clouds and images.

**Dataset Link:** Please download our dataset through this [[link]](https://vcc.tech/research/2021/TreePartNet)  (password: xyz)

### (a) Basic information on our L-system algorithm:
**$\bullet$ Noted that**, apart from our CHI submission, **``my implemented algorithm``** have been also used by a few top-tier papers to generate training dataset, including several recent **``SIGGRAPH-level``** papers, such as:

> **TreePartNet: Neural Decomposition of Point Clouds for 3D Tree Reconstruction.**
>
> **SIGGRAPH Asia 2021** (ACM Transactions on Graphics). [[Papar]](https://vcc.tech/research/2021/TreePartNet) 


Please see their **``Acknowledgement section``** for some proof that their authors borrowed my codes and data in their paper:

<div align=center>
<img src="https://github.com/RyuZhihao123/CHI_DeepTreeSketch/blob/main/Figures/0-ack.png" width = "800" alt="ack" align=center />
</div>
<br/><br/><br/>

**$\bullet$** In this algorithm, each species corresponds to one predefined string-based grammar set (a collection of production rules) which biologically defines a series of self-similar substructures of plants. 
The algorithm works as a parallel rewriting system to recursively expand each symbol into a longer production rule to iteratively form the tree structures.
We can obtain any number of different tree variants of the same species by adjusting parameters and randomly selecting the production rules per iteration. 

Since the Parametric L-system is a fairly complicated algorithm that cannot be briefly summarized in a short manner, please refer to these relevant papers for more details on its mechanism:
[[XXX et al.]](https://vcc.tech/research/2021/TreePartNet)  [[YYY et al.]](https://vcc.tech/research/2021/TreePartNet) [[ZZZ et al.]](https://vcc.tech/research/2021/TreePartNet) 


### (b) Format of our synthesized data:
**$\bullet$** In our CHI submission, we synthesized a large tree dataset with 12 different species. Here are some examples in our dataset:

![examples](https://github.com/RyuZhihao123/CHI_DeepTreeSketch/blob/main/Figures/1-tree-exps-1.png)


**$\bullet$** In our dataset, each ``".tree"`` file corresponds to one tree skeleton sample. One such file is compossed of a set of lines. Below is a simple example:
```

```
> node_id x y z parent_id [children_ids]


## 2. Codes and Software:

We are currently working on a online version software that enables people from all over the world can freely explore our modeling system.
Ideally, we will publish the system by March (around after ACM UIST's deadline).
