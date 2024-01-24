# CHI_DeepTreeSketch

This is the official repository of paper "DeepTreeSketch: Neural Graph Prediction for Faithful 3D Tree Modeling from Sketches. Zhihao Liu, et al. 2024".

## 1. Tree Dataset
In the very beginning, we implemented a very comprehensive **Parametric l-system algorithm** for creating diverse high-quality 3D tree models automatically as the training dataset. This algorithm contributes the majority (approx. 90%) of our training set, while the rest are the real-world trees reconstructed from point clouds and images.

Please download our dataset through this [[link]](https://vcc.tech/research/2021/TreePartNet)  (password: xyz)

#### - More details on L-system Algorithm:
**$\bullet$ Noted that:** apart from our CHI submission, **my implemented algorithm** has been also used by a few top-tier papers to generate training dataset, including several recent **``SIGGRAPH-level``** papers, such as:

> **TreePartNet: Neural Decomposition of Point Clouds for 3D Tree Reconstruction.**
>
> **SIGGRAPH Asia 2021** (ACM Transactions on Graphics). [[Papar]](https://vcc.tech/research/2021/TreePartNet) 


Please see their Acknowledgement section for some proof that their authors borrowed my codes in their paper:

![system](https://github.com/RyuZhihao123/CHI_DeepTreeSketch/blob/main/Figures/0-ack.png)

**$\bullet$** In our CHI submission, we synthesized a large tree dataset with 12 different species. Here are some examples in our dataset:

![system](https://github.com/RyuZhihao123/CHI_DeepTreeSketch/blob/main/Figures/1-tree-exps-1.png)

**$\bullet$** Since the Parametric L-system is a very complex algorithm that cannot be briefly summarized in a short manner, please refer to these relevant papers for more details on its mechanism:
[[XXX et al.]](https://vcc.tech/research/2021/TreePartNet)  [[YYY et al.]](https://vcc.tech/research/2021/TreePartNet) [[ZZZ et al.]](https://vcc.tech/research/2021/TreePartNet) 


## 2. Codes and Software:

We are currently working on a online version software that enables people from all over the world can freely explore our modeling system.
Ideally, we will publish the system by March (around after ACM UIST's deadline).
