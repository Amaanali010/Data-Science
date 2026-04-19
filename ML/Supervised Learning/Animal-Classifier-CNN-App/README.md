# 🐾 Animal Classification Using CNN (Final Student Guide – Kaggle Notebook)


🔗 **Live App:** https://huggingface.co/spaces/Amaanali01/Animal-Classifier-CNN-App



## ✅ Expected Result
- Validation accuracy: **60% – 80%**
- Depends on dataset quality

---

## 📌 STEP 1 — Open Kaggle Notebook

1. Go to **Kaggle → New Notebook**
2. Attach dataset: **90 Animals Dataset**

### Dataset Structure
```
animals/
 ├── lion/
 ├── tiger/
 ├── dog/
 ├── cat/
```

Each folder = one class

---

## 📌 STEP 2 — Import Required Libraries

```python
import tensorflow as tf
import numpy as np
import matplotlib.pyplot as plt
import pickle

from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Conv2D, MaxPooling2D
from tensorflow.keras.layers import Flatten, Dense, Dropout
from tensorflow.keras.preprocessing.image import ImageDataGenerator
from tensorflow.keras.callbacks import EarlyStopping
```

---

## 📌 STEP 3 — Define Dataset Path

```python
dataset_path = "/kaggle/input/animals/animals"
```

*(Change if dataset name differs)*

---

## 📌 STEP 4 — Image Augmentation (Fix Overfitting) ✅

```python
datagen = ImageDataGenerator(

    rescale=1./255,

    validation_split=0.2,

    rotation_range=20,

    width_shift_range=0.2,

    height_shift_range=0.2,

    zoom_range=0.2,

    horizontal_flip=True
)
```

---

## 📌 STEP 5 — Load Training Dataset

```python
train_data = datagen.flow_from_directory(

    dataset_path,

    target_size=(128,128),

    batch_size=32,

    class_mode="categorical",

    subset="training"
)
```

---

## 📌 STEP 6 — Load Validation Dataset

```python
val_data = datagen.flow_from_directory(

    dataset_path,

    target_size=(128,128),

    batch_size=32,

    class_mode="categorical",

    subset="validation"
)
```

### Example Output
```
Found 4320 images belonging to 90 classes
```

---

## 📌 STEP 7 — Build Improved CNN Model

```python
model = Sequential()

model.add(Conv2D(32,(3,3),activation="relu",input_shape=(128,128,3)))
model.add(MaxPooling2D(2,2))

model.add(Conv2D(64,(3,3),activation="relu"))
model.add(MaxPooling2D(2,2))

model.add(Conv2D(128,(3,3),activation="relu"))
model.add(MaxPooling2D(2,2))

model.add(Flatten())

model.add(Dense(128,activation="relu"))
model.add(Dropout(0.5))

model.add(Dense(train_data.num_classes,activation="softmax"))
```

---

## 📌 STEP 8 — Compile Model

```python
model.compile(

    optimizer="adam",

    loss="categorical_crossentropy",

    metrics=["accuracy"]

)
```

---

## 📌 STEP 9 — Add EarlyStopping (Stops Overfitting Automatically)

```python
early_stop = EarlyStopping(

    monitor="val_loss",

    patience=5,

    restore_best_weights=True

)
```

---

## 📌 STEP 10 — Train CNN Model

```python
history = model.fit(

    train_data,

    validation_data=val_data,

    epochs=25,

    callbacks=[early_stop]

)
```

---

## 📌 STEP 11 — Plot Accuracy Graph

```python
plt.plot(history.history["accuracy"])
plt.plot(history.history["val_accuracy"])

plt.title("Model Accuracy")

plt.legend(["Train","Validation"])

plt.show()
```

---

## 📌 STEP 12 — Save Trained Model (Deployment File)

```python
model.save("animal_cnn_model.keras")
```

### Output
```
animal_cnn_model.keras
```

---

## 📌 STEP 13 — Save Class Labels

```python
labels = train_data.class_indices

pickle.dump(labels, open("labels.pkl","wb"))
```

### Output
```
labels.pkl
```

---

## 📌 STEP 14 — Test Model on New Image

```python
from tensorflow.keras.preprocessing import image

img = image.load_img(

    "/kaggle/input/test-image/lion.jpg",

    target_size=(128,128)

)

img_array = image.img_to_array(img)/255

img_array = np.expand_dims(img_array,axis=0)

prediction = model.predict(img_array)

predicted_class = np.argmax(prediction)

print(predicted_class)
```

---

## 📌 STEP 15 — Create Streamlit App (Hugging Face Deployment)

### Create file: `app.py`

```python
import streamlit as st
import tensorflow as tf
import numpy as np
import pickle
from tensorflow.keras.preprocessing import image

model = tf.keras.models.load_model("animal_cnn_model.keras")

labels = pickle.load(open("labels.pkl","rb"))

class_names = list(labels.keys())

st.title("Animal Classifier CNN App")

uploaded_file = st.file_uploader("Upload Animal Image")

if uploaded_file:

    img = image.load_img(uploaded_file,target_size=(128,128))

    img_array = image.img_to_array(img)/255

    img_array = np.expand_dims(img_array,axis=0)

    prediction = model.predict(img_array)

    predicted_class = class_names[np.argmax(prediction)]

    st.success(f"Predicted Animal: {predicted_class}")
```

---

## 📌 STEP 16 — requirements.txt for Hugging Face

### Create file: `requirements.txt`

```
streamlit
tensorflow
numpy
pillow
```

---

## 🚀 FINAL FILES READY FOR DEPLOYMENT

Upload these to Hugging Face:

- `animal_cnn_model.keras`
- `labels.pkl`
- `app.py`
- `requirements.txt`

---

## 🎓 Teaching Tip (Important Insight for Students)

**Explain this learning pipeline:**

- Traditional ML → KNN → Low accuracy  
- Deep Learning → CNN → High accuracy  

---

✅ Your CNN animal classifier is now ready to deploy online!
