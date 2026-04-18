# 🐾 MobileNetV2 Animal Classifier (Kaggle + Deployment Guide)

🔗 **Live App:** https://huggingface.co/spaces/Amaanali01/Animal-Classifier-MobileNetV2-Model

---

## 📁 Dataset Structure

```
animals/
 ├── lion/
 ├── tiger/
 ├── dog/
 ├── cat/
 └── ...
```

Each folder = class name

---

## 🚀 STEP 1 — Import Libraries

```python
import tensorflow as tf
import numpy as np
import matplotlib.pyplot as plt
import pickle

from tensorflow.keras.preprocessing.image import ImageDataGenerator
from tensorflow.keras.callbacks import EarlyStopping
from tensorflow.keras.layers import Dense, Dropout, GlobalAveragePooling2D
from tensorflow.keras.models import Model
from tensorflow.keras.applications import MobileNetV2
```

---

## 📂 STEP 2 — Dataset Path

```python
dataset_path = "/kaggle/input/animals/animals"
```

---

## 🔄 STEP 3 — Image Augmentation

```python
datagen = ImageDataGenerator(
    rescale=1./255,
    validation_split=0.2,
    rotation_range=20,
    zoom_range=0.2,
    width_shift_range=0.2,
    height_shift_range=0.2,
    horizontal_flip=True
)
```

---

## 🧠 STEP 4 — Load Training Dataset

```python
train_data = datagen.flow_from_directory(
    dataset_path,
    target_size=(224,224),
    batch_size=32,
    class_mode="categorical",
    subset="training"
)
```

---

## ✅ STEP 5 — Load Validation Dataset

```python
val_data = datagen.flow_from_directory(
    dataset_path,
    target_size=(224,224),
    batch_size=32,
    class_mode="categorical",
    subset="validation"
)
```

---

## ⚙️ STEP 6 — Load MobileNetV2 Pretrained Model

```python
base_model = MobileNetV2(
    input_shape=(224,224,3),
    include_top=False,
    weights="imagenet"
)

for layer in base_model.layers:
    layer.trainable = False
```

---

## 🧩 STEP 7 — Add Custom Classification Layers

```python
x = base_model.output
x = GlobalAveragePooling2D()(x)
x = Dense(128, activation="relu")(x)
x = Dropout(0.5)(x)

predictions = Dense(train_data.num_classes, activation="softmax")(x)

model = Model(inputs=base_model.input, outputs=predictions)
```

---

## 🛠 STEP 8 — Compile Model

```python
model.compile(
    optimizer="adam",
    loss="categorical_crossentropy",
    metrics=["accuracy"]
)
```

---

## ⏹ STEP 9 — Add EarlyStopping

```python
early_stop = EarlyStopping(
    monitor="val_loss",
    patience=5,
    restore_best_weights=True
)
```

---

## 🔥 STEP 10 — Train Model

```python
history = model.fit(
    train_data,
    validation_data=val_data,
    epochs=20,
    callbacks=[early_stop]
)
```

---

## 📊 STEP 11 — Plot Accuracy Graph

```python
plt.plot(history.history["accuracy"])
plt.plot(history.history["val_accuracy"])

plt.title("MobileNetV2 Accuracy")
plt.legend(["Train","Validation"])

plt.show()
```

---

## 💾 STEP 12 — Save Trained Model

```python
model.save("animal_mobilenet_model.keras")
```

---

## 🏷 STEP 13 — Save Labels File

```python
labels = train_data.class_indices
pickle.dump(labels, open("labels.pkl","wb"))
```

---

## 📦 STEP 14 — Zip Files

```python
import zipfile

zipf = zipfile.ZipFile("animal_model.zip", "w")

zipf.write("animal_mobilenet_model.keras")
zipf.write("labels.pkl")

zipf.close()
```

---

## 🌐 STEP 15 — Streamlit App (app.py)

```python
import streamlit as st
import tensorflow as tf
import numpy as np
import pickle
from tensorflow.keras.preprocessing import image

model = tf.keras.models.load_model("animal_mobilenet_model.keras")
labels = pickle.load(open("labels.pkl","rb"))

class_names = list(labels.keys())

st.title("🐾 Animal Classifier (MobileNetV2)")

uploaded_file = st.file_uploader("Upload Animal Image")

if uploaded_file:
    img = image.load_img(uploaded_file, target_size=(224,224))
    img_array = image.img_to_array(img)/255
    img_array = np.expand_dims(img_array, axis=0)

    prediction = model.predict(img_array)
    predicted_class = class_names[np.argmax(prediction)]

    st.success(f"Predicted Animal: {predicted_class}")
```

---

## 📋 STEP 16 — requirements.txt

```
streamlit
tensorflow
numpy
pillow
```

---

## 📁 Final Files for Deployment

```
animal_mobilenet_model.keras
labels.pkl
app.py
requirements.txt
```

---

## 🎓 Learning Outcome

* KNN → basic ML image classifier
* CNN → deep learning from scratch
* MobileNetV2 → real-world production AI model

---

🚀 Your model is now ready for deployment!
