flowchart TD

A[Machine Learning] --> B[Supervised Learning]
A --> C[Unsupervised Learning]
A --> D[Reinforcement Learning]

%% Supervised Learning Split
B --> E[Regression]
B --> F[Classification]

%% Regression Branch
E --> E1[Linear Regression]
E --> E2[Polynomial Regression]
E --> E3[Ridge and Lasso Regression]
E --> E4[Decision Tree Regressor]
E --> E5[Random Forest Regressor]
E --> E6[Neural Networks for Regression]

%% Classification Branch
F --> F1[Logistic Regression]
F --> F2[Decision Tree Classifier]
F --> F3[Random Forest Classifier]
F --> F4[Support Vector Machine]
F --> F5[K-Nearest Neighbors]
F --> F6[Naive Bayes]
F --> F7[Neural Networks for Classification]

%% Neural Networks Branch
F7 --> G[Deep Learning]
E6 --> G

%% Deep Learning Types
G --> G1[Artificial Neural Network - ANN]
G --> G2[Convolutional Neural Network - CNN]
G --> G3[Recurrent Neural Network - RNN]
G --> G4[Transformers]

%% CNN Variants
G2 --> H1[LeNet]
G2 --> H2[AlexNet]
G2 --> H3[VGG]
G2 --> H4[ResNet]
G2 --> H5[Inception]
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
