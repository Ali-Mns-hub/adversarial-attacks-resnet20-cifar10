# Adversarial Defense on ResNet-20

This repository contains the implementation for the second part of the "Trustworthy AI" project. In this section, we tackle the challenge of adversarial vulnerability by employing various defense mechanisms to improve a pre-trained ResNet-20 model's performance on CIFAR-10 against FGSM and PGD attacks.

## Project Objectives
- Evaluate simple defenses using Data Augmentation (color jitter, rotation, noise).
- Implement Adversarial Training by fine-tuning the model on FGSM-perturbed data (50% adversarial fraction).
- Investigate Contrastive Learning using Circle Loss to optimize pair similarity.
- Build and evaluate a Defense-VAE (Autoencoder) to reconstruct perturbed inputs and filter adversarial noise.

## Dataset
This project uses the **CIFAR-10** dataset. For detailed information on how to set up the data, please refer to the `data/README.md` file.

## Key Results
The implementation of different defense strategies significantly improved the model's robustness against multi-step attacks like PGD ($\epsilon=0.03$, $\alpha=0.005$, steps=40).

- **Accuracy under PGD attack (Data Augmentation):** 28.12%
- **Accuracy under PGD attack (Adversarial Training):** 50.37%
- **Accuracy under PGD attack (Defense-VAE with Fine-tuning):** 48.80%

### Visualizing Feature Robustness (UMAP)
The t-SNE / UMAP plots below illustrate the penultimate-layer feature spaces. Standard training collapses class boundaries under PGD attacks, whereas Adversarial Training and Defense-VAE maintain tight, distinct class clusters even after adversarial perturbations.

**Adversarial Training UMAP:**
![UMAP Adversarial Training](assets/umap_adv_training.png)

**Defense-VAE UMAP:**
![UMAP Defense VAE](assets/umap_defense_vae.png)

### Training Stability
The cross-entropy loss consistently decreased during Adversarial Training, ensuring model convergence while incorporating 50% adversarial examples in each batch.

![Adversarial Training Loss](assets/adversarial_training_loss.png)

## Repository Structure
```text
.
├── assets/                     # UMAP plots, charts, and output samples
├── data/                       # CIFAR-10 dataset directory
│   └── README.md               # Dataset documentation
├── notebooks/
│   └── Q2_Adversarial_Defense.ipynb  # Main Jupyter notebook
├── Autoencoder_model.py        # VAE/Autoencoder architecture script
├── README.md                   # This file
└── requirements.txt            # Python dependencies
