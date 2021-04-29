# Universal-Knowledge-Graph-based-Biomedical-Knowledge-Enlargment
## Introduction:
    
In order to support biomedical research on COVID-19 with information science, we are developing an AI system that automatically analyzes big data from 336K academic abstracts and 160 papers related to COVID-19 and other 30 million abstracts of biomedical papers. This system significantly augments the existing knowledge base by automatically extracting the vast amount of information and knowledge that may be relevant to COVID-19 from the big data. We also infer potential relationship among gene/protein, drug, disease , symptoms, enzyme, etc. based on the associations among the large mount of knowledge and reference relationships between papers. The system presents such information to researchers and supports access to academic papers, knowledge and a "big picture" that would contribute to the <b> academic </b> research on mechanism, drugs repurposing, diagnostics, etc.

## Algorithm:

To identify biomedical concepts in textual corpus, we apply [Scispacy](https://allenai.github.io/scispacy/), a state-of-the-art biomedical named entity recognizer, to detect UMLS entities in text. 

To predict potentially related candidate concepts and generate the supporting explanation (Reasoning Path), we, firstly, represent the large amount of knowledge extracted from existing structured knowledge base and unstructured text as a **Universal Knowledge Graph**. In the **Universal Knowledge Graph**, each node represents the UMLS concept and each edge indicates a UMLS relationship or a textual relationship, as shown in Figure3. In addition, we will incorporate Multi-modal data such as molecular structure into the **Universal Knowledge Graph** in the future.

<img src="overview.png" width="700">
(Figure3)

Next, our system relies on a state-of-the-art Tail Prediction Model (Takahashi et al., 2018) that learns to project **Universal Knowledge Graph** into a same continuous vector space and predicts the candidate concepts based on the vector calculation. 

Then, our system searches the multi-hop reasoning paths that connect the candidate and target concept over the **Universal Knowledge Graph**. Finally, our system applies a new Relation Prediction Model (Dai et al., 2019, 2021) to classify (or reexamine) the relationship between target and candidate concepts based on the multi-hop reasoning paths and evaluate the contribution of each path via a Knowledge Graph based attention mechanism.

## Members:
This project is led by [Kentaro Inui](http://www.cl.ecei.tohoku.ac.jp/~inui/) with a team of members: [Qin Dai](http://www.cl.ecei.tohoku.ac.jp/~dq/) and [Ryo Takahashi](https://reiyw.com/), from the Tohoku University, and is supported by the JST CREST Project on [Scientific Paper Analysis](https://www.jst.go.jp/kisoken/crest/en/project/44/15656596.html) (Research Director:[Yuji Matsumoto](https://cl.naist.jp/staff/matsu/home-e.html)). Special thanks to [Yoshimasa Tsuruoka](https://www.logos.ic.i.u-tokyo.ac.jp/~tsuruoka/) and [Akiko Aizawa](https://www.nii.ac.jp/en/faculty/digital_content/aizawa_akiko/) for their help and advice in building the system.

### References:
- Ryo Takahashi, Ran Tian and Kentaro Inui. 2018. Interpretable and Compositional Relation Learning by Joint Training with an Autoencoder. In *Proceedings of the 56th Annual Meeting of the Association for Computational Linguistics*(Volume 1: Long Papers), volume 1, pages 2148–2159.
- Qin Dai, Naoya Inoue, Paul Reisert, Ryo Takahashi and Kentaro Inui. 2019. Incorporating Chains of Reasoning over Knowledge Graph for Distantly Supervised Biomedical Knowledge Acquisition. In *Proceedings of the 33rd Pacific Asia Conference on Language, Information and Computation (PACLIC33)*, pages 19-28.
- - Qin Dai, Naoya Inoue, Ryo Takahashi and Kentaro Inui. 2021. Two Training Strategies for Improving Relation Extraction over Universal Graph. In *Proceedings of the 16th Conference of the European Chapter of the Association for Computational Linguistics*, pages 3673–3684.
