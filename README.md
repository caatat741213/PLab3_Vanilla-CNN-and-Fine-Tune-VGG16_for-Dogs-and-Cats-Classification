# Practical Lab 3 - Vanilla CNN and Fine-Tune VGG16 - for Dogs and Cats Classification

## 👨‍🎓 Author
* **Chao-Chung ,Liu** (Student ID: 9067679)

---

In this lab, we will work through a common practice of Deep Learning Engineers - that is - take an existing model, that does something similar to what the engineer is interested doing, and fine-tune it for the specific task at-hand.

## 📋 Project Description

This project compares two different approaches for image classification (Cats vs. Dogs):
1. **Vanilla CNN**: A custom neural network built from scratch.
2. **Transfer Learning (VGG16)**: Fine-tuning the pre-trained VGG16 model (Block 5) to achieve higher accuracy with limited data.

---

## 📊 Dataset Overview
* **Title:** Dogs vs. Cats (Kaggle Edition)
* **Source:** [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=54765)
* **Training Size**: 2,000 images
* **Validation Size**: 1,000 images
* **Test Size**: 2,000 images
* **Input Resolution**: 180x180 pixels.
* **Cleaning**: Corrupted images were automatically detected and removed during the loading process.

---

## 🚀 Experimental Results (Final Performance)

| Model | Test Accuracy | F1-Score (Avg) | Training Time |
| :--- | :--- | :--- | :--- |
| **Vanilla CNN** | **72.35%** | 0.72 | ~361 seconds |
| **VGG16 Fine-tuned** | **94.25%** | 0.94 | ~1500 seconds |

### Key Observations:
* **Vanilla CNN**: Experienced early overfitting. While fast to train, it struggled with complex backgrounds, leading to a higher error rate for cat images.
* **VGG16 (Strategy 3)**: Using a small learning rate ($1 \times 10^{-5}$) and a `ReduceLROnPlateau` scheduler allowed the model to reach high accuracy without the volatility seen in aggressive learning rates.

---

## 🧠 Key Insights
* VGG16 outperformed the custom CNN by over **20%**, proving that pre-trained features (textures, edges) are extremely valuable for small datasets.
* VGG16 took about **4 times longer** to train than the Vanilla CNN, but the massive jump in reliability makes it the superior choice for production.
* Most failures occurred in images with poor lighting or where the animal was partially hidden. Adding "Brightness Adjustment" in Data Augmentation could help in the future.

---

## 🛠️ How to Run
1. **Clone the Repo**:
   ```bash
   git clone <Your-Repository-URL>
    ```

2. Set up the Environment:
```bash
python -m venv venv
# Windows:
venv\Scripts\activate
# Mac/Linux:
source venv/bin/activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Dataset Preparation:
* Download the dataset[Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=54765)
* Unzip the file.
* Create the directory structure: data/kaggle_dogs_vs_cats/train.

5. Run the Notebook:

Open VanillaCNN_Fine_Tune_VGG16.ipynb in VS Code or Jupyter Notebook and run the cells sequentially.
