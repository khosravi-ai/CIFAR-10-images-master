# CIFAR-10 Image Classification with MobileNetV2

This project demonstrates image classification on the **CIFAR-10 dataset** using a Convolutional Neural Network (CNN) based on **MobileNetV2**.  
The project was implemented in **Google Colab** with TensorFlow/Keras.

---

## 📂 Dataset
The dataset used is [CIFAR-10](https://www.cs.toronto.edu/~kriz/cifar.html), which contains **60,000 color images** (32x32 pixels) across 10 categories:

- Airplane, Automobile, Bird, Cat, Deer, Dog, Frog, Horse, Ship, Truck  

Split:
- **Training**: 50,000 images  
- **Testing**: 10,000 images  

The dataset was organized into train/test folders before training.

---

## ⚙️ Preprocessing
- Images rescaled to `[0, 1]` using `ImageDataGenerator`.  
- Data loaded with directory-based generator (`flow_from_directory`).  
- Classes mapped automatically from folder names.  

---

## 🏗️ Model Architecture
The model was built using **MobileNetV2** (without pretrained weights), with the following structure:

1. **Input Layer**: (32, 32, 3)  
2. **MobileNetV2 base** (no top layers, trained from scratch)  
3. **GlobalAveragePooling2D**  
4. **Dense (Softmax, 10 classes)**  

Optimizer: `Adam`  
Loss: `categorical_crossentropy`  
Metrics: `accuracy`  

---

## 🚀 Training
- Epochs: up to 20  
- Batch size: 32  
- EarlyStopping: patience=7  
- ModelCheckpoint: saves the best model (`mobilenet_best.h5`)  

Example output:
Epoch 20/20
1563/1563 - accuracy: 0.8175 - loss: 0.5249 - val_accuracy: 0.7299 - val_loss: 0.8523


---

## 📊 Results
- **Training Accuracy**: ~81.7%  
- **Validation Accuracy**: ~73.0%  
- **Training Loss**: ~0.52  
- **Validation Loss**: ~0.85  

---

## 📌 Future Improvements
- Use **pretrained MobileNetV2 (ImageNet weights)** with transfer learning.  
- Apply **Data Augmentation** (rotation, flipping, brightness, zoom).  
- Experiment with **Batch Normalization** and different optimizers.  
- Increase the number of epochs to allow the model to converge further (training was stopped at 20 epochs).  
- Try alternative architectures such as **ResNet** or **VGG** — although these models typically require **much longer training time**, they can potentially achieve higher accuracy.  

---

## 💡 Notes
- Alternative architectures like **ResNet** and **VGG** were considered, but they required significantly more training time in Colab, which made experimentation less practical.  
- The number of epochs was limited to **20** in this project for time efficiency. Running the model for more epochs would likely improve accuracy further.  

---

👤 Author: Hossein Khosravi
