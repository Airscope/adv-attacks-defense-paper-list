# AAAI 2022

## Boosting the Transferability of Video Adversarial Examples via Temporal Translation

- 基于深度学习的**视频识别模型**，在面对对抗样本的时候十分**脆弱**，尤其是在视频中添加人眼难以察觉的扰动信息的时候
- 最近的研究表面，对抗样本是transferable的，很容易遭受现实中的黑盒攻击
  - transferable：可迁移的，深度学习的迁移性指的是，在一个任务上预训练一个模型，之后在另一个模型上使用的特性。例如在图像识别任务上训练好的模型可以用在语音识别的任务上。
  - 注意与泛化能力的区分，泛化能力指的是模型面对未知数据时表现出的良好的预测准确率
- 目前针对**视频的攻击模型的迁移性都很差**，而且关于可迁移的攻击模型研究都比较少。因此论文作者的主要工作就是提升针对视频识别模型的**黑盒攻击**，希望能够提升攻击的可迁移性。
  - 白盒攻击：机器学习的算法和参数已知，攻击者在产生对抗性攻击数据的过程中能够与机器学习的系统交互
  - 黑盒攻击：机器学习的算法和参数未知，但攻击者仍能与机器学习的系统有所交互，比如可以通过传入任意输入观察输出，判断输出
- 关键词：黑盒攻击，视频识别，迁移性



## Towards Transferable Adversarial Attacks on Vision Transformers

- vision transformer (ViT) 在计算机视觉的任务里效果很好，但是面对对抗样本攻击的时候依然非常脆弱。
- 作者指出：针对transformer的对抗攻击，应该重点考虑其架构，同时也要考虑patches和自注意力机制，这样才能实现较好的transferability
- 为了实现在各种不同ViT上的较好的transferability，作者提出了一种dual attack框架，包括一个Pay No Attention (PNA) 攻击和一个PatchOut 攻击
- 作者的dual attack框架能够提升在不同ViT上的transferability，也能够提升从ViT到CNN上的transferability
- 关键词：ViT，计算机视觉，迁移性（transferability）



## Robust Heterogeneous Graph Neural Networks against Adversarial Attacks

- Heterogeneous Graph Neural Networks（异质图神经网络， HGNN）：是图神经网络的一种。同质图的节点都是一个类型的，边也一样。但现实生活中，异质图分布的更加广泛，比如社交网络，节点之间可能会存在点赞、评论的关系；节点也存在提问者、回答者的类型。
  - 同质图：整张图可表示为G=（V，E）
  - 异质图：整张图可表示为G=（V，E，R，T），其中R表示边的类型、T表示节点的类型
- 异质图神经网络最近获得了广泛关注，并且在一些任务上性能非常优秀，但是对于其在面临对抗样本的robustness的研究却很少。
- 作者首先研究了HGNN的鲁棒性，发现HGNN非常容易被欺骗（通过在两个目标节点之间添加对抗的边、或者通过添加一些degree非常高的节点）
- 作者给出了HGNN脆弱的两个原因：
  - 其一是perturbation enlargement effect
  - 其二是soft attention mechanism（这两个原因没看懂，以后再说）
- 作者提出了一个robust的HGNN框架RoHe，在对抗攻击下表现很好
- 关键词：异质图神经网络（HGNN），Robust，防御



## Unsupervised Adversarially Robust Representation Learning on Graphs

- 无监督/自监督的预训练方法在**图表征学习**（graph representation learning）方向很火，通过这些方法可以生成不同种类的下游应用，但是目前这些图学习模型的robustness，研究的比较少
  - TODO：下游应用具体有哪些？图表征学习和传统的图神经网络有什么区别？
- 大部分现存的针对图表征学习的端到端（end-to-end）防御技术需要预先给出labels，而作者提出了一种**无监督**的防御方法来提高预训练模型的鲁棒性
  - TODO：end-to-end的防御技术指的是什么？还有其他类别的防御技术吗？
- 作者主要是引入了一种基于**互信息**的方法来量化神经网络的鲁棒性，然后把整个问题形式化为一个优化问题。作者trade-off了graph encoder的表达能力和鲁棒性。由于图神经网络的拓扑结构、离散的特性以及图数据的joint space，优化问题非常难解，对此作者relax了问题，给出了近似解。
  - TODO：graph encoder是什么？优化问题难解的三个原因的具体内容。
- 此外作者还指出，无监督graph encoder的robustness和下游任务之间存在可以被证明的关系。
- 关键词：图表征学习（graph representation learning），robustness，防御，无监督的防御方法



## Unifying Model Explainability and Robustness for Joint Text Classification and Rationale Extraction

- **可解释性**和**鲁棒性**是**可信、可靠**的文本分类问题中的两个关键因素
  - 可解释性对应可信、鲁棒性对应可靠
- 以往的工作基本上只关注这两个方面的其中某一个方面：
  - 要么在保证预测效果的前提下，给可解释性提供一套准确的rationales（基本原理）
  - 要么就是使模型在面对不同种类的样本攻击时更加robust
- 直观上来说，一个模型的可解释性好，也意味着模型更加robust。假如说一个模型在面对输入样本的扰动时，产生的预测结果也会发生变化，那么这样的模型通常是不可信的。

- 对此，作者提出了一种联合了**文本分类**和**原理提取**（rationale extraction）的一个模型，关键的技术机制有两个：
  - Adversarial Training（AT）：在离散和嵌入空间内使用不同的扰动样本来提高鲁棒性
  - Boundary Match Constraint (BMC)：在Boundary 信息的指导下使得基本原理更加准确
- 总之，作者就是即想要**可解释性**，也想要**鲁棒性**

- 关键词：可解释性（explainability），鲁棒性（robustness），文本分类，原理提取（rationale extraction），防御



## Learning to Learn Transferable Attack

- 迁移对抗攻击（Transfer adversarial attack）是一种non-trivial的黑盒对抗攻击方法。迁移攻击首先在一个代理模型（surrogate model）上生成对抗扰动，然后把扰动应用到被攻击的模型上（victim model）。
- 现有的transferability方法有很多局限性，因为在代理模型上的对抗扰动非常容易over-fitting。因此作者提出了一种Learning
  to Learn Transferable Attack (LLTA)的方法，通过**数据增强**和**模型增强**来使得扰动更加generalized.
- 关键词：迁移学习，对抗攻击，元学习（Meta-Learning），数据增强，模型增强，黑盒攻击



## Sparse-RS: A Versatile Framework for Query-Efficient Sparse Black-Box Adversarial Attacks

- 作者提出了一种基于随机搜索（random search）的框架，进行score-based的黑盒攻击
  - 随机搜索：TODO
  - sparse attack：稀疏攻击，定义为只能修改图像很少数量的像素，但是不限制修改的幅度

- 关键词：稀疏攻击，黑盒攻击，随机搜索



## Shape Prior Guided Attack: Sparser Perturbations on 3D Point Clouds. 

- 作者关注于3D点云（3D point cloud）分类模型的robustness
- 作者提出了一种新的方法用来生成对抗点云样本，使用了shape的先验信息，来使得扰动更加sparse，从而达到更imperceptible的攻击
- 作者提出了一种Spatially Logical Block (SLB)的方法应用于对抗点上，此外还设计了一种算法称为FOFA将问题划分为子问题
- 关键词：先验信息，稀疏扰动，对抗样本攻击，3D点云



## Adversarial Attack for Asynchronous Event-Based Data

- 2D图像和3D点云的对抗样本以及被研究的很多了，但是event-based的数据研究的比较少
- 基于事件的数据在高速移动下可以被替代为2D的图像，比如说自动驾驶。
- 作者首次在event-based上给出了对抗的样本，并训练了一个robust的模型
- 关键词：基于事件的数据，攻击



## CLPA: Clean-Label Poisoning Availability Attacks Using Generative Adversarial Nets

- 投毒攻击