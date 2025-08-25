# IMU-Vibration-Detection-Compensation-Project
This repository focuses on detecting and compensating for vibrations in non-ideal Inertial Measurement Unit (IMU) data. The study combines signal processing, machine learning, and deep learning techniques in MATLAB, inspired by the **MATLAB-Simulink Challenge Project Hub** (Project #231). 

For a detailed overview and references, please see the `Report/report.pdf` file.

## 👥 Contributors
- **Buket ÖZBAY** - ozbayb21@itu.edu.tr
- **Deniz ERDOĞAN** - erdogand21@itu.edu.tr

For any comments or recommendations, please contact us.

## ▶️ Order of Execution
To reproduce the study results, execute the following scripts in order:
1. `data_generation.m`
2. `kmeans_classification.m`
3. `vibration_comp_DL.m`

**Note:** The `moving_imu.m` file is for understanding IMU behavior in motion and is not required to run the main project.

---

## 🎯 Project Objective
Vibrations from engines or environmental factors can negatively affect accelerometer and gyroscope data, degrading a vehicle's navigation accuracy. This project aims to:
- Analyze vibration signals using **time and frequency domain techniques**.
- Generate **synthetic vibration data** for training machine learning models.
- Classify vibration data using **clustering algorithms**.
- Compensate for vibrations using a **deep learning-based denoising autoencoder**.

By improving the detection and compensation of vibrations, the study contributes to designing more reliable navigation systems.

---

## 🧠 Workflow
### 1. Dataset Examination and Vibration Analysis
The initial step involved analyzing the Kaggle dataset, `Accelerometer Data Set for Prediction of Motor Failure Time`, located in the `Dataset` folder.
- **Time-Domain Analysis:** Studied the behavior of acceleration signals over time.
- **Frequency-Domain Analysis:** Used **Fast Fourier Transform (FFT)** to identify key vibration characteristics:
  - **X-Axis:** Dominated by low frequencies; this axis was excluded from the vibration analysis.
  - **Y-Axis:** A significant peak around 15 Hz indicated a mechanical resonance or a primary vibration source.
  - **Z-Axis:** Moderate peaks in the 10–15 Hz range suggested medium-frequency vibrations.

### 2. Vibration Data Generation
Artificial vibration data was created using signal processing techniques. The generated signals exhibited high amplitudes at specific frequencies, closely matching the vibrations observed in the dataset.

### 3. Vibration Detection with K-Means Clustering
The **K-means algorithm**, an unsupervised machine learning technique, was employed to classify data into two clusters:
- **Vibrating**
- **Non-vibrating**
Clusters were determined based on RMS (Root Mean Square) values, providing a simple yet effective way to distinguish between these states.

### 4. Vibration Compensation Using a Denoising Autoencoder
A denoising autoencoder was implemented to reduce vibration effects in IMU data.
- **Input Data:**
  - **Clean data ($\chi$):** Original, vibration-free signals.
  - **Corrupted data ($\tilde{\chi}$):** Signals with added noise.
- **Model Architecture:**
  - **Encoder ($g_{\phi}$):** Compresses the input data to a lower-dimensional representation.
  - **Bottleneck ($z$):** Stores compressed features.
  - **Decoder ($f_{\theta}$):** Reconstructs the data to its original dimensions.
- **Output:** The reconstructed data ($\chi'$) approximates the clean data ($\chi$).

---

## 📈 Key Findings
- **Frequency Analysis:** FFT provided crucial insights for identifying vibration sources and system behavior.
- **Feature Extraction:** RMS and amplitude values effectively distinguished vibration states.
- **Classification:** K-means successfully categorized data into vibrating and non-vibrating clusters.
- **Vibration Compensation:** Deep learning techniques effectively removed vibration artifacts, improving data reliability.

---

## 🚀 Future Work
To enhance data generation, **Generative AI** techniques such as **GANs (Generative Adversarial Networks)** will replace signal processing methods. This approach will expand the dataset and improve model training, leading to more robust models.
