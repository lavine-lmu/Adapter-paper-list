# Adapter-Papers

Paper list and reading notes of Adapters in Natural Language Processing(NLP) and Machine Translation(MT) tasks.



#### Contributiing

<p align="center">
  <img src="https://www.soccerantenna.com/wp-content/uploads/2020/06/We-Need-You-Blue-Bell-Community-Hub-1024x573.png" alt="We Need You!" height="200" width="200">
</p>

Please help contribute this list by contacting <lavine@cis.lmu.de> or add [pull request]()



#### Table of Contents

+ [Natural Language Processing](#Natural-Language-Processing)
+ [Machine Translation](#Machine-Translation)



#### Natural Language Processing

+ [Parameter-Efficient Transfer Learning for NLP](http://proceedings.mlr.press/v97/houlsby19a.html) (Houlsby et al., 2019)
  + First work to using adapters in NLP tasks.
  + Adapter modules yield a compact and extensible model; they add only a few trainable parameters per task, and new tasks can be added without revisiting previous ones.
  + The parameters of the original network remain fixed, yielding a high degree of parameter sharing. 
+ [MAD-X: An Adapter-based Framework for Multi-task Cross-lingual Transfer](https://arxiv.org/pdf/2005.00052.pdf) (Pfeiffer et al., 2020)
  + Pretrained multilingual models performance poorly in low-resource language and language unseen in the pretrained phase. so the authors proposed the MAD-X.
  + MAD-X is an adapter-based framework that enables high portability and parameter-efficient transfer to arbitrary tasks and languages by learning modular language and task representations. 
  + They also introduce a novel invertible adapter architecture and a strong baseline method for adapting a pretrained multilingual model to a new language.
+ [AdapterFusion: Non-Destructive Task Composition for Transfer Learning](https://aclanthology.org/2021.eacl-main.39.pdf) (Pfeiffer et al., 2021)
  + The motivation is to address the problem in sequential fine-tuning and multi-task: catastrophic forgetting and difficulties in dataset balancing. so the authors proposed *AdapterFusion*
  + Two stage learning algorithm that leverages knowledge from multiple tasks
    + ***knowledge extraction stage***: learn task specific parameters called *adapters*, that encapsulate the task-specific information.
    + Combine the adapters in a seperiating ***knowledge cmoposition*** step.
+ [Efficient Test Time Adapter Ensembling for Low-resource Language Varieties](https://aclanthology.org/2021.findings-emnlp.63.pdf) (Wang et al., 2021)
  + Motivations: MAX-D requires training a separate language adapter for every language one wishes to support, which can be impractical for languages with limited data. one solution here is using related langauge adapter for new language variety, but we found that this solution can lead to sub-optimal performance. so the authors aim to improve the robustness of language adapters to uncovered languages without training new adapters.
  + They proposed Entropy Minimized Ensemble of Adapters (EMEA), a. method that optimizes the ensemble weights of the pretrained language adapters for each test sentence by minimizing the entropy of its predictions.
+ [On the Effectiveness of Adapter-based Tuning for Pretrained Language Model Adaptation](https://aclanthology.org/2021.acl-long.172.pdf) (He et al., 2021)
  + Motivations: existing adapter work only focuses on the parameter-efficient asapect of adapter-vased tuning while lacking further investigation on its effectiveness.
  + They showed that:
    + Adapter-based tuning better mitigates forgetting issues than fine-tuning since it yields representations with less deviation from those generated by the initial pretrained langauage model.
    + Adapter-based tuning outperforms fine-tuning on *low-resource* and *cross-lingual* tasks
    + Adapter-based tuning is more robust to overfitting and less sensitive to changes in learning rates.
+ [K-Adapter: Infusing Knowledge into Pre-Trained Models with Adapters](https://aclanthology.org/2021.findings-acl.121.pdf) (Wang et al., 2021)
  + Motivations: they study the problem of injecting knowledge into large pretrained models. traditional methods face the problems: when multiple kinds of knowledge are injected, the historically injected knowledge would be flushed away.
  + They proposed *K-Adapters*, a framework that retains the original parameters of the pre-trained model fixed and supports the development of versatile knowledge-infused model.



#### Machine Translation

+ [Simple, Scalable Adaptation for Neural Machine Translation](https://arxiv.org/pdf/1909.08478.pdf) (Bapna and First, 2019)
  + First work to using adapters in machine translation task.
  + Using in *Domain Adaptation* and *Multilingual Translation*.
  + Adapters for specific language pair.
+ [Monolingual Adapters for Zero-Shot Neural Machine Translation](https://aclanthology.org/2020.emnlp-main.361.pdf) (Philip et al., 2020)
  + Adapter layers are specific to one language, which is different than [Bapna et al., 2019](https://arxiv.org/pdf/1909.08478.pdf).
  + Monlingual adapter layer are inserted into each of the transformer encoder and decoder layers. When translating from source langauge ```x``` to target language ```y```, we only activate the encoder layers for ```x``` and the decoder layer for ```y```  
+ [Recipes for Adapting Pre-trained Monolingual and Multilingual Models to Machine Translation](https://aclanthology.org/2021.eacl-main.301.pdf) (Stickland et al., 2021)
  + Using adapters to fine-tune the multilingual pretrained model for all language pairs with a language-agonostic maners.
+ [Counter-Interference Adapter for Multilingual Machine Translation](https://aclanthology.org/2021.findings-emnlp.240.pdf) (Zhu et al., 2021)
  + They proposed ***embedding adapter*** and ***layer adapter*** to reduce multilingual interference among embedding and intermediate layers, respectively.
  + Layer adapters are in self-attention and feed-forward both in encoder and decoder.
  + Embedding adapters are in the embedding part of both encoder and decoder.
+ [Multilingual Unsupervised Neural Machine Translation with Denoising Adapters](https://aclanthology.org/2021.emnlp-main.533.pdf) (Üstün et al., 2021)
  + The approach combines monolingual denosing adapters with multilingual transfer learning on auxilarity parallel data.
  + Two steps:
    + **Monolingual training**, allows learning of language-specific encoding and decoding through adapter moudles which can easily be composed with other languages' adapter for translation.
    + **Transfer** mBART to multilingual UNMT by plugging in the denoting adapters and then fine-tuning cross-attention with auxiliary parallel data.

+ [Multilingual Domain Adaptation for NMT: Decoupling Language and Domain Information with Adapters](https://aclanthology.org/2021.wmt-1.64.pdf) (Stickland et al., 2021)
  + First work to integrate the task adapters and language adapters in machine translation scenarios.

+ [Language-Family Adapters for Multilingual Neural Machine Translation](https://openreview.net/pdf?id=TS3flrd9wWY) (ARR version)
  + Language-specific adapters do not learn useful cross-lingual representations for multiple language pairs, and Language-agonostic adapters share parameters for all languages and potentially have to deal with negative interference. so the author proposed training *langauge-family adapters* on top of a pretrained multilingual model to facilitate cross-lingual transfer.
  + They train a different set of adapters for each language family, to avoid negative transfer.