# 🚀 Dog Breed Classification Pipeline (MobileNetV3)

## 📌 OVERALL PIPELINE
Dataset → Preprocessing → MobileNetV3 → Training → Analysis → Save Model → Deployment

---

## ✅ STEP 1 — Import Libraries
```python
import os
import numpy as np
import matplotlib.pyplot as plt
import tensorflow as tf
import pickle

from tensorflow.keras.preprocessing.image import ImageDataGenerator
from tensorflow.keras.applications import MobileNetV3Small
from tensorflow.keras.layers import Dense, GlobalAveragePooling2D, Dropout
from tensorflow.keras.models import Model
from tensorflow.keras.callbacks import EarlyStopping, ReduceLROnPlateau
✅ STEP 2 — Dataset Path
dataset_path = "/kaggle/input/datasets/jessicali9530/stanford-dogs-dataset/images/Images"

classes = os.listdir(dataset_path)
print("Total Classes:", len(classes))

✔ Expected: 120 dog breeds

🔍 ANALYSIS 1 — Problem Understanding
Fine-grained classification problem
Classes are visually similar (e.g., Labrador vs Golden Retriever)
Basic CNN performs poorly ❌
Transfer learning is required ✔

👉 Using MobileNetV3 pretrained on ImageNet

✅ STEP 3 — Data Generators
Training Generator (with augmentation)
train_datagen = ImageDataGenerator(
    rescale=1./255,
    validation_split=0.2,
    rotation_range=25,
    zoom_range=0.2,
    shear_range=0.2,
    horizontal_flip=True
)
Validation Generator
val_datagen = ImageDataGenerator(
    rescale=1./255,
    validation_split=0.2
)
🔍 ANALYSIS 2 — Why Augmentation?

Without augmentation:

Model memorizes images ❌

With augmentation:

Model learns general patterns ✔
✅ STEP 4 — Load Dataset
train_data = train_datagen.flow_from_directory(
    dataset_path,
    target_size=(224,224),
    batch_size=32,
    class_mode="categorical",
    subset="training"
)

val_data = val_datagen.flow_from_directory(
    dataset_path,
    target_size=(224,224),
    batch_size=32,
    class_mode="categorical",
    subset="validation"
)
✅ STEP 5 — Save Labels
pickle.dump(train_data.class_indices, open("labels.pkl","wb"))
🔍 ANALYSIS 3 — Why 224×224?
MobileNetV3 is trained on 224 × 224 images
Matching input size improves feature extraction ✔
✅ STEP 6 — Load MobileNetV3 (Pretrained)
base_model = MobileNetV3Small(
    input_shape=(224,224,3),
    include_top=False,
    weights="imagenet"
)

for layer in base_model.layers:
    layer.trainable = False
🔍 ANALYSIS 4 — What is Transfer Learning?

Instead of training from scratch:

Reuse pretrained knowledge ✔

MobileNet already understands:

Edges
Shapes
Textures
✅ STEP 7 — Add Custom Layers
x = base_model.output
x = GlobalAveragePooling2D()(x)

x = Dense(256, activation="relu")(x)
x = Dropout(0.5)(x)

output = Dense(train_data.num_classes, activation="softmax")(x)

model = Model(inputs=base_model.input, outputs=output)
🔍 ANALYSIS 5 — Architecture Reasoning
Base model → Feature extractor
Dense layer → Learns breed-specific patterns
Dropout → Prevents overfitting
✅ STEP 8 — Compile Model
model.compile(
    optimizer=tf.keras.optimizers.Adam(learning_rate=0.0001),
    loss="categorical_crossentropy",
    metrics=["accuracy"]
)
✅ STEP 9 — Callbacks
early_stop = EarlyStopping(
    monitor="val_loss",
    patience=3,
    restore_best_weights=True
)

reduce_lr = ReduceLROnPlateau(
    monitor="val_loss",
    factor=0.3,
    patience=2,
    min_lr=1e-6
)
🔍 ANALYSIS 6 — Why Callbacks?
EarlyStopping → Stops overfitting
ReduceLR → Improves convergence
✅ STEP 10 — Train Model
history = model.fit(
    train_data,
    validation_data=val_data,
    epochs=15,
    callbacks=[early_stop, reduce_lr]
)
🔍 ANALYSIS 7 — Expected Results
Model	Accuracy
CNN	~20%
MobileNetV3	70–85%

🚀 Significant improvement!

✅ STEP 11 — Plot Accuracy
plt.plot(history.history["accuracy"])
plt.plot(history.history["val_accuracy"])
plt.title("MobileNetV3 Accuracy")
plt.legend(["Train","Validation"])
plt.show()
🔍 ANALYSIS 8 — Good Graph Indicators

✔ Both curves increasing
✔ Small gap between training & validation

✅ STEP 12 — Save Model
model.save("dog_mobilenetv3.keras")
✅ STEP 13 — Test Prediction
from tensorflow.keras.preprocessing import image

img_path = "/kaggle/input/datasets/jessicali9530/stanford-dogs-dataset/images/Images/n02086646-Blenheim_spaniel/n02086646_1002.jpg"

img = image.load_img(img_path, target_size=(224,224))
img_array = image.img_to_array(img)/255.0
img_array = np.expand_dims(img_array, axis=0)

prediction = model.predict(img_array)

labels = pickle.load(open("labels.pkl","rb"))
labels = dict((v,k) for k,v in labels.items())

print(labels[np.argmax(prediction)])
🎯 FINAL OUTPUT FILES
dog_mobilenetv3.keras
labels.pkl
🧠 FINAL UNDERSTANDING
Concept	What You Learned
CNN	Basic feature learning
MobileNetV3	Transfer learning
Augmentation	Improve generalization
Callbacks	Control training
Deployment	Real-world AI application
