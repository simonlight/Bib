#From Where and How to What We See
###S. Karthikeyan, Vignesh Jagadeesh, Renuka Shenoy, Miguel Eckstein, B.S. Manjunath
####ICCV2013

1.论文主要解决的问题是什么？
	predicting face and text regions in images using eye tracking data from multiple subjects,
	without using any image information
	
2.主要问题

	这个问题重要吗？为什么？
	Important. Because it means gazes are meaningful for localizing faces and text. 
	我为什么要读这篇文献？ 
	Gaze keyword
	是否有人做过？
	No.
	自己会怎么设计方法来解决？
	I will extract the features of gazes from the regions of faces and text, then train two classifiers.
3.图表

	3.A	通过图表，你会得到什么结论？
	跟我说的方法差不多。
	3.B	图表说明什么问题？能否说明该问题?自己要得到这张图会用什么方法？作者用的是什么方法？
	说明用fixation聚类的方法能得到数个候选区域，从候选区域中用bounding box能得到目标fixation cluster。可以。 
	我说的方法。
	3.C	你能够重新画出这张图，用自己的语言表达吗？
	可以
4.方法分析
	
	作者采用什么方法来解决这个问题？假设是什么？理论依据是什么？
	
	这些方法是否符合论证命题的需要？
	有缺陷。卖点是没有用到image information，但是用到了bounding box。
	通过这个方法，你觉得大概能得到怎样的结果？
	
	是否有能得到更好结果的方法或更加简单的方法？
	
	他为什么这样设计试验？是怎么想到的？有什么创新？你为什么没有想到？
	
5.逻辑

	5.A	这些设计能否满足需要？为什么？这种方法有什么缺陷或进一步需要阐明的地方? 结果分析统计方法有什么缺陷
		
	5.B	这些试验是如何组织起来的，之间的逻辑关系是什么？每项试验都有什么意义？哪些是必要的？哪些是不必要的？ 
		
	5.C	如果是我得到这样的结果，我会得到什么结论？
	
6.结论
	
	6.A	文章的结论是什么？和你想的差异在哪里?
	用文中的方法能提高现有的object detector方法。
	差异：使用的gaze来自free viewing。
	6.B	结论可靠性如何？对原来的结论有什么支持或变化？ 你如何评价？
	略
	6.C	讨论中是如何从已知的知识得到结论
	略
7.不足
	
	7.A	试验结果是否支持文章的结论 问题、设计、方法和讨论的逻辑关系是什么，作者是如何达到目的的？有哪些哲学思想和技巧？
		
	7.B	还有哪些不确定采用的是推测的地方？为什么不确定？我能否进一步确定？ 
	
	7.C	文章是如何描述结果、如何解析图表趋势，论据如何组合，如何表达自己的观点？
	
8.和同类文献，有什么共同点和不同点？

9.和以前的文献，作者思路上有什么变化，下一步是什么？我能否有进一步改进或者加入？

10.别人还有哪些地方没做？要是我接着此方向继续做，哪些是在我所在工作条件下可以做的，哪些必须要做，哪些别人肯定比我做得更好更快？
