# ⚛️ Quantum Hackathon 2025 — Problem Statement 3  
### *Classical and Quantum-Hybrid Models for Image Generation*

---

## 🧠 Project Overview
This project focuses on comparing **classical deep learning** models with a **quantum–classical hybrid** approach for image generation using the MNIST dataset.  

The main goal was to explore how quantum circuits can be integrated into existing neural architectures and to analyze whether quantum embeddings can improve generative performance or training stability.

Three models were built and trained:
1. **Variational Autoencoder (VAE)** – learns compressed latent representations and reconstructs images.  
2. **Deep Convolutional GAN (DCGAN)** – a classical adversarial network that produces sharper digits.  
3. **Quantum-Classical GAN (qGAN)** – introduces a small 4-qubit **Parameterized Quantum Circuit (PQC)** inside the discriminator to extract quantum features.

---

## ⚙️ Implementation Summary

### 🔹 1. Variational Autoencoder (VAE)
- **Architecture:** Encoder → latent layer (μ, σ) → decoder  
- **Loss:** Reconstruction (MSE) + KL Divergence  
- **Output:** Smooth, slightly blurred digits  
- **Observation:** Very stable training with consistent loss reduction.

### 🔹 2. Deep Convolutional GAN (DCGAN)
- **Architecture:** Classical generator & discriminator using convolutional layers  
- **Loss:** Binary Cross Entropy (BCE)  
- **Output:** Sharper and more realistic digits  
- **Observation:** Generator and discriminator losses oscillate, as expected in adversarial setups.

### 🔹 3. Quantum-Classical Hybrid GAN (qGAN)
- **Concept:** Replace the first discriminator layer with a **4-qubit quantum circuit** simulated via PennyLane.  
- **Circuit Details:**  
  - Rotation encoding (RY gates) + CNOT entanglement  
  - Outputs 4 expectation values of Pauli-Z operators  
- **Training:** Integrated seamlessly with PyTorch using PennyLane’s `default.qubit` simulator.  
- **Observation:** Discriminator converged quickly; generator struggled to keep up, producing noisy images.  
  Still, the model successfully demonstrated hybrid quantum-classical co-training.

---

## 🧩 How the Project Works
1. **Dataset:** MNIST is automatically downloaded (no manual data upload).  
2. **Training:** Each model trains independently for 15–20 epochs.  
3. **Evaluation:**  
   - Visual inspection of generated samples  
   - Loss curve comparison for training stability  
4. **Results:**  
   - VAE → Stable but blurry outputs  
   - DCGAN → Sharp outputs, unstable training  
   - qGAN → Slower training, lower image quality, but verified working quantum integration.

---

## 🚀 How to Run

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/<your-username>/QuantumVision.git
cd QuantumVision

### 2️⃣ Install Dependencies
pip install torch torchvision matplotlib pennylane

### 3️⃣ Run Each Model
# Run the Variational Autoencoder
jupyter notebook VAE.ipynb

# Run the Classical GAN
jupyter notebook DCGAN.ipynb

# Run the Quantum–Classical GAN
jupyter notebook quantum.ipynb

