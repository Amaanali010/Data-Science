## Complete Machine Learning Flowchart - Including Image Data Models

```mermaid
flowchart TD
    A[Start: What type of data do you have] --> B{Data Type}
    
    B -->|Numbers/Tables| T1[Tabular Data]
    B -->|Images/Pixels| I1[Image Data]
    B -->|Text/Words| TX1[Text Data]
    B -->|Time/Sequences| TS1[Time Series]
    B -->|No Labels| U1[Unsupervised]
    
    %% TABULAR DATA PATH
    T1 --> T2{Task Type}
    T2 -->|Predict Number| REG[Regression Models]
    T2 -->|Predict Category| CLS[Classification Models]
    
    REG --> R1["Linear Regression /n Best: Simple relationships /n Data: Small, clean"]
    REG --> R2["Decision Tree Reg /n Best: Easy to explain /n Data: Mixed features"]
    REG --> R3["Random Forest Reg /n Best: High accuracy /n Data: Medium-large"]
    REG --> R4["Neural Network Reg /n Best: Complex patterns /n Data: Large, non-linear"]
    
    CLS --> C1["Logistic Regression /n Best: Binary outcomes /n Data: Linear separable"]
    CLS --> C2["Decision Tree Classifier /n Best: Explainable results /n Data: Any size"]
    CLS --> C3["Random Forest Classifier /n Best: High accuracy /n Data: Medium-large"]
    CLS --> C4["SVM /n Best: Clear boundaries /n Data: Small-medium"]
    CLS --> C5["KNN /n Best: Simple baseline /n Data: Small, clean"]
    CLS --> C6["Naive Bayes /n Best: Text categories /n Data: High dimensions"]
    
    %% IMAGE DATA PATH
    I1 --> I2{What is your goal}
    
    I2 -->|Classify image content| IMG_CLASS[Image Classification]
    I2 -->|Find objects in image| IMG_DETECT[Object Detection]
    I2 -->|Split image into parts| IMG_SEGMENT[Segmentation]
    I2 -->|Generate new images| IMG_GEN[Generation]
    
    %% Image Classification Models
    IMG_CLASS --> IC1["STEP 1: LeNet-5 /n Best for: LEARNING FIRST /n Works with: 32x32 grayscale"]
    IMG_CLASS --> IC2["STEP 2: AlexNet /n Best for: Understanding CNNs /n Works with: 227x227 color"]
    IMG_CLASS --> IC3["STEP 3: VGG16-VGG19 /n Best for: Transfer learning /n Works with: 224x224 color"]
    IMG_CLASS --> IC4["STEP 4: ResNet /n Best for: PRODUCTION USE /n Works with: Any size"]
    IMG_CLASS --> IC5["Inception-GoogLeNet /n Best for: Complex scenes /n Works with: 299x299 color"]
    IMG_CLASS --> IC6["MobileNet /n Best for: Mobile-Edge /n Works with: Compressed images"]
    IMG_CLASS --> IC7["EfficientNet /n Best for: Latest SOTA /n Works with: Flexible sizes"]
    
    %% Object Detection Models
    IMG_DETECT --> OD1["YOLO /n Best for: Real-time detection /n Use: Videos, live camera"]
    IMG_DETECT --> OD2["Faster R-CNN /n Best for: High accuracy /n Use: Quality over speed"]
    IMG_DETECT --> OD3["SSD /n Best for: Balance speed-accuracy /n Use: General purpose"]
    IMG_DETECT --> OD4["RetinaNet /n Best for: Small objects /n Use: Many small objects"]
    
    %% Segmentation Models
    IMG_SEGMENT --> SG1["U-Net /n Best for: Medical images /n Use: Precise boundaries"]
    IMG_SEGMENT --> SG2["Mask R-CNN /n Best for: Instance segmentation /n Use: Detect + segment"]
    IMG_SEGMENT --> SG3["DeepLab /n Best for: Semantic segmentation /n Use: Scene understanding"]
    
    %% Generation Models
    IMG_GEN --> GN1["Autoencoders /n Best for: Learning first /n Use: Image compression"]
    IMG_GEN --> GN2["GANs /n Best for: Realistic generation /n Use: Create faces, art"]
    IMG_GEN --> GN3["Diffusion Models /n Best for: State-of-the-art /n Use: Text-to-image"]
    IMG_GEN --> GN4["VAE /n Best for: Controlled generation /n Use: Image interpolation"]
    
    %% TEXT DATA PATH
    TX1 --> TX2{Task Type}
    TX2 -->|Classification| TXC["Naive Bayes /n Best: Spam detection /n Use: Simple text tasks"]
    TX2 -->|Generation| TXL["Transformers BERT-GPT /n Best: LLMs, translation /n Use: Complex text"]
    TX2 -->|Sentiment| TXS["LSTM-RNN /n Best: Sentiment analysis /n Use: Sequence tasks"]
    
    %% TIME SERIES
    TS1 --> TS2["LSTM-GRU /n Best: Stock, weather /n Use: Long patterns"]
    TS1 --> TS3["Prophet /n Best: Business forecasting /n Use: Seasonal data"]
    TS1 --> TS4["ARIMA-SARIMA /n Best: Traditional stats /n Use: Small datasets"]
    
    %% UNSUPERVISED
    U1 --> U2[Clustering]
    U1 --> U3[Dimensionality Reduction]
    U2 --> KMEANS["K-Means /n Best: Customer segments"]
    U2 --> DBSCAN["DBSCAN /n Best: Arbitrary shapes"]
    U3 --> PCA["PCA /n Best: Visualization"]
    U3 --> TSNE["t-SNE /n Best: 2D plotting"]
    
    %% REINFORCEMENT LEARNING
    A --> RL[Reinforcement Learning]
    RL --> RL1["Q-Learning /n Best: Discrete actions /n Use: Games, grids"]
    RL --> RL2["Deep Q-Network /n Best: Complex states /n Use: Atari games"]
    RL --> RL3["Policy Gradient /n Best: Continuous actions /n Use: Robot control"]
    
    %% QUICK DECISION PATHS



flowchart LR
    W1[Week 1-2: LeNet-5] --> W2[Week 3-4: AlexNet]
    W2 --> W3[Week 5-6: VGG16]
    W3 --> W4[Week 7-8: ResNet50]
    W4 --> W5[Week 9-10: YOLO or U-Net]



    Do you have images?
│
├─> Less than 1,000 images
│   └─> USE: VGG16 with Transfer Learning (you don't need more data!)
│
├─> More than 10,000 images + need best accuracy
│   └─> USE: ResNet50 or EfficientNet
│
├─> Need real-time (video, camera, mobile)
│   └─> USE: MobileNetV3 or YOLOv8
│
├─> Medical image (X-ray, MRI, CT scan)
│   └─> USE: U-Net
│
├─> Detect objects + draw bounding boxes
│   └─> USE: YOLOv8 (easy) or Faster R-CNN (accurate)
│
├─> Each pixel needs a label (car, road, sky)
│   └─> USE: DeepLab or Mask R-CNN
│
└─> Generate new images
    └─> USE: Stable Diffusion or StyleGAN
    IC4 -.-> BEST1[Best Overall: ResNet50]
    OD1 -.-> BEST2[Best Real-time: YOLOv8]
    SG1 -.-> BEST3[Best Medical: U-Net]
