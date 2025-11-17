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
---

# 🟢 OUTPUT — Cloudless Mosaic

The final processed mosaic, after applying cloud removal, tile alignment, and seam blending, is available for download below:

👉 [**Download Cloudless Mosaic (Google Drive)**](https://drive.google.com/file/d/1S-ZwtwZr8tKzcwfpcDIdrDYdXxhBHfni/view?usp=sharing)

---

---

# 🗺️ Satellite Mosaic, Cloud Removal & Seamless Stitching Pipeline

This project implements a complete end-to-end workflow for generating a **high-quality, cloud-reduced, and seamless satellite mosaic** from multiple input tiles.  
The pipeline integrates reprojection, cloud detection, mask refinement, overlap handling, and seam blending to ensure a clean and visually consistent output.

---

## 🔧 Components Used in the Pipeline

This system relies on a combination of geospatial and image-processing libraries:

- **Rasterio** – Handles reading tiles, writing the output mosaic, coordinate systems, and geospatial transforms.  
- **Reprojection (rasterio.warp)** – Ensures each tile is accurately placed on the global canvas.  
- **NumPy** – Performs fast numerical operations on image arrays.  
- **SciPy (Gaussian Filter & Binary Dilation)** – Used for cloud mask smoothing and removing cloud edges.  
- **Gaussian Weighting** – Produces smooth transitions in overlapping regions.  
- **TQDM** – Displays progress while processing large datasets.  
- **Matplotlib** – Generates a preview of the final mosaic.

---

# 🧠 How the Pipeline Works 

The pipeline is divided into multiple functional stages.  
Each stage plays a specific role in producing a clean mosaic.

---

## **1️⃣ Tile Collection & Spatial Canvas Construction**  
The pipeline begins by scanning the folder for all `.tif` satellite tiles.  
For these tiles:

- Their **geographical bounds** are extracted.
- A **global bounding box** is computed to determine the extent of the final mosaic.
- Using this extent, a **blank canvas** of the appropriate resolution, height, width, and CRS is created.

**Purpose:**  
To ensure all tiles fit accurately onto one unified global coordinate system.

---

## **2️⃣ Tile Reprojection & Spatial Alignment**  
Each tile is then:

- Reprojected into the output coordinate reference system.  
- Resampled using bilinear interpolation for smooth positioning.  
- Placed precisely at the correct pixel location on the mosaic using spatial window calculations.

**Purpose:**  
To ensure every tile aligns perfectly, even if tiles originate from different projections or coordinate systems.

---

## **3️⃣ Cloud Detection & Mask Generation**  
A dedicated cloud-masking function is applied to every tile. It identifies:

- Very bright white areas  
- Blue-white atmospheric haze  
- High-intensity pixel clusters  

After initial detection, **binary dilation** is applied to expand cloud regions and eliminate residual edges.

A **Gaussian filter** then smooths the mask so transitions are not harsh.

**Purpose:**  
To remove clouds effectively while preventing hard edges or leftover cloud fragments.

---

## **4️⃣ Selecting Usable (Cloud-Free) Pixels**  
Using the cloud mask:

- Clouded pixels receive **low weight** or are discarded entirely.  
- Cloud-free pixels receive **high priority**.  
- Tiles containing too few valid pixels are automatically skipped.

**Purpose:**  
To ensure only clean and reliable pixel values contribute to the final mosaic.

---

## **5️⃣ Overlap Detection & Decision Logic**  
When a new tile overlaps with regions already written to the mosaic:

- The existing and incoming pixel values are compared.  
- If the overlap is small, the new tile is simply merged.  
- If the overlap is significant, the values are blended intelligently.

**Purpose:**  
To maintain consistency and avoid abrupt boundaries between tiles.

---

## **6️⃣ Seam Blending Using Gaussian Weighting**  
For overlapping regions, the algorithm:

- Computes the squared difference between the two pixel sets.  
- Smooths these differences using a Gaussian filter.  
- Normalizes them to create a **difference-based weight map**.  
- Applies an exponential function to assign higher weight to cleaner pixels.  
- Blends the tiles accordingly.

**Purpose:**  
To remove visible seams, adjust for brightness mismatches, and produce a uniform mosaic without tile edges.

---

## **7️⃣ Mosaic Writing & Final Preview Generation**  
The blended result is written back into the mosaic canvas.  
Once all tiles are processed:

- A low-resolution preview of the final mosaic is generated.  
- Colors are preserved, clouds are reduced, and seams are minimized.

**Purpose:**  
To confirm visually that the mosaic is seamless, clean, and cloud-corrected.

---

# 🖼️ Final Output Preview

<img width="971" height="923" alt="Screenshot 2025-11-18 at 12 52 21 AM" src="https://github.com/user-attachments/assets/bf6e654e-8b84-4bba-9de4-0a347c656b00" />

