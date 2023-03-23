# 基因表达矩阵处理过程中的基因id转换问题

最近对基因表达矩阵进行处理时，又遇到了之前一直有点模糊没完全解决掉的问题，当需要将基因ENSEMBL转换为SYMBOL时，
会出现基因id之间一对多情况，现在记录一下其他人的处理方法，作为参考。

使用clusterprofiler将基因ENSEMBL id转换为SYMBOL id时，会出现两种情况：  
ENSEMBL id对应多个SYMBOL id
一个SYMBOL id对应多个ENSEMBL id

按照前人的经验，一般来说，由于其中有一些ENSEMBL id对应的表达值行全为0或低表达，因此可以先进行基因表达值过滤，
以此先筛掉一部分ENSEMBL id，从而减少上述两种情况的发生。
（Ref：https://www.biostars.org/p/389804/）

另外，首先需要弄清楚需要使用数据研究什么问题？

如果使用GSEA做基因富集分析，有研究表示需要直接删除这些由于基因id转换产生的重复基因。
（Ref：Preparation for GSEA in https://hbctraining.github.io/DGE_workshop_salmon_online/lessons/11_FA_functional_class_scoring.html
）
