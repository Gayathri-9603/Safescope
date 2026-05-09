# Safe Scope: An Intelligent Online Behaviour Tracker

Safe Scope is a professional-grade web application designed for parents to monitor their children's online activity in real time. It integrates a Django backend, a Chrome extension, and MongoDB to provide risk-aware browsing logs and intuitive dashboards.


## Key Features

* **Parental Authentication System**
  Register, log in, and manage multiple children under one account securely.

* **Multi-Child Management**
  Parents can monitor multiple children. Each child's browsing logs are shown separately.

* **Real-Time Browsing Activity Logging**
  Chrome extension captures website titles, URLs, timestamps, and risk scores.

* **Risk Prediction**

  * Uses LLMs to analyze browsing queries and website content.
  * Supports NSFW detection via Deep Learning Model in the form of ONNX.

* **Modern Dashboard**
  Professional-looking, responsive dashboard showing browsing history, safe/risky counts, and filtering options.

* **MongoDB Backend**
  Stores browsing logs, user accounts, and child information securely.

---

## 📁 Project Structure

```
safeweb/
├── chrome_extension/        ← Chrome extension files
├── data/                    ← (For static data files if required)
├── monitor/                 ← Django app (core logic and views)
│   ├── migrations/
│   ├── static/
│   ├── templates/
│   ├── utils/
│   │   ├── alert_engine.py
│   │   ├── data_preprocessor.py
│   │   ├── nsfw_detector.py
│   │   ├── predict_behaviour.py
│   │   └── query_analyzer.py
│   ├── admin.py
│   ├── apps.py
│   ├── forms.py
│   ├── models.py
│   ├── mongo_config.py
│   ├── tests.py
│   ├── urls.py
│   └── views.py
├── safeweb/                 ← Django project configuration
├── manage.py
```


### 2️⃣ Setup Python Environment

```bash
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3️⃣ MongoDB Setup

* Install and start MongoDB locally or use a cloud service.
* Update your MongoDB URI in:

  `monitor/mongo_config.py`

Example:

```python
MONGO_URI = "mongodb://localhost:27017/"
DB_NAME = "safewebguard_db"
```

### 4️⃣ Django Setup

```bash
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

### 5️⃣ Chrome Extension Setup

* Open `chrome://extensions/`
* Enable **Developer Mode**
* Click **Load Unpacked**
* Select the `chrome_extension/` folder
* Set child email through the extension popup

---

## 🔄 System Flow Diagram

```
Parent → Register → Login → Select Child → Dashboard
Child → Browsing Activity → Chrome Extension → Django Backend → MongoDB → Dashboard
```

---

## 🖥️ Usage Guide

* Visit: `http://127.0.0.1:8000/`
* Register as a parent.
* Add child emails.
* Install Chrome Extension on your child's device.
* Monitor browsing logs in real-time through the dashboard.

---

## 🔒 Important Notes

* All predictions rely on external APIs integrated in `monitor/utils/`.
* Ensure backend URL in the Chrome extension matches your Django server URL.
* Works with MongoDB only; no SQL databases configured.

---

## 📄 Screenshots
<img width="1919" height="1018" alt="Register - Page" src="https://github.com/user-attachments/assets/ed1a2dde-d2be-44cb-9bdb-e0fb281c4d34" />
<img width="1905" height="1028" alt="Login - Page" src="https://github.com/user-attachments/assets/5ed91d12-7c6d-4f7a-aab0-e53ce90a078f" />
<img width="1916" height="1010" alt="Select Child" src="https://github.com/user-attachments/assets/b8bbd5c8-d34d-4823-a9e9-117767589d41" />
<img width="616" height="474" alt="Chrome Extension" src="https://github.com/user-attachments/assets/a2c1c9ea-a06e-427e-b637-806e0339a8f6" />
<img width="1899" height="1018" alt="Dashboard - Content" src="https://github.com/user-attachments/assets/c8701568-4611-4c34-af0c-379f87ccde2d" />
<img width="1918" height="1000" alt="Dashboard of New User" src="https://github.com/user-attachments/assets/ab816eae-a8a9-4d10-af1f-dca16171f436" />
<img width="1479" height="726" alt="Parent Alert Through Gmail" src="https://github.com/user-attachments/assets/b022787a-2e69-4e59-b45e-62ec072607ba" />




