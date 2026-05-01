G2 --> H6[MobileNet]

H6 --> H61[MobileNetV1]
H6 --> H62[MobileNetV2]
H6 --> H63[MobileNetV3]

%% Unsupervised Learning
C --> C1[Clustering]
C --> C2[Dimensionality Reduction]

C1 --> C11[K-Means]
C1 --> C12[Hierarchical Clustering]
C1 --> C13[DBSCAN]

C2 --> C21[PCA]
C2 --> C22[t-SNE]

%% Reinforcement Learning
D --> D1[Q-Learning]
D --> D2[Deep Q Networks]
D --> D3[Policy Gradient Methods]
🔧 What was wrong (quickly)
❌ Multiple arrows on one line
❌ Comments mixed with code on same line
❌ Missing line breaks
