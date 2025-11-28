# 🌿 Eco-Friendly Shopping Assistant

## 📌 Project Overview

The **Eco-Friendly Shopping Assistant** is an AI-powered system that analyzes online product pages and determines whether a product is **Eco-Friendly, Moderate, or Not Eco-Friendly** based on its materials and specifications.
It aims to help users make more **sustainable and environmentally conscious shopping decisions**.

This project combines:

* ✅ Machine Learning (NLP + Classification)
* ✅ Flask REST API
* ✅ Chrome Extension (Real-time website analysis)
* ✅ Text Processing & Material Extraction
* ✅ Sustainable product awareness

---

## 🎯 Objectives

* Automatically analyze a product’s material composition
* Identify eco-friendly and non-eco-friendly materials
* Classify products into 3 categories:

  * **Eco-Friendly**
  * **Moderate**
  * **Not Eco-Friendly**
* Display the result as an interactive popup in the browser

---

## 🛠️ Tech Stack

### Backend (Machine Learning & API)

* Python
* Scikit-Learn
* LinearSVC (Support Vector Machine)
* TF-IDF Vectorizer (Word + Character level)
* Flask
* ngrok (for public tunnel)
* Joblib (model saving)

### Frontend (Chrome Extension)

* JavaScript
* HTML / CSS
* Chrome Extension API (Manifest V3)
* MutationObserver & DOM Parsing

---

## 📁 Project Structure

```
Eco-Friendly-Shopping-Assistant/
│
├── new.ipynb
├── eco_friendly_model_optimized.joblib
│
├── app.py
│
├── chrome_extension/
│   ├── manifest.json
│   ├── background.js
│   ├── content.js
│
├── flipkart_products_with_fixed_labels.csv
│
└── README.md
```

---

## 🔍 How the System Works

### Step 1: Data Preparation

* Product Name
* Brand
* Specification

These fields are cleaned using regex and combined into one text field.

### Step 2: Feature Extraction

Two types of TF-IDF features are used:

* **Word-level TF-IDF** (1-2 grams)
* **Character-level TF-IDF** (3-5 grams)

These features are combined using `FeatureUnion`.

---

### Step 3: Model Training

The following algorithm is used:

```
LinearSVC(class_weight='balanced')
```

With hyperparameter tuning using:

```
GridSearchCV()
```

Labels:

* 0 → Not Eco-Friendly
* 1 → Moderate
* 2 → Eco-Friendly

The trained model is saved as:

```
eco_friendly_model_optimized.joblib
```

---

### Step 4: Flask API

A local Flask API is created with:

* `/health` – To check status
* `/predict` – To get classification

Example:

```json
POST /predict
{
  "text": "Bamboo toothbrush biodegradable"
}
```

Response:

```json
{
  "label": "Eco-Friendly",
  "confidence": 98.21
}
```

ngrok is used to expose the local server:

```
http://localhost:5001 → https://xxxxx.ngrok-free.dev
```

---

### Step 5: Chrome Extension

The extension:

1. Runs on e-commerce sites (Amazon, Flipkart, Myntra)
2. Extracts materials and product details
3. Sends text to Flask API
4. Displays popup showing:

   * Eco status
   * Materials found
   * Harmful materials
   * Certification tags

Popup Example:

✅ Eco-Friendly
🌿 Materials: Bamboo, Organic Cotton
⚠️ Harmful: Plastic

---

## 📊 Model Performance

### Training Accuracy:

```
99.93 %
```

### Metrics Used:

* Accuracy
* Precision
* Recall
* F1-Score
* Confusion Matrix

The model achieved near-perfect results on training data and performed strongly on unseen test data as well.

---

## 🚀 How to Run This Project

### 1️⃣ Train the Model

```bash
python model_training.py
```

This will create:

```
eco_friendly_model_optimized.joblib
```

---

### 2️⃣ Run Flask Server

```bash
python app.py
```

This runs on:

```
http://localhost:5001
```

Use ngrok:

```bash
ngrok http 5001
```

---

### 3️⃣ Load Chrome Extension

1. Go to: `chrome://extensions/`
2. Turn ON **Developer Mode**
3. Click **Load Unpacked**
4. Select `chrome_extension/` folder

Now visit:

* Amazon
* Flipkart
* Myntra

Popup will appear automatically.

---

## 💡 Key Features

* Real-time eco-classification
* Smart material detection
* Fast NLP processing
* Lightweight Chrome extension
* Sustainable consumer awareness

---

## 🔮 Future Enhancements

* Deploy on AWS/Heroku/Vercel
* Mobile application
* Carbon footprint estimation
* Green product recommendations
* Multilingual support

---

## 👩‍🎓 Developed By

**Pooja B,**
**Poornima,**
**Prathika**

3rd Year – Computer Science and Engineering

M S Ramaiah Institute of Technology,Bengaluru

Eco-Friendly AI Project

---

## ✅ License

This project is purely for educational and research purposes.


