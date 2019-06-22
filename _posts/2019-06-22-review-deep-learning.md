---
title: 'Review:Deep-learning'
layout: post
categories: Paper
tags: summary
author: chuyuzhang
---
这段时间一直在读论文，会坚持写一下论文总结，以及自己的思考。
怎样读论文，参考[Summarize-a-Journal-Article](https://www.wikihow.com/Summarize-a-Journal-Article)

## 简要概括
这篇文章是三个巨头写的综述，对深度学习的一个总结。文章首先概括了深度学习在语音识别、物体识别、物体检测以及药物发现等领域的应用，之后又讨论了卷积神经网络和循环神经网络的应用与发展，最后指出未来深度学习的发展方向-无监督学习。

## 主要观点

1. Deep-learning methods are representation-learning methods with multiple levels of representation, obtained by composing simple but non-linear modules that each transform the representation at one level (starting with the raw input) into a representation at a higher, slightly more abstract level. With the composition of enough such transformations, very complex functions can be learned.

 作者认为深度学习就是表征学习，组合多层非线性模型来表达高层抽象的特征，层数足够的情况下，非常复杂的函数都可以学习到。

2. The conventional option is to hand design good feature extractors, which requires a considerable amount of engineering skill and domain expertise. But this can all be avoided if good features can be learned automatically using a general-purpose learning procedure. This is the key advantage of deep learning.

 这是深度学习在监督学习中如此成功的主要原因。传统的机器学习是要手工设计特征，这需要领域知识和工程技能，深度学习能自动学习特征，从而避免繁杂的特征工程。

3. Recent theoretical and empirical results strongly suggest that local minima are not a serious issue in general. Instead, the landscape is packed with a combinatorially large number of saddle points where the gradient is zero, and the surface curves up in most dimensions and curves down in the remainder. The analysis seems to show that saddle points with only a few downward curving directions are present in very large numbers, but almost all of them have very similar values of the objective function. Hence, it does not much matter which of these saddle points the algorithm gets stuck at.

 作者指出目前反向传播的困境--鞍点。梯度在鞍点处为零，这使得反向传播不能优化参数。研究表明，只有少数向下弯曲方向的鞍点非常多，但几乎所有鞍点都具有非常相似的目标函数值。因此，目标函数困在哪一个鞍点并不重要。

4. There are four key ideas behind ConvNets that take advantage of the properties of natural signals: local connections, shared weights, pooling and the use of many layers。

 First, in array data such as images, local groups of values are often highly correlated, forming distinctive local motifs that are easily detected. Second, the local statistics of images and other signals are invariant to location. 

 Although the role of the convolutional layer is to detect local conjunctions of features from the previous layer, the role of the pooling layer is to merge semantically similar features into one

 这里指出，卷积神经网络的四个特点，局部连接、共享权重、池化、多层。后面一句话，给出了局部连接和共享权重的原因，最后一句话指出卷积和池化的区别。

5. A recent stunning demonstration combines ConvNets and recurrent net modules for the generation of image captions.
<figure>
   <img src="{{ "/media/img/image_caption.JPG" | absolute_url }}" />
</figure>

 卷积神经网络和循环神经网络的结合应用。

6. Deep-learning theory shows that deep nets have two different exponential advantages over classic learning algorithms that do not use distributed representations. Both of thhse advantages arise from the power of composition and depend on the underlying data-generating distribution having an appropriate componential structure. First,learning distributed representations enable generalization to new combinations of the values of learned features beyond those seen during training. Second, composing layers of representation in a deep net brings the potential for another exponential advantage.

 作者指出深度学习分布式表达的优点。

## 总结

1. We expect unsupervised learning to become far more important in the longer term.
2. We expect much of the future progress in vision to come from systems that are trained end-to- end and combine ConvNets with RNNs that use reinforcement learning to decide where to look.
3. We expect systems that use RNNs to understand sentences or whole documents will become much better when they learn strategies for selectively attending to one part at a time.
4. Ultimately, major progress in artificial intelligence will come about through systems that combine representation learning with complex reasoning. Although deep learning and simple reasoning have been used for speech and handwriting recognition for a long time, new paradigms are needed to replace rule-based manipulation of symbolic expressions by operations on large vectors.

作者指出，未来的重点是无监督学习、端到端学习、组合学习、注意力机制、表征学习和复杂推理结合。这些都是未来值得探索的方向，也许我也会贡献我的力量。

## Reference
[1]LeCun, Yann, Yoshua Bengio, and Geoffrey Hinton. "Deep learning." Nature 521.7553 (2015): 436-444. [pdf](http://www.cs.toronto.edu/~hinton/absps/NatureDeepReview.pdf) (Three Giants' Survey)