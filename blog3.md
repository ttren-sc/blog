# 基因表达矩阵处理过程中的基因id转换问题

最近对基因表达矩阵进行处理时，又遇到了之前一直有点模糊没完全解决掉的问题，当需要将基因ENSEMBL转换为SYMBOL时，
会出现基因id之间一对多情况，现在记录一下其他人的处理方法，作为参考。
  
### 使用clusterprofiler将基因ENSEMBL ID转换为SYMBOL ID时，会出现两种情况：  
* ENSEMBL ID对应多个SYMBOL ID
* SYMBOL ID对应多个ENSEMBL ID
  
### 如何解决？
很遗憾，目前为止，并没有找到一个统一的解决方案。
  
但是，如果你知道RNA-seq reads映射到Ensembl ID时使用了哪种基因注释构建，可以使用相同的构建将Ensembl ID转换为SYMBOL ID。这不一定能解决所有问题，但会有很大帮助。
  
按照前人的经验，一般来说，由于其中有一些ENSEMBL ID对应的表达值行全为0或低表达，因此可以先进行基因表达值过滤，以此先筛掉一部分ENSEMBL ID，从而减少很多上述两种情况对应产生的基因数量。
  
另外，需要弄清楚需要使用基因表达数据研究什么问题？如果使用GSEA做基因富集分析，有研究表示需要直接删除这些由于基因ID转换产生的重复基因。
  
最后，需要注意的是，不应该合并相同SYMBOL ID对应的基因表达值（不同基因被标记为相同的symbol是很常见的），有建议表示可以选取基因表达值最大的ENSEMBL ID。
  
-------
References
1. https://www.biostars.org/p/389804/
2. https://www.researchgate.net/post/How-to-deal-with-multiple-ensemble-IDs-mapping-to-one-gene-symbol-in-a-RNA-Seq-dataset
3. Preparation for GSEA in https://hbctraining.github.io/DGE_workshop_salmon_online/lessons/11_FA_functional_class_scoring.html
  
---
**NOTE**
永远在学习路上~  
欢迎各位在评论区留言批评指正，共同学习！:smile:
---
