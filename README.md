# 🚀 AI Resume Intelligence & Job Matcher

🚀 A smart Flask application that parses resumes, 📄 calculates an **ATS (Applicant Tracking System) Score**, and fetches **real-time job listings** relevant to your skills using the Adzuna API.

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![Flask](https://img.shields.io/badge/Flask-Web_Framework-green?style=for-the-badge&logo=flask)
![Bootstrap](https://img.shields.io/badge/Bootstrap-UI-purple?style=for-the-badge&logo=bootstrap)

## ✨ Key Features

* **📄 AI Resume Parsing:** Extracts text and skills from PDF resumes automatically.
* **📊 ATS Scoring System:** Analyzes resume length, keyword density, and essential sections to give a score (0-100) with actionable feedback.
* **🧠 Intelligent Matching:** Uses NLP (Natural Language Processing) to identify skills and match them with live market data.
* **🌍 Real-Time Job Search:** Fetches live job openings via the Adzuna API based on detected skills.
* **🖱️ Interactive Dashboard:**
    * **Clickable Skills:** Filter jobs instantly by clicking on detected skill tags.
    * **Sticky Sidebar:** Profile details stay visible while scrolling through jobs.
    * **Session Memory:** Remembers your location and filter preferences.

---

## 📂 Project Structure

Here is an explanation of the core files in this repository:

| File / Folder | Description |
| :--- | :--- |
| **`app.py`** | The main Flask application. Handles routes (`/`, `/process`, `/search`), session management, and ties the logic together. |
| **`job_engine/`** | Contains the "Brain" of the application. |
| ├── `matcher.py` | Logic for skill extraction, calculating ATS scores, and parsing resume text. |
| ├── `job_api.py` | Connects to the **Adzuna API** to fetch live job listings. |
| ├── `skills.py` | A database list of technical skills used for matching. |
| **`resume_parser/`** | Handles file processing. |
| ├── `extract_text.py` | Extracts raw text from PDF files using libraries like `pdfminer`. |
| **`templates/`** | HTML frontend files. |
| ├── `index.html` | The upload page with filter options (City, Remote, etc.). |
| ├── `results.html` | The main dashboard displaying the ATS score, Skills Cloud, and Job Cards. |
| **`requirements.txt`** | List of Python dependencies required to run the app. |
| **`Procfile`** | Configuration file for deployment on Render. |

---

## 🛠️ Installation & Local Setup

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/YOUR_USERNAME/ai-resume-matcher.git](https://github.com/YOUR_USERNAME/ai-resume-matcher.git)
    cd ai-resume-matcher
    ```

2.  **Create a Virtual Environment:**
    ```bash
    python -m venv .venv
    # Windows
    .venv\Scripts\activate
    # Mac/Linux
    source .venv/bin/activate
    ```

3.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Download NLP Model:**
    This app uses Spacy's English model.
    ```bash
    python -m spacy download en_core_web_sm
    ```

5.  **Configure API Keys:**
    Open `job_engine/job_api.py` and replace the placeholders with your actual Adzuna credentials:
    ```python
    ADZUNA_APP_ID = "YOUR_ID"
    ADZUNA_APP_KEY = "YOUR_KEY"
    ```

6.  **Run the App:**
    ```bash
    python app.py
    ```
    Visit `http://127.0.0.1:5000` in your browser.

---

## 🚀 Deployment (Render)

This app is ready for deployment on **Render.com**.

1.  Create a new **Web Service** on Render.
2.  Connect this repository.
3.  Use the following settings:
    * **Runtime:** Python 3
    * **Build Command:** `pip install -r requirements.txt && python -m spacy download en_core_web_sm`
    * **Start Command:** `gunicorn app:app`

---

## 🛡️ License

This project is open-source and available for educational purposes.
