
# 🔍 Scratch Detection using Deep Learning and Computer Vision

This project detects whether an image of printed text is "good" (clear) or "bad" (scratched), using deep learning classification and image processing techniques. It also includes scratch localization using bounding boxes and masks.

---

## 📂 Repository Structure

```
project-root/
├── good/                     # Folder containing good images
├── bad/                      # Folder containing bad images (scratched text)
├── masks/                    # (Optional) Binary masks for bad images
├── augmented_bad/            # Simulated bad images from good ones
├── augmented_masks/          # Simulated scratch masks
├── Boundingbox&Mask.ipynb    # Notebook for drawing bounding boxes & masks
├── mowito.ipynb              # Notebook for training 5 deep learning models
```

---

## 🧾 Dataset

- ~5000 labeled images (good/bad)
- Optional `masks/` folder with binary annotations of scratches (255 = scratch)
- All images are resized to `(224, 224)` for training

---

## 📦 Required Libraries

Install dependencies using pip:

```bash
pip install tensorflow opencv-python matplotlib numpy
```

If using Google Colab:

```python
!pip install tensorflow opencv-python matplotlib numpy
```

---

## 🚀 How to Run

### 1️⃣ Step 1: Setup Your Data

Unzip or place your dataset in the structure:

```
.
├── good/
│   ├── img1.jpg
│   ├── ...
├── bad/
│   ├── img1.jpg
│   ├── ...
├── masks/
│   ├── img1.jpg   # Binary mask for each bad image
```

Or use `augmented_bad/` and `augmented_masks/` to simulate data.

---

### 2️⃣ Step 2: Train and Compare Deep Learning Models

Open: `mowito.ipynb`

This notebook trains and compares **5 deep learning models**:

| Model        | Method              |
|--------------|---------------------|
| Custom CNN   | Sequential from scratch |
| MobileNetV2  | Transfer Learning     |
| ResNet50     | Transfer Learning     |
| VGG16        | Transfer Learning     |
| InceptionV3  | Transfer Learning     |

#### ✅ What it does:
- Loads images using `ImageDataGenerator`
- Splits into training and validation sets
- Trains each model
- Saves training history
- Plots **accuracy and loss** graphs for each model

---

### 3️⃣ Step 3: Visualize Masks and Bounding Boxes

Open: `Boundingbox&Mask.ipynb`

This notebook:

- Loads images and binary masks
- Applies `cv2.findContours` on each mask
- Draws bounding boxes around scratch areas
- Plots the original image, mask, and box overlay side-by-side

---

## 📊 Example Visual Output

| Image Type   | Visualization        |
|--------------|----------------------|
| Good Image   | Clear image, no box  |
| Bad Image    | Scratch highlighted with green box & white mask |
| Simulated Bad | Artificial scratch drawn + mask |

---

## 💡 Bonus Features

- Automatically skip good images with empty masks
- Simulate scratch data using line overlays
- Allows you to plug into object detection models like YOLO or U-Net

---

## 🛠️ Tips

- You can control which models to run by modifying the model list
- Use mask thresholding or morphological ops to improve detection
- Try `cv2.addWeighted()` for overlaying mask on the image

---

## 📬 Author

**Nandha Kumar Vijayan**  
_Email_: nandhv6@gmail.com 
_Project developed for interview-ready, scratch classification and detection task_

---

## 📘 Suggested Extensions

- Real-time scratch detection using YOLOv8
- Fine-grained scratch severity classification
- Custom GUI with threshold slider
- Convert bounding box coordinates to COCO/YOLO format
