# 🖊️ Secure Signature Verification Using Siamese Networks

This repository contains a **signature verification system** using a **Siamese ResNet-based neural network**. The system is trained to distinguish between genuine and forged signatures and can be used to authenticate handwritten signatures across multiple datasets.

---

## ⌚ Workflow

- Preprocessing the images: All signatures are converted to grayscale and resized to a uniform size for consistent input to the network.
- Creating signature pairs: Positive pairs (genuine-genuine) and negative pairs (genuine-forged) are generated to train the model.
- Training a Siamese network: Each branch of the Siamese network uses a ResNet18 backbone to extract embeddings from the signature images. The network learns to minimize the distance between embeddings of genuine pairs and maximize the distance for forged pairs using contrastive loss. 
- Threshold-based verification: During inference, the Euclidean distance between embeddings is compared to a threshold to classify whether a signature pair is genuine or forged.
- Integration: The trained model can be accessed via a Django REST Framework backend and interacted with using a Streamlit interface.

---

## 📂 Repository Structure

 
- **checkpoints/** - Saved intermediate training checkpoints. 
- **organized_data/** - Preprocessed datasets (GPDS and CEDAR) used for training and evaluation.  
- **image_pairs/** - Pickled positive and negative signature pairs for training/testing.  
- **notebooks/** - Jupyter notebooks for preprocessing, training, and evaluation. 
- **trained_model_parameters/** - Pretrained Siamese ResNet model weights.  
- **requirements.txt/** - Python dependencies required to run the project.

---

## 🛠️ Features

- Siamese network for signature verification using **ResNet18 embeddings**.  
- Handles both **GPDS** and **CEDAR** datasets.  
- Supports **fine-tuning and evaluation** of signature verification models.  

---

## ⚡ Getting Started

1. **Clone the repository**

```bash
git clone https://github.com/Siddarth021/secure-signature-verification.git
cd secure-signature-verification
````
2. **Create and activate a virtual environment**

```bash
python -m venv venv

▶ On Windows:

venv\Scripts\activate

▶ On macOS / Linux:

source venv/bin/activate
````

3. **Install dependencies**

```bash
pip install -r requirements.txt
````



4. **Train / Evaluate the Siamese network**

* Use the notebooks in the root directory for **image preprocessing**, **training**, and **testing**.
* Pretrained model weights are available in `trained_model_parameters/siamese_resnet_18.pth`.

---

## 📊 Results

* On the **GPDS dataset**, the model achieves \~**99.98% test accuracy**.
* On the **CEDAR dataset**, the model achieves \~**80.21% test accuracy** due to dataset differences.
* Distance threshold for classification is **0.4275** (can be tuned per dataset).

---

## 🧩 Future Improvements

* Fine-tuning on additional datasets (e.g., CEDAR) to improve accuracy
* Implementing data augmentation for enhanced generalization
* Addressing and mitigating current overfitting issues
* Incorporating Explainable AI techniques for model interpretability
* Replacing ResNet18 with a custom-designed backbone network

---
