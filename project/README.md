# Project: Understand the Impact of Different Regression Techniques on Updatable Learned Index

Indexing data-structures are a fundamental part of many data management applications. Instead of searching in the whole space, indexing data-structures accelerate the data access by narrowing the search space to a lower granularity level. For example, B-Tree, a tree-like indexing data-structure, is widely used in the data management domain. In B-Tree, only the leaf nodes store both the keys and values, but the internal nodes only store keys. In a B-Tree, searching for a key happens in two-stage lookup operations. First, it traverses to leaf the leaf node by making comparisons in the internal nodes. Second, it does a binary search within the leaf note to find the key's exact location. There are a couple of drawbacks of such storage layout and search strategies. First, the internal nodes have to store the keys to compare during the lookups and thus introduce the "write amplification". This issue would worsen when the storage devices have asymmetric read-write latency. Second, the lookup is suffered by the cache misses. When the tree becomes deep, the number of comparisons and branches can be large, which leads to many cache misses. Furthermore, typically, at the leaf node, a binary search is performed to find the key's position, which brings additional cache misses. Figure 1 shows the example of a B-Tree.

<p align="center">
  <img src="https://github.com/biqar/Fall-2020-ITCS-8156-MachineLearning/blob/master/project/resources/b-tree.png" />
  <p align="center">Figure 1: Example of B-Tree<p align="center">
</p>

Targeting to reduce the data amplifications and lookup cache misses, the data management domain tries to adopt machine learning techniques. Thanks to the “learned index” [1] that first shows these possibilities. We know the machine learning models can predict the location of a targeted “key” from a sorted array, and we also know that data is kept sorted in the B-Tree leaf nodes. Let us consider, we have a supervised machine learning model for all the leaf nodes of a B-Tree and the leaf nodes placed side by side. Now, given a key, that model will predict the key's location within the (logically) sorted array. This is the key idea behind the “Learned Index” concept, where a machine learning model replaces b-Tree. Figure 2 shows such an arrangement from [1].

<p align="center">
  <img src="https://github.com/biqar/Fall-2020-ITCS-8156-MachineLearning/blob/master/project/resources/b-tree_as_ml_model.png" />
  <p align="center">Figure 2: Why B-Trees are models [1]<p align="center">
</p>

Here, although we replaced the B-Tree with a machine learning model (e.g., neural network), the lookup operation would be the same as before. Given a key, the machine learning model will predict the key's exact location within a sorted array. As we know, such a perfect machine learning model is hard to get. So in our use-case, we should consider some error boundary during the prediction, and we have to search within this range to get the exact key. In figure 2, after the neural network predicts a key position, we have to make a local search within the minimum and maximum error margin of the model.

In this regard, the benefits of using machine learning models are two folded. First, there is no need for the intermediate nodes of the B-Trees, and even if we need, we no longer need to store the keys in the intermediate nodes. Instead, we can keep the models there, which ultimately tears down the storage overhead. Second, we can avoid running binary searches in the B-Tree nodes and thus incur lower cache misses and improve the search performance.

In this research, we systematically explored the learned index model's design choices and proposed our choices of changes over the existing work.

## TODOs
1. Understand the ALEX codebase
2. Understand the CDFShop codebase
3. Clearly mention the contribution of this project

## Reference

### Paper References
1. T. Kraska, A. Beutel, E. H. Chi, J. Dean, and N. Polyzotis. The Case for Learned Index Structures. In Proceedings of the 2018 International Conference on Management of Data, SIGMOD ’18, New York, NY, USA, 2018. ACM.
2. J. Ding, U. F. Minhas, H. Zhang, Y. Li, C. Wang, B. Chandramouli, J. Gehrke, D. Kossmann, and D. Lomet. ALEX: An Updatable Adaptive Learned Index. arXiv:1905.08898 [cs], May 2019.
3. A. Kipf, R. Marcus, A. vanRenen,M. Stoian, A. Kemper, T. Kraska, and T. Neumann. RadixSpline: A single-pass learned index. In Proceedings of the Third International Workshop on Exploiting Artificial Intelligence Techniques for Data Management, aiDM @ SIGMOD ’20, pages 1–5, Portland, Oregon, June 2020. Association for Computing Machinery.
4. Qing Xie, Chaoyi Pang, Xiaofang Zhou, Xiangliang Zhang, and Ke Deng. 2014. Maximum error-bounded Piecewise Linear Representation for online stream approximation. The VLDB Journal 23, 6 (December 2014), 915–937. DOI: https://doi.org/10.1007/s00778-014-0355-0
5. Microsoft, ALEX-A library for building an in-memory, Adaptive Learned indEX, (2020), GitHub repository, https://github.com/microsoft/ALEX
6. Ryan Marcus, Error-bounded piecewise linear regression, (2019), GitHub repository, https://github.com/RyanMarcus/plr
7. Yifan Dai, Yien Xu, Aishwarya Ganesan, Ramnatthan Alagappan, Brian Kroth, Andrea C. Arpaci-Dusseau, and Remzi H. Arpaci-Dusseau. From Wisckey to Bourbon: A Learned Index for Log-structured Merge Trees. In Proceedings of the 14th Symposium on Operating System and Design Implementation, OSDI ’20, Nov, 2020.
8. Ani Kristo, Kapil Vaidya, Ugur Çetintemel, Sanchit Misra, and Tim Kraska. 2020. The Case for a Learned Sorting Algorithm. In Proceedings of the 2020 ACM SIGMOD International Conference on Management of Data (SIGMOD '20). Association for Computing Machinery, New York, NY, USA, 1001–1016. DOI:https://doi.org/10.1145/3318464.3389752
9. Stephen Macke, Alex Beutel, Tim Kraska, Maheswaran Sathiamoorthy, Derek Zhiyuan Cheng, Ed H. Chi. Lifting the Curse of Multidimensional Data with Learned Existence Indexes. ML for Systems Workshop at NeurIPS Int'l Conf. on Neural Information Processing Systems, Dec. 2018 and Bay Area Machine Learning Symposium, Oct. 2018
10. Lujing Cen, Ryan Marcus, Hongzi Mao, Justin Gottschlich, Mohammad Alizadeh, and Tim Kraska. 2020. Learned garbage collection. In Proceedings of the 4th ACM SIGPLAN International Workshop on Machine Learning and Programming Languages (MAPL 2020). Association for Computing Machinery, New York, NY, USA, 38–44. DOI:https://doi.org/10.1145/3394450.3397469
11. Andreas Kipf, Ryan Marcus, Alexander van Renen, Mihail Stoian, Alfons Kemper, Tim Kraska, and Thomas Neumann. 2020. RadixSpline: a single-pass learned index. In Proceedings of the Third International Workshop on Exploiting Artificial Intelligence Techniques for Data Management (aiDM '20). Association for Computing Machinery, New York, NY, USA, Article 5, 1–5. DOI:https://doi.org/10.1145/3401071.3401659
12. Ryan Marcus, Emily Zhang, and Tim Kraska. 2020. CDFShop: Exploring and Optimizing Learned Index Structures. In Proceedings of the 2020 ACM SIGMOD International Conference on Management of Data (SIGMOD '20). Association for Computing Machinery, New York, NY, USA, 2789–2792. DOI:https://doi.org/10.1145/3318464.3384706

### Github Repositories
1. [ALEX](https://github.com/biqar/ALEX/tree/7e83ef9d211ff4d67b46aeabbe414fbacf5489e5): A library for building an in-memory, Adaptive Learned indEX
2. [PLR](https://github.com/RyanMarcus/plr/tree/cce4fe1dfdbb0f4efcca25267b0ac1d72b0d2e58): Error-bounded piecewise linear regression
3. [mlcpp](https://github.com/Kolkir/mlcpp): Set of examples of ML approaches implemented in C++
4. [xtensor](https://github.com/xtensor-stack/xtensor/): C++ tensors with broadcasting and lazy computing
5. [xtensor-blas](https://github.com/xtensor-stack/xtensor-blas/): BLAS extension to xtensor
