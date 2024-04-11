
**[W1]** A practical application of our work lies in automated hiring systems. In such systems, a learned model can make hiring decisions for employment candidates on behalf of a company, irrespective of sensitive information such as race. For instance, an automated hiring system can be trained using historical data collected from various geographical regions. Each data sample represents a candidate with multiple features, including age, race, education levels, past working experience, and so on. However, distributions of these data features may differ across regions (covariate shift), and the correlations between predicted outcomes (whether to extend a job offer or not) and sensitive attributes (such as race) may also vary across regions (dependence shift). In this scenario, our proposed approach aims to develop a fairness-aware classifier capable of generalizing from data sampled from given geographical regions to unknown ones while simultaneously addressing potential covariate and dependence shifts.

**[W2, Q2]** To analyze the complexity of Algorithm 1, we initially address the complexity of learning the transformation model $T$. According to Algorithm 2 in the appendix, the complexity of learning $T$ is expressed as $O(n \cdot q \cdot p)$, where $n$ stands for the number of epochs, $q$ represents the number of batches, and $p$ signifies the number of iterations of the optimizer Adam. In Algorithm 1, the transformation model is employed to produce samples in synthetic domains. The complexity of Algorithm 1 can be defined as $O(t \cdot m \cdot (h + p))$, where $t$ denotes the number of epochs, $m$ indicates the number of batches, $h$ signifies the number of samples generated through $T$, and $p$ represents the number of iterations of Adam.

**[Q1]** Thanks for your suggestions! We read through the recommended paper and considered the following methods (AFN[a], RSC[b], FSCL[c]) mentioned in the paper as baselines. We will add the following results to the accepted version.

Evaluation of the FairFace dataset, where DP and Accuracy are higher, the better, and AUC_fair is lower, the better. The best performances are highlighted in bold.
  DP / AUC_fair / Accuracy    |       (B, 0.91)      |       (E, 0.87)      |       (I, 0.58)      |       (W, 0.49)      |       (L, 0.48)      |       (M, 0.87)      |       (S, 0.39)      |         Avg         |
|:-------------:|:-------------------:|:-------------------:|:-------------------:|:-------------------:|:-------------------:|:-------------------:|:-------------------:|:-------------------:|
|      AFN [a]  | 0.82 / **0.55** / 91.08 | 0.51 / 0.62 / 94.65 | 0.46 / 0.59 / 91.48 | 0.34 / 0.61 / 91.15 | 0.53 / 0.61 / 91.87 | 0.50 / 0.66 / 91.01 | 0.54 / 0.61 / 91.47 | 0.53 / 0.61 / 91.82 |
|      RSC [b]  | 0.88 / 0.56 / 91.73 | 0.34 / 0.64 / 92.89 | 0.42 / 0.58 / 91.91 | 0.43 / 0.59 / 91.00 | 0.52 / 0.63 / 91.88 | 0.51 / 0.66 / 91.47 | 0.43 / 0.59 / 91.00 | 0.53 / 0.61 / 91.66 |
|      FSCL [c] | 0.85 / 0.56 / 90.69 | 0.62 / 0.61 / 88.44 | 0.45 / 0.58 / 86.93 | 0.50 / 0.70 / 77.13 | 0.52 / 0.64 / 88.39 | 0.51 / 0.67 / 81.85 | 0.62 / 0.79 / 84.93 | 0.58 / 0.66 / 85.48 |
| FEDORA (Ours) | **0.94** / **0.55** / **93.91** | **0.87** / **0.60** / **95.91** | **0.48** / **0.57** / **92.55** | **0.52** / **0.58** / **93.02** | **0.58** / **0.59** / **93.73** | **0.54** / **0.62** / **92.61** | **0.98** / **0.55** / **92.26** | **0.70** / **0.58** / **93.42** |

Evaluation of the YFCC100M-FDG dataset, where DP and Accuracy are higher, the better, and AUC_fair is lower, the better. The best performances are highlighted in bold.
| DP / AUC_fair / Accuracy |      (d_0,0.73)     |      (d_1,0.84)     |      (d_2,0.72)     |         Avg         |
|:------------------------:|:-------------------:|:-------------------:|:-------------------:|:-------------------:|
|            AFN [a]       | 0.78 / 0.59 / 61.86 | 0.92 / 0.55 / 79.02 | 0.88 / 0.54 / 77.23 | 0.86 / 0.56 / 72.71 |
|            RSC [b]       | 0.78 / 0.58 / 59.66 | 0.93 / 0.54 / 79.23 | 0.90 / 0.54 / 77.51 | 0.87 / 0.55 / 72.13 |
|           FSCL [c]       | 0.79 / 0.72 / 58.35 | 0.89 / 0.72 / 69.53 | 0.90 / 0.73 / 67.78 | 0.86 / 0.72 / 65.23 |
|       FEDORA (Ours)      | **0.87** / **0.53** / **62.56** | **0.94** / **0.52** / **93.36** | **0.93** / **0.53** / **93.43** | **0.92** / **0.53** / **83.12** |


- [a] Ruijia Xu, Guanbin Li, Jihan Yang, and Liang Lin. Larger norm more transferable: An adaptive feature norm approach for unsupervised domain adaptation. In ICCV, 2019.
- [b] Zeyi Huang, Haohan Wang, Eric P Xing, and Dong Huang. Self-challenging improves cross-domain generalization. In ECCV, 2020.
- [c] Sungho Park, Jewook Lee, Pilhyeon Lee, Sunhee Hwang, Dohyung Kim, and Hyeran Byun. Fair contrastive learning for facial attribute classification. In CVPR, 2022.
