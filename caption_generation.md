##Attribute based

- @inproceedings{cvpr2016/Wu,

  author    = {Qi Wu, Chunhua Shen, Lingqiao Liu, Anthony Dick, Anton van den Hengel},
  
  title     = {What Value Do Explicit High Level Concepts Have in Vision to Language Problems?},
  
  booktitle = {CVPR)},
  
  year = {2016}
  
}

**key words**: CNN+RNN, attribute

**Problem**: whether avoiding the explicit representation of high-level information leads to the success of CNN+RNN framework in Vision to Language problem (image captioning/single word QA/sentence QA).

**Conclusion**: high-level information is critical.

**Analysis**: 

The basic architecture is CNN+RNN with a intermediate layer for predicting the attribute. The attribute is then used as the first input of the RNN. (shown in Fig. 1)

What's Attribute? The objects detected. This paper uses a region-based multi-label classification framework to do this. (shown in Fig. 2)

For different V2L problems, models are different. (shown in Fig. 3). 
 

- @inproceedings{iclr2017/Yao,

  author    = {Ting Yao, Yingwei Pan, Yehao Li, Zhaofan Qiu, Tao Mei},
  
  title     = {Boosting  image captioning with attributes},
  
  booktitle = {ICLR (rejected)},
  
  year = {2017}
  
}

**key words**: CNN+RNN, attribute, where to add attribute

**Problem**: where to add Attributes into RNN part for improving the performance

**Analysis**:

The basic architecture is CNN+RNN+Attribute.

What's Attribute? The objects detected. This work uses MIL for detecting as [cvpr2015/Fang].

The models have 5 variations, the differences are where to add Attributes into the RNN

A<sub>1</sub>: same as [cvpr2016/Wu], image infomation is absent, only attribute is used as the first input for the RNN

A<sub>2</sub> --- A<sub>5</sub>, all explained in his Fig. 1

**Conclusion**: **know** where to add Attributes into RNN part for improving the performance. A<sub>5</sub> is the best, where image is the first input, and attribute is added to every timestep of RNN.

##Attention based
- @inproceedings{icml2015/Xu,

  author    = {Kelvin Xu, Jimmy Ba, Ryan Kiros, Kyunghyun Cho, Aaron Courville, Ruslan Salakhutdinov, Richard Zemel, Yoshua Bengio.},
  
  title     = {Show, Attend and Tell: Neural Image Caption Generation with Visual Attention},

  booktitle = {ICML},

  year = {2015}

}

**key words**: CNN+RNN, attention

**Problem**: incorporating attention into the CNN+RNN framework.

**Analysis**: The basic architecture is CNN+RNN.

The CNN feature is extracted from the last convolutional layer of VGG-16. The input of the RNN has the context, which is defined as the image being applied attention mask. Soft attention is a simple weighted sum without technical RL strategy. Furthermore, regularization term which forces the attention to look over the whole image. 
The figure here explains well the model: http://blog.csdn.net/shenxiaolu1984/article/details/51493673 
and (Fig. 3) in pami2016/kun
and Fig. 2(a) in arxiv2016/Lu

**Conclusion**: Attention simulates how human viewing an image. This paper does alignment automatically. Specifically, the region with attention is also aligned well with the word predicted. This is the first paper using the attention for image captioning. 

- @article{pami2016/kun,

    title={Aligning where to see and what to tell: image captioning with region-based attention and scene-specific contexts},
    
    author={Fu, Kun and Jin, Junqi and Cui, Runpeng and Sha, Fei and Zhang, Changshui},

    journal={Pattern Analysis and Machine Intelligence, IEEE Transactions on (TPAMI)},

    year={2016}

}

**key words**: RNN+CNN, attention, high-level semantic scene analysis, 

**Problem**: 1. align visual regions with words using the attention mechanism as in icml2015/Xu. 2. incorporating scene-specific context that captures higher-level semantic information encoded in an image.

**Analysis**: Globally, this model adds scene information (high level conception) into the LSTM as an extra input.

1. select regions and extract CNN feature from them. (Fig. 2)

2. attention model arch is the same as icml2015/Xu. The difference is that the candidate regions in [icml2015/Xu] is grids while this paper uses more fine regions. (Fig. 3)  

3. Scene-specific LSTM. This is an instantiation of the g-LSTM [iccv2015/Jia]. The scene vector is plugged into the LSTM as shown in Fig. 4. The general pipeline of this model is presented in Fig. 1. The scene vector is served as a global context. It is used to biasing the LSTM, so the question: how to caculate it? 
Two steps: unsupervised clustering of captions into “scene” categories and supervised learning of a classifier to predict the scene categories from the visual appearance.

**Conclusion**: the combination of attention and scene vector is useful 

- @inproceedings{arxiv2016/Lu,

  author    = {Jiasen Lu, Caiming Xiong, Devi Parikh and Richard Socher},
  
  title     = {Knowing When to Look: Adaptive Attention via A Visual Sentinel for Image Captioning},
  
  booktitle = {arxiv},
  
  year = {2016}
  
}

**key words**: RNN+CNN, attention, when to pay attention to the image

**Problem**: The decoder likely requires little to no visual information from the image to predict non-visual words such as “the” and “of”. Other words that may seem visual can often be predicted reliably just from the language model e.g., “sign” after “behind a red stop” or “phone” following “talking on a cell”. 

**Analysis**: the model can attend to the image if necessary, otherwise it will just rely on language model. Fig. 1 describes how this system performs. 

Two important novelties:

1. using current state h<sub>t</sub> to calculate attention, which is different from [icml2015/Xu]. See Fig. 2 for understanding the difference. The performance is better but the explanation I do not understand.

2. the sentinel is a latent representation of what the decoder already knows. This paper then extracts **the information from the memory cell**. the sentinel gate is calculated from the current and previous informatio to decide n 
 

- @inproceedings{arxiv2016/Zhou,

  author    = {Luowei Zhou, Chenliang Xu, Parker Koch, and Jason J. Corso},
  
  title     = {Watch What You Just Said: Image Captioning with Text-Conditional Attention},
  
  booktitle = {arxiv)},
  
  year = {2016}

}

- @inproceedings{cvpr2016/You,

  author    = {Quanzeng You, Hailin Jin, Zhaowen Wang, Chen Fang, and Jiebo Luo},
  
  title     = {Image captioning with semantic attention},
  
  booktitle = {CVPR)},
  
  year = {2016}
  
}




- @inproceedings{nips2016/Yang,

  author    = {Zhilin Yang, Ye Yuan, Yuexin Wu, Ruslan Salakhutdinov, William W. Cohen},
  
  title     = {Review Networks for Caption Generation},
  
  booktitle = {NIPS},
  
  year = {2016}
  
}



- @inproceedings{cvpr2015/Chen,

  author    = {X. Chen and C. L. Zitnick.},

  title     = {Mind’s eye: A recurrent visual representation for image caption generation.},

  booktitle = {CVPR},

  year = {2015}

}

- @inproceedings{iclr2015/Bahdanau,

  author    = {Dzmitry Bahdanau, Kyunghyun Cho, Yoshua Bengio},

  title     = {Neural Machine Translation by Jointly Learning to Align and Translate},

  booktitle = {ICLR},

  year = {2015}

}

- @inproceedings{cvpr2015/Donahue,

Author = {Jeff Donahue and Lisa Anne Hendricks and Sergio Guadarrama
             and Marcus Rohrbach and Subhashini Venugopalan and Kate Saenko
             and Trevor Darrell},

   Title = {Long-term Recurrent Convolutional Networks
            for Visual Recognition and Description},

   Year  = {2015},

   Booktitle = {CVPR}

}

- @inproceedings{cvpr2015/Karpathy,

  author    = {Andrej Karpathy, Li Fei-Fei},

  title     = {Deep Visual-Semantic Alignments for Generating Image Descriptions},

  booktitle = {CVPR},

  year = {2015}

}

- @inproceedings{iccv2015/Jia,

  author    = {Xu Jia, Efstratios Gavves, Basura Fernando, Tinne Tuytelaars},

  title     = {Guiding the Long-Short Term Memory Model for Image Caption Generation},

  booktitle = {ICCV},

  year = {2015}

}


- @inproceedings{cvpr2015/Vinyals,

  author    = {Oriol Vinyals, Alexander Toshev, Samy Bengio, Dumitru Erhan},

  title     = {Show and Tell: A Neural Image Caption Generator},

  booktitle = {CVPR},

  year = {2015}

}

- @inproceedings{cvpr2015/Fang,

  author    = {Hao Fang, Saurabh Gupta, Forrest Iandola, Rupesh Srivastava, Li Deng, Piotr Dollár, Jianfeng Gao, Xiaodong He, Margaret Mitchell, John C. Platt, C. Lawrence Zitnick, Geoffrey Zweig},
 
  title     = {From Captions to Visual Concepts and Back},
 
  booktitle = {CVPR},
 
  year = {2015}

}

- @inproceedings{iclr2015/Mao,
  
  author    = {Junhua Mao, Wei Xu, Yi Yang, Jiang Wang, Zhiheng Huang, Alan Yuille},
  
  title     = {Deep Captioning with Multimodal Recurrent Neural Networks (m-RNN)},
  
  booktitle = {ICLR},
  
  year = {2015}

}

- @inproceedings{emnlp2015/Luong,

  author    = {Minh-Thang Luong, Hieu Pham, Christopher D. Manning},

  title     = {Effective Approaches to Attention-based Neural Machine Translation},

  booktitle = {EMNLP},

  year = {2015}

}

- @inproceedings{tacl2015/Yin,

  author    = {Wenpeng Yin, Hinrich Schütze, Bing Xiang, Bowen Zhou},

  title     = {ABCNN: Attention-Based Convolutional Neural Network for Modeling Sentence Pairs},

  booktitle = {TACL},

  year = {2015}

}


- @inproceedings{pr2014/Rohrbach,

  author    = {Anna Rohrbach, Marcus Rohrbach, Wei Qiu, Annemarie Friedrich,Manfred Pinkal, and Bernt Schiele},

  title     = {Coherent Multi-Sentence Video Description with Variable Level of Detail},

  booktitle = {PR},

  year = {2014}

}

- @inproceedings{tacl2014/Kiros,

  author    = {Jamie Ryan Kiros, Ruslan Salakhutdinov, Richard Zemel},

  title     = {Unifying Visual-Semantic Embeddings with Multimodal Neural Language Models },

  booktitle = {TACL},

  year = {2014}

}

- @inproceedings{nips2014/Mnih,

  author    = {Volodymyr Mnih, Nicolas Heess, Alex Graves, Koray Kavukcuoglu},

  title     = {Recurrent Models of Visual Attention},

  booktitle = {NIPS},

  year = {2014}

}



##Metric optimization

- @inproceedings{cvpr2017/Liu,  

  author    = {Siqi Liu, Zhenhai Zhu, Ning Ye, Sergio Guadarrama, and Kevin Murphy},
  
  title     = {Optimization of image description metrics using policy gradient methods},
  
  booktitle = {CVPR (under review)},
  
  year = {2017}
  
}

*Purpose: an optimization method on the metrics of text generation.*

*Value: It's possible to get high score with this methods*

*Analysis: I did not read it through*

*code: No*


#Review Networks for Caption Generation},
###Zhilin Yang, Ye Yuan, Yuexin Wu, Ruslan Salakhutdinov, William W. Cohen},
####NIPS2016

important, need to re read carefully

1.论文主要解决的问题是什么？
improve encoder+attention+decoder framework 
2.主要问题

	这个问题重要吗？为什么？
	important. More thought on attention model. Discriminative supervision is interesting.
	我为什么要读这篇文献？ 
	
	是否有人做过？
	
	自己会怎么设计方法来解决？
	
3.图表

	3.A	通过图表，你会得到什么结论？

	3.B	图表说明什么问题？能否说明该问题?自己要得到这张图会用什么方法？作者用的是什么方法？
	
	3.C	你能够重新画出这张图，用自己的语言表达吗？
	
4.方法分析
	
	作者采用什么方法来解决这个问题？假设是什么？理论依据是什么？
	
	这些方法是否符合论证命题的需要？
	
	通过这个方法，你觉得大概能得到怎样的结果？
	
	是否有能得到更好结果的方法或更加简单的方法？
	
	他为什么这样设计试验？是怎么想到的？有什么创新？你为什么没有想到？
	
5.逻辑

	5.A	这些设计能否满足需要？为什么？这种方法有什么缺陷或进一步需要阐明的地方? 结果分析统计方法有什么缺陷
		
	5.B	这些试验是如何组织起来的，之间的逻辑关系是什么？每项试验都有什么意义？哪些是必要的？哪些是不必要的？ 
		
	5.C	如果是我得到这样的结果，我会得到什么结论？
	
6.结论
	
	6.A	文章的结论是什么？和你想的差异在哪里?
	
	6.B	结论可靠性如何？对原来的结论有什么支持或变化？ 你如何评价？
	
	6.C	讨论中是如何从已知的知识得到结论

7.不足
	
	7.A	试验结果是否支持文章的结论 问题、设计、方法和讨论的逻辑关系是什么，作者是如何达到目的的？有哪些哲学思想和技巧？
		
	7.B	还有哪些不确定采用的是推测的地方？为什么不确定？我能否进一步确定？ 
	
	7.C	文章是如何描述结果、如何解析图表趋势，论据如何组合，如何表达自己的观点？
	
8.和同类文献，有什么共同点和不同点？

9.和以前的文献，作者思路上有什么变化，下一步是什么？我能否有进一步改进或者加入？

10.别人还有哪些地方没做？要是我接着此方向继续做，哪些是在我所在工作条件下可以做的，哪些必须要做，哪些别人肯定比我做得更好更快？


#From Captions to Visual Concepts and Back
###Hao Fang, Saurabh Gupta, Forrest Iandola, Rupesh K. Srivastava,Li Deng Piotr Dollar Jianfeng Gao Xiaodong He Margaret Mitchell John C. Platt C. Lawrence Zitnick Geoffrey Zweig
####CVPR2015
1.论文主要解决的问题是什么？

2.主要问题

	这个问题重要吗？为什么？
	
	我为什么要读这篇文献？ 
	
	是否有人做过？
	
	自己会怎么设计方法来解决？
	
3.图表

	3.A	通过图表，你会得到什么结论？

	3.B	图表说明什么问题？能否说明该问题?自己要得到这张图会用什么方法？作者用的是什么方法？
	
	3.C	你能够重新画出这张图，用自己的语言表达吗？
	
4.方法分析
	
	作者采用什么方法来解决这个问题？假设是什么？理论依据是什么？
	
	这些方法是否符合论证命题的需要？
	
	通过这个方法，你觉得大概能得到怎样的结果？
	
	是否有能得到更好结果的方法或更加简单的方法？
	
	他为什么这样设计试验？是怎么想到的？有什么创新？你为什么没有想到？
	
5.逻辑

	5.A	这些设计能否满足需要？为什么？这种方法有什么缺陷或进一步需要阐明的地方? 结果分析统计方法有什么缺陷
		
	5.B	这些试验是如何组织起来的，之间的逻辑关系是什么？每项试验都有什么意义？哪些是必要的？哪些是不必要的？ 
		
	5.C	如果是我得到这样的结果，我会得到什么结论？
	
6.结论
	
	6.A	文章的结论是什么？和你想的差异在哪里?
	
	6.B	结论可靠性如何？对原来的结论有什么支持或变化？ 你如何评价？
	
	6.C	讨论中是如何从已知的知识得到结论

7.不足
	
	7.A	试验结果是否支持文章的结论 问题、设计、方法和讨论的逻辑关系是什么，作者是如何达到目的的？有哪些哲学思想和技巧？
		
	7.B	还有哪些不确定采用的是推测的地方？为什么不确定？我能否进一步确定？ 
	
	7.C	文章是如何描述结果、如何解析图表趋势，论据如何组合，如何表达自己的观点？
	
8.和同类文献，有什么共同点和不同点？

9.和以前的文献，作者思路上有什么变化，下一步是什么？我能否有进一步改进或者加入？

10.别人还有哪些地方没做？要是我接着此方向继续做，哪些是在我所在工作条件下可以做的，哪些必须要做，哪些别人肯定比我做得更好更快？


#Guiding the Long-Short Term Memory Model for Image Caption Generation
###Xu Jia, Efstratios Gavves, Basura Fernando, Tinne Tuytelaars},
####ICCV2015
1.论文主要解决的问题是什么？
extracting
semantic information from the image and then use
it to “guide” the decoder, keeping it “on track” by adding
a positive bias to words that are semantically linked to the
image content.
2.主要问题

	这个问题重要吗？为什么？
	important. Because it is more general than attention map. Knowing how to process the semantic information of image can inspire me how
	to generate extra attention map
	我为什么要读这篇文献？ 
	see above
	是否有人做过？
	yes, attention map is a special kind of semantic info.
	自己会怎么设计方法来解决？
	no idea.
3.图表

	3.A	通过图表，你会得到什么结论？
	glsvm is a genral framework. It takes an extra input for input gate, input modulate gate, forget gate and output gate. 
	3.B	图表说明什么问题？能否说明该问题?自己要得到这张图会用什么方法？作者用的是什么方法？
	
	3.C	你能够重新画出这张图，用自己的语言表达吗？
	
4.方法分析
	
	作者采用什么方法来解决这个问题？假设是什么？理论依据是什么？
	Retrieval-based guidance: generate a sentence, then feed back as guidance.
	Semantic embedding guidance (emb-gLSTM): word is represented by embedding, with lower dimension.
	Image as guidance (img-gLSTM): using image as guidance. 
	这些方法是否符合论证命题的需要？
	
	通过这个方法，你觉得大概能得到怎样的结果？
	
	是否有能得到更好结果的方法或更加简单的方法？
	
	他为什么这样设计试验？是怎么想到的？有什么创新？你为什么没有想到？
	
5.逻辑

	5.A	这些设计能否满足需要？为什么？这种方法有什么缺陷或进一步需要阐明的地方? 结果分析统计方法有什么缺陷
		img as guidance is not the best result.
	5.B	这些试验是如何组织起来的，之间的逻辑关系是什么？每项试验都有什么意义？哪些是必要的？哪些是不必要的？ 
		
	5.C	如果是我得到这样的结果，我会得到什么结论？
	
6.结论
	
	6.A	文章的结论是什么？和你想的差异在哪里?
	
	6.B	结论可靠性如何？对原来的结论有什么支持或变化？ 你如何评价？
	
	6.C	讨论中是如何从已知的知识得到结论

7.不足
	
	7.A	试验结果是否支持文章的结论 问题、设计、方法和讨论的逻辑关系是什么，作者是如何达到目的的？有哪些哲学思想和技巧？
		
	7.B	还有哪些不确定采用的是推测的地方？为什么不确定？我能否进一步确定？ 
	
	7.C	文章是如何描述结果、如何解析图表趋势，论据如何组合，如何表达自己的观点？
	
8.和同类文献，有什么共同点和不同点？

9.和以前的文献，作者思路上有什么变化，下一步是什么？我能否有进一步改进或者加入？

10.别人还有哪些地方没做？要是我接着此方向继续做，哪些是在我所在工作条件下可以做的，哪些必须要做，哪些别人肯定比我做得更好更快？

  



