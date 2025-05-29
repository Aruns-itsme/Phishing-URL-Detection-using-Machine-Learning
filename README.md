# Phishing URL Detection using Machine Learning

This project identifies potentially malicious (phishing) URLs using machine learning techniques. Phishing is a common cyber threat where attackers trick users into sharing sensitive information via deceptive websites. Our model analyzes URLs based on 30+ features and predicts whether they are safe or phishing.

The system is built using **Flask** for the web interface, with **Gradient Boosting Classifier** as the core machine learning model trained on a Kaggle dataset. The project also includes feature extraction logic implemented in Python.

---

## Project Structure

```bash
Phishing-URL-Detection/
├── app.py # Flask web application script
├── feature.py # Feature extraction logic for URLs
├── phishing.csv # Dataset (Kaggle phishing URLs)
├── projectSample.ipynb # Jupyter Notebook (EDA and ML model training)
├── requirements.txt # Python dependencies
├── Procfile # Heroku deployment config
├── pickle/
│ └── model.pkl # Pre-trained ML model (Gradient Boosting)
├── static/
│ └── styles.css # Frontend CSS styling
├── templates/
│ └── index.html # HTML template for the web interface
├── .idea/ # PyCharm IDE configuration files
│ ├── .name
│ ├── encodings.xml
│ ├── misc.xml
│ ├── modules.xml
│ ├── Phishing-URL-Detection-master.iml
│ ├── workspace.xml
│ └── inspectionProfiles/
├── pycache/ # Python bytecode cache
│ ├── app.cpython-311.pyc
│ ├── feature.cpython-39.pyc
│ ├── feature.cpython-310.pyc
├── .DS_Store # macOS system file
└── README.md # Project documentation (this file)
```

---

## Web Application Workflow

1️⃣ **User inputs a URL** in the web interface  
2️⃣ Flask backend extracts features using `feature.py`  
3️⃣ The model (`model.pkl`) predicts if the URL is phishing or safe  
4️⃣ The result and confidence score are displayed on the web page  

---

## Features Extracted

| Feature Name        | Description                                                   |
|---------------------|---------------------------------------------------------------|
| UsingIP             | Checks if the URL uses an IP address instead of a domain name |
| LongURL             | Evaluates URL length; long URLs may hide malicious intent     |
| ShortURL            | Detects URL shorteners like bit.ly, goo.gl, etc.             |
| Symbol@             | Checks for '@' symbol, often used to redirect phishing URLs   |
| Redirecting//       | Detects '//' in abnormal positions                            |
| PrefixSuffix        | Identifies dashes '-' in the domain name                      |
| SubDomains          | Checks for multiple subdomains                                |
| HTTPS               | Verifies HTTPS usage                                          |
| DomainRegLen        | Domain registration length from WHOIS                         |
| Favicon             | Checks if favicon is loaded from a different domain           |
| ...                 | **Total 30+ features implemented** in `feature.py`            |

---

## Model & Evaluation

- **Algorithm Used:** Gradient Boosting Classifier (best accuracy)  
- **Other models tested:** Random Forest, KNN, Decision Tree, Logistic Regression  
- **Dataset:** [Kaggle Phishing Dataset](https://www.kaggle.com/code/eswarchandt/website-phishing/notebook) (11,000+ URLs)  
- **Metrics Evaluated:** Accuracy, Precision, Recall, F1-score

---

## Installation & Setup

1️. **Clone the Repository**

```bash
git clone https://github.com/yourusername/Phishing-URL-Detection.git
cd Phishing-URL-Detection
```
2️. Install Dependencies

```bash
pip install -r requirements.txt
```

3️. Run the Application

```bash
python app.py
```

4️. Access the Web App

```bash
http://127.0.0.1:5000/
```
## Tech Stack

- Frontend: HTML, CSS (in static/ and templates/)
- Backend: Flask (Python Web Framework)
- ML Model: Gradient Boosting Classifier (scikit-learn)
- Feature Engineering: BeautifulSoup, Requests, Whois, Regex, URL parsing
- Deployment: Procfile (Heroku ready)

## Requirements

All dependencies are listed in requirements.txt:

```bash
Flask==2.0.1
scikit_learn==1.0.2
beautifulsoup4==4.9.3
requests==2.25.1
whois==0.9.13
googlesearch_python==1.0.1
numpy==1.22.4
pandas==1.3.4
gunicorn==20.1.0
Werkzeug==2.2.2
```

## Acknowledgements

- Kaggle Dataset Contributors
- Scikit-learn, Flask, and Open-Source Python Libraries

## References

- [Kaggle Phishing Dataset](https://www.kaggle.com/code/eswarchandt/website-phishing/notebook)
- [Research Paper 1](https://www.sciencedirect.com/science/article/abs/pii/S0957417418306067)
- [Phishing Detection Techniques](https://towardsdatascience.com/phishing-domain-detection-with-ml-5be9c99293e5)
