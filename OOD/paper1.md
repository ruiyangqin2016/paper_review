# Generalized Out-of-Distribution Detection: A Survey
OOD is relative to ID, which means in-distribution. For ID, the test dataset is from the same distribution as the training dataset. But in the real-world cases, the machine learning model might occur situations which don't belong to its data domain. There are five types of such situation: AD, ND, OSR, OOD, and OD. 
## Generalized OOD Detection
1. Anomaly Detection (AD): Detect any anomalous samples that are deviated from the predefined normality during testing. 
2. Novelty Detection (ND): Detect any test samples that do not fall into any training category. Prepared for future constructive procedures.
3. Open Set Recognition (OSR): OSR requires the multi-class classifier to simultaneously: (1) accurately classify test samples that from "known known class" and "detect test samples from unknown unknown class"
4. Out-of Distribution (OOD): Detect test samples with nono-overlapping labels with respect to train data. Semantic shift
5. Outlier Detection (OD): Detect samples that are markedly different from the others in the given observation set, due to either covariate or semantic shift.
## Anomaly Detection & One-class Novelty Detection: Methodology
1. Density-based methods (Clustering?):*Assuming that anomalous test data has low likehood whereas normal data has higher likelihood under the estimated density model* <br/>
    a. Parametric Density Estimation <br/>
    b. AE/VAE-based Models <br/>
    c. GAN-based Models <br/>
    d. Flow-based Models <br/>
    e. Representation Enhancement <br/>
2. Reconstruction-based methods: The encoder-decoder framework trained on the ID data usually yields different outcomes for ID and OOD samples. The difference in models performance can be utilized as an indicator for detecting anaomalies.
3. Classification-based methods: <br/>
    a. One-class classification <br/>
    b. Positive-unlabeled learning <br/>
    c. Self-supervised learning <br/>
## Open Set Recognition & Multi-class Novelty Detection: Methology
