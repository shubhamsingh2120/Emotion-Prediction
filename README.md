# 🧠 Emotion Detection using BiGRU & FastAPI

An end-to-end **Deep Learning-based Emotion Detection application** that analyzes user-provided text and predicts the underlying emotion using a **Bidirectional GRU (BiGRU)** neural network.

The trained model is integrated with a **FastAPI backend** that provides real-time emotion predictions along with confidence scores and probability distributions for all supported emotions.

## 🚀 Project Overview

This project takes a text sentence as input, preprocesses it, converts the text into numerical sequences using a trained tokenizer, and passes the padded sequence to a trained BiGRU model.

The application predicts one of six emotions:

* 😢 Sadness
* 😄 Joy
* ❤️ Love
* 😠 Anger
* 😨 Fear
* 😲 Surprise

The emotion labels and corresponding emojis are defined in the application configuration.

## ✨ Features

* Text-based emotion classification
* BiGRU deep learning model
* Text preprocessing and cleaning
* Tokenization
* Sequence padding
* Six emotion classes
* Prediction confidence score
* Probability distribution for all emotions
* FastAPI REST API
* API health-check endpoint
* Web-based frontend
* CORS support
* Model and tokenizer loaded during application startup

## 🧠 Machine Learning Model

The project uses a **Bidirectional GRU (BiGRU)** neural network for text classification.

The trained model is stored as:

```text
Artifacts/BiGRU_Model.keras
```

The tokenizer used to convert text into numerical sequences is stored as:

```text
Artifacts/tokenizer.pkl
```

The application uses a maximum sequence length of **50 tokens**.

## 🔄 Text Processing Pipeline

The input text goes through the following preprocessing steps:

```text
User Input
    ↓
Convert to Lowercase
    ↓
Remove Apostrophes
    ↓
Remove Special Characters & Punctuation
    ↓
Remove Extra Spaces
    ↓
Tokenization
    ↓
Sequence Padding
    ↓
BiGRU Model
    ↓
Emotion Probabilities
    ↓
Predicted Emotion
```

The preprocessing function converts text to lowercase, removes apostrophes and non-alphanumeric characters, and normalizes extra spaces.

## 📊 Supported Emotions

| Emotion  | Emoji |
| -------- | ----- |
| Sadness  | 😢    |
| Joy      | 😄    |
| Love     | ❤️    |
| Anger    | 😠    |
| Fear     | 😨    |
| Surprise | 😲    |

## 🌐 FastAPI Backend

The application is built using **FastAPI**.

### API Endpoints

#### `GET /`

Serves the application's web interface.

#### `GET /health`

Checks whether the API server is running and whether the model and tokenizer have been loaded successfully.

#### `POST /predict`

Accepts a text sentence and returns the predicted emotion, confidence score, and probabilities for all emotion classes.

### Example Request

```json
{
  "text": "I feel so happy and excited"
}
```

### Example Response

```json
{
  "text": "I feel so happy and excited",
  "predicted_emotion": "joy",
  "confidence": 0.94,
  "all_probabilites": {
    "sadness": 0.01,
    "joy": 0.94,
    "love": 0.02,
    "anger": 0.01,
    "fear": 0.01,
    "surprise": 0.01
  }
}
```

The API response schema contains the original text, predicted emotion, confidence, and probability distribution.

## 🔐 Input Validation

The API validates incoming text using Pydantic.

The input:

* Must contain at least 1 character
* Can contain a maximum of 2000 characters
* Is validated before being processed by the model

An example sentence is also provided in the API schema.

## ⚙️ Model Loading

The BiGRU model and tokenizer are loaded once when the FastAPI application starts.

```text
BiGRU_Model.keras
        +
tokenizer.pkl
        ↓
FastAPI Startup
        ↓
Loaded into Memory
        ↓
Ready for Prediction
```

When the server shuts down, the loaded objects are cleared from memory.

## 🛠️ Technologies Used

* Python
* TensorFlow
* Keras
* NumPy
* FastAPI
* Pydantic
* Uvicorn
* BiGRU
* REST API
* HTML/CSS/JavaScript

The project uses TensorFlow CPU 2.17.0, NumPy 1.26.4, FastAPI 0.115.0, Uvicorn 0.30.6, Pydantic 2.9.2, and h5py 3.11.0.

## 📁 Project Structure

```text
Emotion-Detection/
│
├── Artifacts/
│   ├── BiGRU_Model.keras
│   └── tokenizer.pkl
│
├── static/
│   └── index.html
│
├── final_clean.ipynb
├── main.py
├── requirements.txt
├── runtime.txt
└── README.md
```

## ▶️ Run Locally

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/emotion-detection.git
cd emotion-detection
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

### 3. Activate the Environment

**Windows:**

```bash
venv\Scripts\activate
```

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

### 5. Start the FastAPI Server

```bash
uvicorn main:app --reload
```

The application will start locally and can be accessed through the FastAPI server.

## 📌 API Workflow

```text
Client
  │
  │ POST /predict
  ▼
FastAPI
  │
  ▼
Text Preprocessing
  │
  ▼
Tokenizer
  │
  ▼
Sequence Padding
  │
  ▼
BiGRU Model
  │
  ▼
Emotion Probabilities
  │
  ▼
Predicted Emotion + Confidence
```

## 🔍 Example Use Cases

This project can be used as a foundation for:

* Customer feedback analysis
* Social media sentiment/emotion analysis
* Chatbot emotion detection
* User feedback classification
* Text-based emotional analytics
* Customer support analytics
* Educational NLP applications

## 🔮 Future Improvements

Potential improvements include:

* Adding more emotion categories
* Improving model accuracy with additional training data
* Adding multilingual emotion detection
* Adding model performance metrics to the web interface
* Adding prediction history
* Adding batch text prediction
* Adding authentication and API security
* Adding Docker deployment
* Adding automated model monitoring

## ⚠️ Disclaimer

This project is intended for **educational and demonstration purposes**. Emotion predictions are model-generated classifications and should not be treated as definitive assessments of a person's actual emotional state.

## 👨‍💻 Author

**Shubham Singh**

B.Tech – Information Technology

Interested in **Data Science, Machine Learning, Deep Learning, Python, NLP, and AI**.
