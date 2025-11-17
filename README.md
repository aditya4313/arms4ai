# 👨‍💻 About Me

Hello! My name is **Roushan Kumar**, and I am a **4th-year student at Netaji Subhas University of Technology (NSUT), New Delhi**.  
I have a strong interest in **Image Processing, Machine Learning, and Deep Learning**, and I enjoy building models that solve real-world problems.

---

## 🛰️ Internship at ISRO – Space Applications Centre (SAC)

I completed my internship at **Space Applications Centre (ISRO)**, where I worked on **remote sensing image denoising and noise removal techniques**.  
My project involved enhancing satellite imagery using a two-stage deep learning framework with classical filtering and attention-based CNN models.

You can view the full project here:  
👉 **ISRO Internship Project Repository:**  
🔗 **https://github.com/aditya4313/isro_intern**

---

## 🤖 Currently Working at Jaipur Robotics

I am currently working at **Jaipur Robotics** as a **Machine Learning Intern**, where I focus on:

- Designing and training **segmentation models**  
- Building and fine-tuning **object detection models**  
- Customizing model architectures for real-world industrial applications  

Company Website:  
🔗 **[Jaipur Robotics](https://jaipurrobotics.com/)**

---

## 💡 Skills & Interests

- Image Processing  
- Deep Learning  
- Machine Learning  
- Computer Vision  
- Model Training & Fine-tuning  
- Applied AI in Remote Sensing and Robotics  

---
---

# 🗺️ Satellite Mosaic, Cloud Removal & Seamless Stitching

This project takes a folder full of **satellite image tiles** and converts them into **one clean, seamless, cloud-removed mosaic**.  
Everything is fully automated and easy to run.

---

## 🔧 What This Pipeline Uses

To build the final mosaic, the code uses:

- 🧭 **Rasterio** → reading tiles, writing the final mosaic, coordinate handling  
- 🗺️ **Reprojection** → placing each tile into the correct geographic location  
- ☁️ **Custom Cloud Masking** → detects bright white + blue-ish haze clouds  
- 🔍 **Pixel-based Cloud Removal** → keeps only the clean parts of each tile  
- 🔄 **Gaussian Blending** → smooths the borders where tiles overlap  
- 🎨 **Seam Weighting Logic** → decides which tile looks better in overlap regions  
- 🧮 **NumPy** → fast image & math operations  
- 🌫️ **Scipy (Gaussian Filter + Dilation)** → cloud smoothing + edge softening  
- 📦 **TQDM** → progress bar while processing tiles

---

## 🧠 How the Code Works (Simple English)

Even a beginner can understand the flow — it's like assembling a puzzle but smarter:

### 1️⃣ **All tiles are scanned**
The script reads all `.tif` tiles inside the folder and finds where each tile belongs on the big map.

### 2️⃣ **A big empty canvas is created**
One huge blank image (mosaic) is created with correct width, height & coordinates.

### 3️⃣ **Each tile is reprojected & aligned**
Using Rasterio + reprojection, every tile is:
- put at the correct real-world location  
- resized/interpolated if needed  
- matched to the global mosaic coordinate system  

### 4️⃣ **Clouds are detected automatically**
Using a custom cloud mask:
- very bright pixels (RGB > threshold)  
- bluish cloud patches  
- cloud outlines are expanded using dilation  
These pixels are removed or down-weighted.

### 5️⃣ **Good pixels from each tile are used**
Cloudy areas get ignored.  
Cleaner tile regions get higher priority.

### 6️⃣ **Overlapping tiles are blended**
Where tiles overlap:
- the script compares both tiles  
- checks which one looks cleaner  
- blends them smoothly using Gaussian weights  
This removes **hard seams**, **strips**, and **color jumps**.

### 7️⃣ **Final mosaic becomes clean, bright & seamless**
A single output file is created with:
✔ Cloud removed  
✔ Colors preserved  
✔ No visible seams  
✔ Smooth transitions  
✔ All tiles stitched perfectly  

---

## 🖼️ **Final Output (Preview)**

*(Your output mosaic image will be shown here)*

 
