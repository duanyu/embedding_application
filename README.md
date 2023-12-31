# embedding_application

一些embedding model的应用，例如语义检索、聚类等。

# 语义检索

## 应用：鲁迅全集检索

`embedding_luxun_search.ipynb`

将[鲁迅全集](https://github.com/Ac-heron/luxun)进行passage切分，随后用`bge-large-zh-v1.5`进行embedding表征，随后导入milvus，然后就可以搜索各种内容啦。

由于是语义检索的概念，像“内卷与躺平”这种query也可以搜到不错的结果。

说明：

1. 在modelscope-GPU环境可直接运行，所需依赖的库已在jupyter中指明，在其他环境下还需`pip3 install modelscope`；
2. 在GPU上大约需消耗2G显存，CPU也能跑但是贼慢。

感兴趣的读者可以读[这篇博文](https://mp.weixin.qq.com/s?__biz=MzkwNjUyODgzMQ==&mid=2247483936&idx=1&sn=29f31ee063a1576524d916be92347a3c&chksm=c0e65370f791da665f54d6098d6f10cdb74db8913b9cf7a532b136678d3f6e7d75bfda017087&token=46985569&lang=zh_CN#rd)，以了解更多细节。

# 聚类

## 应用：新闻早报聚类

`embedding_news_clustering.ipynb`

将几个微信公众号的早报新闻解析为（title，passages）格式，随后使用`bge-large-zh-v1.5`对title进行表征，最后进行DBSCAN聚类，以聚合相同、相关的新闻。

说明：

1. 在modelscope-GPU环境可直接运行，所需依赖的库已在jupyter中指明，在其他环境下还需`pip3 install modelscope`；
2. DBSCAN的超参选择方面，metric选择cosine距离、eps选择0.4-0.45、min_samples=2。其中eps越大，越能包含“相关”新闻；eps越小，越只能包含“相同”新闻；
3. 解析url使用了`unstructured`，此库依赖[nltk_data](http://www.nltk.org/nltk_data/)中的punkt、averaged_perceptron_tagge，如果nltk下载慢，建议直接使用下载好的punkt、averaged_perceptron_tagge（本项目source目录下已下载好，可直接用）。

感兴趣的读者可以读[这篇博文](https://mp.weixin.qq.com/s?__biz=MzkwNjUyODgzMQ==&mid=2247483936&idx=1&sn=29f31ee063a1576524d916be92347a3c&chksm=c0e65370f791da665f54d6098d6f10cdb74db8913b9cf7a532b136678d3f6e7d75bfda017087&token=46985569&lang=zh_CN#rd)，以了解更多细节。


