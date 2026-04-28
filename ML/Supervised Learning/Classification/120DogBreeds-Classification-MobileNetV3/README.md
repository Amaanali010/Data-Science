🚀 Dog Breed Classification using MobileNetV3
📌 STEP 1 — Import Libraries
import os
import numpy as np
import matplotlib.pyplot as plt
import tensorflow as tf
import pickle

from tensorflow.keras.preprocessing.image import ImageDataGenerator
from tensorflow.keras.applications import MobileNetV3Small
from tensorflow.keras.applications.mobilenet_v3 import preprocess_input
from tensorflow.keras.layers import Dense, GlobalAveragePooling2D, Dropout
from tensorflow.keras.models import Model
📌 STEP 2 — Dataset Path
dataset_path = "/kaggle/input/datasets/jessicali9530/stanford-dogs-dataset/images/Images"

print("Total Classes:", len(os.listdir(dataset_path)))

✔ Expected Output: 120 classes

📌 STEP 3 — Data Generators (CRITICAL FIX)
✅ Training Generator (with augmentation)
train_datagen = ImageDataGenerator(
    preprocessing_function=preprocess_input,
    validation_split=0.2,
    rotation_range=25,
    zoom_range=0.2,
    horizontal_flip=True
)
✅ Validation Generator (NO augmentation + shuffle OFF)
val_datagen = ImageDataGenerator(
    preprocessing_function=preprocess_input,
    validation_split=0.2
)
📌 STEP 4 — Load Dataset (IMPORTANT SETTINGS)
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
    subset="validation",
    shuffle=False   # 🔥 VERY IMPORTANT
)
📌 STEP 5 — Save Labels
pickle.dump(train_data.class_indices, open("labels.pkl","wb"))
📌 STEP 6 — Load MobileNetV3
base_model = MobileNetV3Small(
    input_shape=(224,224,3),
    include_top=False,
    weights="imagenet"
)
📌 STEP 7 — Fine-Tuning (MOST IMPORTANT STEP)
# Freeze early layers
for layer in base_model.layers[:-30]:
    layer.trainable = False

# Train last layers
for layer in base_model.layers[-30:]:
    layer.trainable = True
📌 STEP 8 — Build Model
x = base_model.output
x = GlobalAveragePooling2D()(x)

x = Dense(512, activation="relu")(x)
x = Dropout(0.5)(x)

output = Dense(train_data.num_classes, activation="softmax")(x)

model = Model(inputs=base_model.input, outputs=output)
📌 STEP 9 — Compile Model
model.compile(
    optimizer=tf.keras.optimizers.Adam(learning_rate=0.0001),
    loss="categorical_crossentropy",
    metrics=["accuracy"]
)
📌 STEP 10 — Train Model (NO EarlyStopping for Debug)
history = model.fit(
    train_data,
    validation_data=val_data,
    epochs=10
)

👉 IMPORTANT: Do NOT use EarlyStopping yet

📌 STEP 11 — Plot Accuracy
plt.plot(history.history["accuracy"])
plt.plot(history.history["val_accuracy"])

plt.title("MobileNetV3 Accuracy")
plt.xlabel("Epoch")
plt.ylabel("Accuracy")

plt.legend(["Train","Validation"])

plt.show()
📌 STEP 12 — Plot Loss
plt.plot(history.history["loss"])
plt.plot(history.history["val_loss"])

plt.title("Model Loss")
plt.xlabel("Epoch")
plt.ylabel("Loss")

plt.legend(["Train","Validation"])

plt.show()
📌 STEP 13 — Save Model
model.save("dog_mobilenetv3.keras")
📌 STEP 14 — Test Prediction
from tensorflow.keras.preprocessing import image

img_path = "/kaggle/input/datasets/jessicali9530/stanford-dogs-dataset/images/Images/n02086646-Blenheim_spaniel/n02086646_1002.jpg"

img = image.load_img(img_path, target_size=(224,224))
img_array = image.img_to_array(img)

img_array = preprocess_input(img_array)
img_array = np.expand_dims(img_array, axis=0)

prediction = model.predict(img_array)
📌 STEP 15 — Convert to Label
labels = pickle.load(open("labels.pkl","rb"))
labels = dict((v,k) for k,v in labels.items())

print("Prediction:", labels[np.argmax(prediction)])
🎯 Expected Results
Epoch	Validation Accuracy
1	20–30%
3	40–60%
5	60–75%
🧠 Key Concepts
🔹 Pretrained Model
MobileNetV3Small(weights="imagenet")

A model already trained on large datasets like ImageNet.

🔹 Transfer Learning

Reuse learned features (edges, shapes, textures) for a new task.

✔ Faster training
✔ Better accuracy
✔ Less data needed

🔹 Fine-Tuning
for layer in base_model.layers[:-30]:
    layer.trainable = False

for layer in base_model.layers[-30:]:
    layer.trainable = True

✔ Early layers → General features
✔ Last layers → Dog breed specialization

🧠 How CNN Understands Images
🔹 1. Edges (Early Layers)
Lines, boundaries
Example: dog outline
🔹 2. Shapes (Middle Layers)
Face, legs, structure
🔹 3. Textures (Deep Layers)
Fur patterns
Breed-specific details
🎯 Summary
Layer Type	Learns
Early	Edges
Middle	Shapes
Deep	Textures & Objects
🚀 Next Steps

✔ Build Gradio app
✔ Deploy on Hugging Face Spaces
✔ Share results (20% → 75% improvement)
