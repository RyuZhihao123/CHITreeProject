# CHI24_TreeProject


This is the site for the paper "DeepTreeSketch: Neural Graph Prediction for Faithful 3D Tree Modeling from Sketches. **[Zhihao Liu](https://ryuzhihao123.github.io/)**, et al., **ACM CHI**, 2024". 


🎦 **Demo Videos:** [[Preview Video (30s)]](https://drive.google.com/file/d/1Kvj47Ckju43i9IpJ6OjWzE2ZkxVbOFTX/view?usp=sharing)
[[Full Video (3min)]](https://drive.google.com/file/d/1YNooKZMfFbwdyMv2JzuzhmUu7tJSMahL/view?usp=sharing).

📙 **Paper:** [[Paper PDF]](https://drive.google.com/file/d/1hyoL_i8CPeNgi1NJd1Ay5osbsw-mATt9/view?usp=drive_link).

In this repository, you can find and download the software toolkits we developed for both interactive tree design and automated data generation, as well as the training dataset.

<!-- 
<a id="Chapter1"/></a>
This repository contains the following stuffs:
- **@ Dataset Generator:** The first content in this repo is to respond the concerns from Reviewers on how to get 3D tree dataset. Thus, we released the **softwares that we developed** for automatically generating the 3D tree models for training the network. Please go to <a href="#Chapter1">[Chapter 1]</a> to download them.
- **@ Software of DeepTreeSketch:** We releasesd the client of our DeepTreeSketch in <a href="#Chapter2">[Chapter 2]</a> (it needs to connect our server via internet).
- **@ Software of my old sketching system:** This is another option. When you cannot access our server but you're very urgent to design tree models, please try this more light-weight software of mine (<a href="https://github.com/RyuZhihao123/TreeDesigner17">[Link]</a>) which was developed several years ago by myself. Compared to our DeepTreeSketch, my old version software can be directly used offline without using neural networks, but please also understand its results are with relatively lower quality and fidelity than our new DeepTreeSketch system. 
-->



# 1. Tree Dataset Generator.


In the very beginning, we implemented a comprehensive **Parametric l-system algorithm** ffor creating diverse high-quality 3D tree models automatically as the training dataset. 
This algorithm contributes the majority of our training set, while the rest are the real-world trees reconstructed from point clouds and images.

- **Dataset Generator:** We have developed a series of software in advance to help us synthesize diverse high-quality 3D tree models from scratch or real-world data. **Please download my software for dataset generation from: <a href="#tool1">[Tool-1: Auto Gen]</a> and <a href="#tool2">[Tool-2: Gen from Real-data]</a>.** You can freely play with these tools to generate new 3D tree models. ⭐ 

- **Dataset Link:** You can also download the original experimental dataset through this [[link (version: 20220509)]](https://univtokyo-my.sharepoint.com/:u:/g/personal/1487479010_utac_u-tokyo_ac_jp/EYL59bp6A2hMsjYFnHeDZaUBVow5KimE9KsTjwQfsSPMGw?e=LUjHsy), which contains 1800 samples of various tree skeletons.

## (a) Foreword about Our Dataset Creation Algorithms.

:hearts: Note that, apart from our CHI submission, <ins>**My implemented algorithm has also been used by several top-tier SIGGRAPH-level Papers</ins> to help them generate the training dataset of 3D trees.** For example: 


> **TreePartNet: Neural Decomposition of Point Clouds for 3D Tree Reconstruction.**
>
> **SIGGRAPH 2021** (ACM Transactions on Graphics). [[Paper]](https://dl.acm.org/doi/abs/10.1145/3478513.3480486) 

Please see their **``Acknowledgement section``** below for some proof that their authors used my codes to get training data for their paper:
<!--${\color{red}\text{Please see their}}$ **``Acknowledgement section``** ${\color{red}\text{for some proof that their authors used my codes or data in their paper:}}$-->
<a id="tool1"/></a>
<div align=center>
<img src="https://github.com/RyuZhihao123/CHI_DeepTreeSketch/blob/main/0-ack.png" width = "700" alt="ack" title="dasdasdsa title" align=center />
<br/><center><b>Fig. 1. Several SIGGRAPH-level papers <a href="https://dl.acm.org/doi/abs/10.1145/3478513.3480486">[link]</a> also borrowed my tree modeling algorithm <br/>to synthesize the 3D tree dataset, because of the strong capability of my implementated system.</b></center>
</div>
<br/>
<!--
**$\bullet$** In this algorithm, each species corresponds to one predefined string-based grammar set (a collection of production rules) which biologically defines a series of self-similar substructures of plants.  <a id="tool1"/>
The algorithm works as a parallel rewriting system to recursively expand each symbol into a longer production rule to iteratively form the tree structures.
We can obtain any number of different tree variants of the same species by adjusting parameters and randomly selecting the production rules per iteration.
Considering that the Parametric L-system is not the main focus of our paper, and is a quite complicated algorithm framework that cannot be briefly summarized in a short manner, please refer to these relevant papers or articles for more details on its mechanism: 
[[Wikipedia: L-system]](https://en.wikipedia.org/wiki/L-system)
[[A Tutorial Video on YouTube]](https://www.youtube.com/watch?v=ps7Mt1y1F48)
[[Prusinkiewicz et al. 96]](http://algorithmicbotany.org/papers/sigcourse.2003/2-1-lsystems.pdf) 
[[Sun et al. 09]](https://www.researchgate.net/publication/216337877_Intelligent_Tree_Modeling_Based_on_L-system) 
[[Lee et al. 23]](https://dl.acm.org/doi/full/10.1145/3627101?casa_token=VqUTDXPJQSsAAAAA%3A2D6naUDWtbzLoSAaVBqApxomg1W_MQ0gEagUY7c30HFNU8Tiua9iYI1N1RRhpf8E3t7vvF1OsSmE5w)
[[Prusinkiewicz et al. 12]](https://scholar.google.ca/citations?view_op=view_citation&hl=en&user=pjH7e8IAAAAJ&citation_for_view=pjH7e8IAAAAJ:TIZ-Mc8IlK0C) 
<br/> 
-->



## (b) [My Dataset Software 1] Automatic Tree Dataset Generator.

:hearts: We released **our software** that we developed for automatically generating the 3D tree models. This is a clean version tool so that you can use it to easily get different 3D tree variants of a specifed species.

- ⬇️ **Download Link:** Please download our tool (light-weight version) under this **[Folder](https://github.com/RyuZhihao123/CHITreeProject/tree/main/TreeDatasetGenerator)** **(You need download the entire folder)**.

- 💻 **Requirement (Configuration):**
  - Your should install **Visual Studio 2019+** on your PC. **Qt 5.8+** is also an option, but you basically only need one of them.
  - Additionally, we strongly suggest to install **CMake** and **OpenGL** (for 3D visualization) into your system path. Sometimes they are not strictly required because some PC may already have installed them by default. But pre-installation can somehow avoid unexpected compile errors.
  - Note that, this tool is only compiled for **Windows System (win10+)**. *Mac* is currently NOT supported.

- 📁 **Usage:**
  - Double click the **``Tree_Dataset_Generator.exe``** to run this problem.
  - You can re-generate a new random tree model by simply pressing the button **``Get New Tree``**. <a id="tool2"/>
  - Also you can change the tree species through the ComboBox (droplist).



<div align=center>
  <img src="https://github.com/RyuZhihao123/CHITreeProject/blob/main/TreeDatasetGenerator/dataset_generator.png" width = "330" alt="ack" align=center />
  <br/><center><b>Fig. 2.</b> The software we developed for automatically <br/>generating a large number of 3D tree models (100ms per tree).</center>
</div>





## (c) [My Dataset Software 2] Point-cloud based 3D Tree Reconstruction.

:hearts: In addition to the automatic generation of tree data, **our paper also includes some real-world trees in our dataset.** For example, we reconstructed some 3D tree models from **scanned 3D point clouds**.

<div align=center>
<img src="https://github.com/RyuZhihao123/SVDTree/blob/main/Fig_0.png" width = "900" alt="ack" align=center />
</div>


- ⬇️ **Download Link:** Please check this **[Folder](https://github.com/RyuZhihao123/CHITreeProject/tree/main/TreeFromPointClouds)** to download our developed software **(You need download the entire folder)**.

- 📺 **Demo Video:** Please first watch this **[[demo video]](https://drive.google.com/file/d/1htelf6xldyFYocqnZ6rtEZxSvwj3Gy1I/view?usp=sharing)** to see the intructions of the usage of my software.

- 📁 **Requirement & Usage:**
  - This software is only compiled for **Win10+**. The configuration is the same as the above software 1.
  - After downloading the entire **[Folder](https://github.com/RyuZhihao123/CHITreeProject/tree/main/TreeFromPointClouds)**, you can directly run the program by double clicking the **``TreeFromPoint.exe``**.
  - After activating the executable program, you can click the button "Load Point Data" to load a point cloud file. And then sequentially click the buttons from "(1)" to "(7)".

- ⭐ **Test Data of a 3D Point Cloud:**
  - Please download **this EXAMPLE 3D point cloud file [[xyz file](https://github.com/RyuZhihao123/CHITreeProject/blob/main/Tree1_input.xyz)]** to quickly have a try with our software.
  - You can easily use your own collected 3D point clouds in our software as well, as long as you have reformated them beforehand according to the form of the above example point cloud file.




<div align=center>
  <img src="https://github.com/RyuZhihao123/SVDTree/blob/main/Fig_UI_1.png" width = "400" alt="ack" title="dasdasdsa title" align=center />
  <img src="https://github.com/RyuZhihao123/SVDTree/blob/main/Fig_UI_3.png" width = "400" alt="ack" title="dasdasdsa title" align=center />
  <br/><center><b>Fig. 3.</b> The second software we developed for reconstructing real-world trees from 3D point clouds.<br/>These tree models were also used in the training dataset.</center>

</div>
<br/>

## (d) Dataset Format.

As mentioned above, in our CHI submission, we synthesized a large tree dataset with various different species. 
Please download the dataset of tree skeletons through this [[link (version: 20220509)]](https://univtokyo-my.sharepoint.com/:u:/g/personal/1487479010_utac_u-tokyo_ac_jp/EYL59bp6A2hMsjYFnHeDZaUBVow5KimE9KsTjwQfsSPMGw?e=LUjHsy).

Here are some examples in our dataset:

<div align=center>
<img src="https://github.com/RyuZhihao123/CHI24_TreeProject/blob/main/1-tree-exps-1.png" width = "500" alt="ack" align=center />
</div>

<br/>

Since our proposed neural network (TGP-Net) is designed to process the tree skeletons, we mainly store the branching structures (skeletons) in the dataset, to help reduce the memory footprint.

- In our dataset, **each ``.skel`` file** records the full branching structure of a 3D tree skeleton, and corresponds to one training sample. The **``.skel`` file** is organized in JSON format, thus you can use any JSON loader to easilly decode its structure. 

     Below, we use a simple example to explain the data format in detail:
```c
{type="header", name="tree_0001.skel", species_id = 6, treenode_num = 867, leaf_num = 2971},

// Tree nodes (total count=867):
{type: "treenode", node_id: 0, pos: [0.000, 0.000, 0.000],  parent_id: -1, children_ids: [1], radius: 0.027861, branch_id: 0},
{type: "treenode", node_id: 1, pos: [0.000, 0.148, 0.000],  parent_id: 0, children_ids: [2, 3], radius: 0.025100, branch_id: 0},
{type: "treenode", node_id: 2, pos: [-0.004, 0.278, 0.002], parent_id: 1, children_ids: [4, 5, 6], radius: 0.020372, branch_id: 0},
{type: "treenode", node_id: 3, pos: [-0.002, 0.407, 0.012], parent_id: 2, children_ids: [7, 8], radius: 0.018353, branch_id: 1},
{type: "treenode", node_id: 4, pos: [0.034, 0.368, -0.025], parent_id: 2, children_ids: [9, 10, 11], radius: 0.016534, branch_id: 2},
......
// All the leaves (total count=2971):
{type: "leaf", leaf_id: 0, pos: [-0.269, 0.894, 0.244],  orientation: [-0.861, 0.506, 0.040], size_scale: 0.041084},
{type: "leaf", leaf_id: 1, pos: [-0.030, 0.686, -0.012], orientation: [-0.576, -0.749, -0.325], size_scale: 0.042160},
```

- The first row with **``type="header"``** summarizes the overall information of this tree sample, such as, its species and the number of tree nodes, etc.

- Each row with **``type="treenode"``** represents one single tree node, recording its necessary attributes such as: *coordinate* and *edge connections*. 

    - ``node_id``: The index of this node. It starts from 0.
    - ``pos``: The global 3D position of this node. In our dataset, the height of all the trees are normalized to 1.0 in advance.
    - ``parent_id``: The index of the parent tree node of the current node.
    - ``children_ids``: The index of all the children nodes of the current node. It's an array since one tree node may have multiple children nodes.
    - ``radius``: The branch radius at this node.
    - ``branch_id``: The index of the long branch that this node belongs to. (not used in this project.)

<a id="Chapter2"/></a>
- The data file also additionally contains the information on leaves.
The rows with **``type="leaf"``** are all the leaves of this tree, recording its orientation and other attributes. 
Note that, our proposed TGP-Net doesn't use these leaf information in practice. But you can freely use them in your own project if needed. ^_^


:hearts: Please feel free to use my dataset in your work as long as you have indicated my name or cited this paper.





# 2. DeepTreeSketch Client.


<div align=center>
  <img src="https://github.com/RyuZhihao123/CHI_DeepTreeSketch/blob/main/Figures/2-system.png" width = "400" alt="ack" align=center />
  <br/><center><b>Fig. 4. The user client of our DeepTreeSketch system.</b></center>
</div>

- ⏬ **Download Link:** Please check this **[Folder](https://github.com/RyuZhihao123/CHITreeProject/tree/main/User_DeepTreeSketch_Client)** to download our developed software **(You need download the entire folder)**.

- 🎦 **Demo Videos:** [[Preview Video (30s)]](https://drive.google.com/file/d/1Kvj47Ckju43i9IpJ6OjWzE2ZkxVbOFTX/view?usp=sharing)
[[Full Video (3min)]](https://drive.google.com/file/d/1YNooKZMfFbwdyMv2JzuzhmUu7tJSMahL/view?usp=sharing).

- 💻 **Requirement & Usage:**
  - This software is only compiled for **Win10+**. The configuration is the same as the above software 1 (i.e., Visual Studio 2019+/Qt5.8+, CMake, and OpenGL for 3D visualization).
  - After downloading the entire **[Folder](https://github.com/RyuZhihao123/CHITreeProject/tree/main/User_DeepTreeSketch_Client)**, you can directly run the program by double clicking the **``DeepTreeDrawing_Client.exe``**.

- ❗**Regarding Server Connection**: After downloading the client of our sketching system, you also need to connect to **our listening server** that runs the neural network (TGP-Net) to handle the prediction request before using our software. **<ins>Thus, you MUST ensure to use our software client with internet connection.</ins>** But please understand that, since the TGP-Net Listening Server is currently configured on my own personal computer which might be sometimes shut down, the connection may not be established (if so, you may see some warnings in the software). **<ins>Therefore, in the case of failing to establish the server connection, you can try the followings:</ins>**
  - (1) Please directly contact me to re-start the server for you when you need to use our sketching software.
  - (2) If our time is hard to coodinate: You can save your own drawn sketches in your computer by pressing the ``Save`` button in the ``File Menu`` on the top-right corner. Then, directly email to me with your sketch files (*.txt format). I will return the results to you immediately once I see your email.
  - (3) Try my another Offline software for sketch-based tree modeling below . This old software can be directly used offline since it's based on another different algorithm. But it's consistency and quality is kind of below our new DeepTreeSketch.


- ⭐ **(Bonus Alternative) Another Offline software for sketch-based 3D tree modeling:**
  - When I was an undergraduate student, I have also developed another software for sketch-based 3D tree modeling (please download it from my another **[Github Repository](https://github.com/RyuZhihao123/TreeDesigner17)**). **Even though it is based on another totally different algorithm,** **the advantage of this software is that it can be used offline and without any configuration. Therefore, if you urgently need to obtain some 3D tree models and find my server is not running, you could try this old software first.** According to my information, many designers have used this tool to design 3D trees in their projects as well.

<div align=center>
<img src="https://github.com/RyuZhihao123/TreeDesigner17/blob/master/picA.png" width = "320" alt="ack" align=center />
<br/><center><b>Fig. 5.</b> Another alternative software I developed several years ago, </br>which can be directly run in your local PC without the need of connecting our server.</b></center>
</div>





