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





