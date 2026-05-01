# Complete Machine Learning Guide: Flowcharts & Tables

## 📊 Main Flowchart: Complete ML Decision Tree

```mermaid
flowchart TD
    A[Start: What type of data do you have] --> B{Data Type}
    
    B -->|Numbers/Tables| T1[Tabular Data]
    B -->|Images/Pixels| I1[Image Data]
    B -->|Text/Words| TX1[Text Data]
    B -->|Time/Sequences| TS1[Time Series]
    B -->|No Labels| U1[Unsupervised]
    
    T1 --> T2{Task Type}
    T2 -->|Predict Number| REG[Regression Models]
    T2 -->|Predict Category| CLS[Classification Models]
    
    REG --> R1["Linear Regression<br/>Best: Simple relationships<br/>Data: Small, clean"]
    REG --> R2["Decision Tree Reg<br/>Best: Easy to explain<br/>Data: Mixed features"]
    REG --> R3["Random Forest Reg<br/>Best: High accuracy<br/>Data: Medium-large"]
    REG --> R4["Neural Network Reg<br/>Best: Complex patterns<br/>Data: Large, non-linear"]
    
    CLS --> C1["Logistic Regression<br/>Best: Binary outcomes<br/>Data: Linear separable"]
    CLS --> C2["Decision Tree Classifier<br/>Best: Explainable results<br/>Data: Any size"]
    CLS --> C3["Random Forest Classifier<br/>Best: High accuracy<br/>Data: Medium-large"]
    CLS --> C4["SVM<br/>Best: Clear boundaries<br/>Data: Small-medium"]
    CLS --> C5["KNN<br/>Best: Simple baseline<br/>Data: Small, clean"]
    CLS --> C6["Naive Bayes<br/>Best: Text categories<br/>Data: High dimensions"]
    
    I1 --> I2{What is your goal}
    
    I2 -->|Classify image content| IMG_CLASS[Image Classification]
    I2 -->|Find objects in image| IMG_DETECT[Object Detection]
    I2 -->|Split image into parts| IMG_SEGMENT[Segmentation]
    I2 -->|Generate new images| IMG_GEN[Generation]
    
    IMG_CLASS --> IC1["STEP 1: LeNet-5<br/>Best: LEARNING FIRST<br/>Works: 32x32 grayscale"]
    IMG_CLASS --> IC2["STEP 2: AlexNet<br/>Best: Understanding CNNs<br/>Works: 227x227 color"]
    IMG_CLASS --> IC3["STEP 3: VGG16-VGG19<br/>Best: Transfer learning<br/>Works: 224x224 color"]
    IMG_CLASS --> IC4["STEP 4: ResNet<br/>Best: PRODUCTION USE<br/>Works: Any size"]
    IMG_CLASS --> IC5["Inception-GoogLeNet<br/>Best: Complex scenes<br/>Works: 299x299 color"]
    IMG_CLASS --> IC6["MobileNet<br/>Best: Mobile-Edge<br/>Works: Compressed images"]
    IMG_CLASS --> IC7["EfficientNet<br/>Best: Latest SOTA<br/>Works: Flexible sizes"]
    
    IMG_DETECT --> OD1["YOLO<br/>Best: Real-time detection<br/>Use: Videos, live camera"]
    IMG_DETECT --> OD2["Faster R-CNN<br/>Best: High accuracy<br/>Use: Quality over speed"]
    IMG_DETECT --> OD3["SSD<br/>Best: Balance speed-accuracy<br/>Use: General purpose"]
    IMG_DETECT --> OD4["RetinaNet<br/>Best: Small objects<br/>Use: Many small objects"]
    
    IMG_SEGMENT --> SG1["U-Net<br/>Best: Medical images<br/>Use: Precise boundaries"]
    IMG_SEGMENT --> SG2["Mask R-CNN<br/>Best: Instance segmentation<br/>Use: Detect + segment"]
    IMG_SEGMENT --> SG3["DeepLab<br/>Best: Semantic segmentation<br/>Use: Scene understanding"]
    
    IMG_GEN --> GN1["Autoencoders<br/>Best: Learning first<br/>Use: Image compression"]
    IMG_GEN --> GN2["GANs<br/>Best: Realistic generation<br/>Use: Create faces, art"]
    IMG_GEN --> GN3["Diffusion Models<br/>Best: State-of-the-art<br/>Use: Text-to-image"]
    IMG_GEN --> GN4["VAE<br/>Best: Controlled generation<br/>Use: Image interpolation"]
    
    TX1 --> TX2{Task Type}
    TX2 -->|Classification| TXC["Naive Bayes<br/>Best: Spam detection<br/>Use: Simple text tasks"]
    TX2 -->|Generation| TXL["Transformers BERT-GPT<br/>Best: LLMs, translation<br/>Use: Complex text"]
    TX2 -->|Sentiment| TXS["LSTM-RNN<br/>Best: Sentiment analysis<br/>Use: Sequence tasks"]
    
    TS1 --> TS2["LSTM-GRU<br/>Best: Stock, weather<br/>Use: Long patterns"]
    TS1 --> TS3["Prophet<br/>Best: Business forecasting<br/>Use: Seasonal data"]
    TS1 --> TS4["ARIMA-SARIMA<br/>Best: Traditional stats<br/>Use: Small datasets"]
    
    U1 --> U2[Clustering]
    U1 --> U3[Dimensionality Reduction]
    U2 --> KMEANS["K-Means<br/>Best: Customer segments"]
    U2 --> DBSCAN["DBSCAN<br/>Best: Arbitrary shapes"]
    U3 --> PCA["PCA<br/>Best: Visualization"]
    U3 --> TSNE["t-SNE<br/>Best: 2D plotting"]
    
    A --> RL[Reinforcement Learning]
    RL --> RL1["Q-Learning<br/>Best: Discrete actions<br/>Use: Games, grids"]
    RL --> RL2["Deep Q-Network<br/>Best: Complex states<br/>Use: Atari games"]
    RL --> RL3["Policy Gradient<br/>Best: Continuous actions<br/>Use: Robot control"]
    
    IC4 -.-> BEST1[Best Overall: ResNet50]
    OD1 -.-> BEST2[Best Real-time: YOLOv8]
    SG1 -.-> BEST3[Best Medical: U-Net]
