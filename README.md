# 🌿 Plant Disease Recognition & Recommendation System

A full-stack intelligent system that identifies plant diseases from images, offers treatment advice using Large Language Models (LLMs), provides real-time weather insights, and suggests nearby agro shops – all accessible through a sleek Streamlit web interface.

## 📦 Dataset Information

**Source**: [Kaggle - New Plant Diseases Dataset](https://www.kaggle.com/datasets/vipoooool/new-plant-diseases-dataset)

- **Classes**: 38 disease categories including healthy states
- **Images**: ~87,000 RGB images
- **Split**:
  - `train/`: 70,295 images
  - `validation/`: 17,572 images
  - `test/`: 33 images
- **Image Format**: JPEG
- **Structure**: Folder-per-class classification format

## ✨ Features

| Feature                        | Description                                                                 |
|-------------------------------|-----------------------------------------------------------------------------|
| 🖼 Image Classification        | Upload plant leaf image and detect disease via trained TensorFlow CNN       |
| 💊 LLM-based Cure Suggestion  | Query Groq’s LLaMA/Mixtral models for treatments                            |
| 🌦 Weather Monitoring         | Real-time weather conditions using OpenWeatherMap API                        |
| 🛒 Nearby Agro Shop Search    | Find vendors around a location using LLM text-based search                  |
| 🧑‍🎨 Multilingual UI          | English, Hindi, and Telugu language support                                 |
| ⚡ Streamlit Web Interface    | Clean, interactive UI for easy access and navigation                        |

## 📁 Directory Structure

├── new\.py                         
├── config.json                    
├── train\_code.ipynb              
├── test\_code.ipynb               
├── trained\_plant\_disease\_model.keras  
└── dataset/
├── train/
├── test/
└── validation/

## 🧪 Model Architecture (TensorFlow CNN)

- **Input Size**: (128x128x3)
- **Layers**:
  - Conv2D → ReLU → MaxPooling
  - Conv2D → ReLU → MaxPooling
  - Flatten → Dense → Dropout
  - Dense with Softmax (38 units)
- **Loss Function**: Categorical Crossentropy
- **Optimizer**: Adam
- **Metrics**: Accuracy

Train using:
jupyter notebook train_code.ipynb

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/plant-disease-detection.git
cd plant-disease-detection
```

### 2. Install Requirements

```bash
pip install -r requirements.txt
```

If `requirements.txt` is missing, use:

```bash
pip install streamlit tensorflow pillow requests groq notebook
```

### 3. Download & Organize Dataset

Download from [Kaggle](https://www.kaggle.com/datasets/vipoooool/new-plant-diseases-dataset) and place it like:

```
dataset/
  ├── train/
  ├── validation/
  └── test/
```

### 4. Add API Keys

Create `config.json`:

```json
{
  "GROQ_API_KEY": "your_groq_api_key"
}
```

Note: The Groq key is needed for treatment suggestions and nearby shop search.

---

## 🚀 Running the Application

```bash
streamlit run new.py
```

## 🧠 How It Works

### 📸 Disease Detection

* Upload a leaf image.
* TensorFlow CNN predicts disease class (out of 38).
* Outputs predicted label (e.g., `Tomato___Late_blight`).

### 🤖 LLM Suggestions

* LLaMA 3 via Groq suggests medicines & prices.
* Mixtral model finds nearby agro stores by location.

### 🌍 Weather Integration

* OpenWeatherMap API fetches temperature, humidity, condition.
* Threshold alerts for excessive temperature or moisture.

## 🌐 UI Pages

| Page                   | Functionality                                                       |
| ---------------------- | ------------------------------------------------------------------- |
| 🏠 Home                | Project introduction, walkthrough                                   |
| 📖 About               | Dataset info and stats                                              |
| 🧪 Disease Recognition | Image upload → disease prediction → treatment + shop recommendation |
| 🌦 Weather Monitoring  | Location-based weather metrics                                      |
| 🛒 Nearby Shops        | Manual search for vendors treating specific diseases                |


## 🔐 API Integration

### Groq API (LLM)

* **Used Models**:

  * `llama-3.3-70b-versatile`
  * `mixtral-8x7b-32768`
* **Features**:

  * Cure suggestions
  * Nearby agro vendor text search

### OpenWeatherMap

* Location-based weather forecast
* API Key required: [https://openweathermap.org/api](https://openweathermap.org/api)

## 🔥 Example Use Case

1. Upload a leaf with spots.
2. App detects: `Potato___Late_blight`.
3. LLM returns:

   * Suggested medicines with prices.
   * Nearby Hyderabad agro shops.
4. Weather shows:

   * 35°C, 80% humidity → high risk alert.

## 🚫 Limitations

* ⚠️ LLM output is text-based; shop data is not geocoded.
* 📡 Requires internet for API requests.
* 🧪 Model may overfit if dataset not balanced well.

## 👨‍💻 Author

* **Your Name**
* Email: [your.email@example.com](mailto:your.email@example.com)
* GitHub: [@yourusername](https://github.com/yourusername)

## 🔗 Related Links

* [Groq LLM API](https://console.groq.com/)
* [OpenWeatherMap](https://openweathermap.org/)
* [Kaggle Dataset](https://www.kaggle.com/datasets/vipoooool/new-plant-diseases-dataset)
