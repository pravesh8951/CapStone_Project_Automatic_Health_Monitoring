# 🏥 AI-Powered Automated Health Monitoring System (AHMS)

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-2.0+-green.svg)](https://flask.palletsprojects.com/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0+-orange.svg)](https://www.mysql.com/)
[![License](https://img.shields.io/badge/License-Academic-red.svg)](#license)

A comprehensive healthcare intelligence platform that bridges the gap between medical data, patients, and doctors through intelligent automation and secure data management.

**Capstone Project by:** Pravesh Dubey, Siddharth N. Allagi, Veeresh Pattar  
**Guided by:** Dr. Afroz Pasha, Department of Information Science, Presidency University, Bangalore

---

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [System Architecture](#system-architecture)
- [Tech Stack](#tech-stack)
- [Installation](#installation)
- [Usage Guide](#usage-guide)
- [Project Structure](#project-structure)
- [Testing & Results](#testing--results)
- [Future Enhancements](#future-enhancements)
- [Contributors](#contributors)
- [License](#license)

---

## 🎯 Project Overview

The **AI-Powered Automated Health Monitoring System (AHMS)** automates the extraction, analysis, and summarization of medical reports while providing a secure patient-doctor collaboration portal. The system leverages cutting-edge AI technologies including OCR, NLP, and CNN models to streamline healthcare workflows and improve accessibility.

**Problem Statement:** Medical professionals spend significant time manually reviewing documents and generating reports. This project aims to reduce this burden through intelligent automation while maintaining HIPAA-compliant data security.

---

## ✨ Key Features

### 🧾 OCR-Based Medical Report Extraction
- Extracts text from PDFs, scanned reports, and images
- Preprocesses noisy and low-resolution documents using Tesseract-OCR
- Achieves **90.7% accuracy** on clinical documents

### 🧠 AI-Generated Medical Summaries
- Automatically generates clinical summaries from extracted text
- Identifies symptoms, test results, abnormalities, and recommendations
- Powered by Gemini 2.5 Flash LLM
- Average processing time: **< 8 seconds per report**

### 🩻 CNN-Based Medical Image Analysis
- Detects abnormalities in X-rays and scans (infections, opacity, structural issues)
- Provides confidence scores with clinical interpretations
- Model accuracy: **82%** on test dataset

### 👥 Dual-Access Patient & Doctor Portal
- **Patient Features:** Email/mobile + DOB authentication, multi-profile family mode
- **Doctor Features:** Email/phone/password login, patient record access, report uploads
- Secure role-based access control

### 📅 Intelligent Appointment Booking System
- Schedule in-person appointments with hospitals and doctors
- Automated email confirmations
- 24-hour reminder notifications via APScheduler

### 📂 Electronic Medical Records (EMR)
- Securely store, upload, and categorize medical documents
- Bi-directional sync: doctor-uploaded records appear on patient dashboard
- Encrypted storage and access logging

### 🆘 Emergency Assistance Module
- AI-powered first-aid guidance
- One-click ambulance request with GPS-based location detection
- Integration with geolocation APIs for rapid response

### 🏋️ AI-Powered Exercise Plan Generator
- Generates personalized exercise recommendations based on medical history
- Creates AI-generated illustrations using DALL-E 3
- Customizable difficulty levels

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────┐
│           Frontend Layer                 │
│  HTML5 • CSS3 • JavaScript • Bootstrap  │
└────────────────┬────────────────────────┘
                 │ AJAX/REST API
┌────────────────▼────────────────────────┐
│         Backend Application              │
│  Flask (Python) • RESTful API            │
│  • OCR Pipeline                          │
│  • NLP Processing                        │
│  • CNN Inference                         │
│  • Appointment Management                │
│  • EMR Operations                        │
└────────────────┬────────────────────────┘
                 │
┌────────────────▼────────────────────────┐
│        Data Layer (MySQL)                │
│  • User Accounts                         │
│  • Medical Documents                     │
│  • Appointment Records                   │
│  • EMR Storage                           │
│  • Activity Logs                         │
└────────────────┬────────────────────────┘
                 │
┌────────────────▼────────────────────────┐
│   External Services & AI Models          │
│  • Tesseract OCR                         │
│  • Google Gemini API                     │
│  • DALL-E 3 Image Generation             │
│  • Geolocation Services                  │
│  • Email (SMTP)                          │
└─────────────────────────────────────────┘
```

---

## 🛠️ Tech Stack

### Backend
- **Framework:** Python Flask
- **ORM:** SQLAlchemy
- **OCR:** Pytesseract (Tesseract Engine)
- **NLP:** Google Gemini 2.5 Flash
- **Image Processing:** Pillow, PyMuPDF
- **Task Scheduling:** APScheduler
- **Email:** Flask-Mail with SMTP

### Frontend
- **Markup:** HTML5
- **Styling:** CSS3, Bootstrap 4/5
- **Scripting:** Vanilla JavaScript, AJAX
- **UI Components:** Bootstrap Grid & Components

### Database
- **RDBMS:** MySQL 8.0+
- **Driver:** PyMySQL
- **Connection Pooling:** SQLAlchemy

### AI/ML Models
- **Medical Image Classification:** CNN (TensorFlow/Keras)
- **Text Summarization:** Gemini 2.5 Flash API
- **Image Generation:** DALL-E 3 API
- **Computer Vision:** OpenCV

### DevOps & Tools
- **Version Control:** Git
- **Testing:** Locust, Postman
- **Environment:** Virtual Environment (venv)

---

## 📂 Project Structure

```
ahms/
├── app.py                          # Main Flask application
├── requirements.txt                # Python dependencies
├── .env.example                    # Environment variables template
├── config.py                       # Configuration settings
│
├── models/
│   ├── __init__.py
│   ├── user.py                    # User model (Patient/Doctor)
│   ├── document.py                # Medical document model
│   ├── appointment.py             # Appointment model
│   ├── emr.py                     # Electronic medical records
│   └── cnn_model.py               # CNN model for X-ray analysis
│
├── routes/
│   ├── __init__.py
│   ├── auth.py                    # Authentication routes
│   ├── patient.py                 # Patient portal routes
│   ├── doctor.py                  # Doctor portal routes
│   ├── ocr.py                     # OCR processing routes
│   ├── nlp.py                     # NLP summary generation
│   ├── appointments.py            # Appointment management
│   ├── emergency.py               # Emergency assistance routes
│   └── admin.py                   # Admin dashboard
│
├── utils/
│   ├── ocr_processor.py           # OCR pipeline
│   ├── nlp_processor.py           # NLP processing
│   ├── image_analyzer.py          # CNN inference
│   ├── email_service.py           # Email operations
│   ├── validators.py              # Input validation
│   └── decorators.py              # Authentication decorators
│
├── static/
│   ├── css/
│   │   ├── style.css
│   │   └── bootstrap.min.css
│   ├── js/
│   │   ├── main.js
│   │   ├── dashboard.js
│   │   └── upload.js
│   ├── images/
│   └── exercises/                 # Exercise illustrations
│
├── templates/
│   ├── base.html
│   ├── index.html                 # Home page
│   ├── auth/
│   │   ├── login.html
│   │   └── register.html
│   ├── patient/
│   │   ├── dashboard.html
│   │   ├── upload_document.html
│   │   ├── medical_history.html
│   │   └── appointments.html
│   ├── doctor/
│   │   ├── dashboard.html
│   │   ├── patient_list.html
│   │   └── upload_report.html
│   ├── emergency/
│   │   └── first_aid_guide.html
│   └── exercises/
│       └── exercise_plan.html
│
├── uploads/                        # User-uploaded documents
│   ├── documents/
│   └── xrays/
│
├── tests/
│   ├── test_ocr.py
│   ├── test_nlp.py
│   ├── test_api.py
│   └── test_models.py
│
└── README.md
```

---

## 🚀 Installation

### Prerequisites
- Python 3.8 or higher
- MySQL 8.0 or higher
- Git
- pip (Python package manager)

### Step 1: Clone the Repository

```bash
git clone https://github.com/your-username/ahms.git
cd ahms
```

### Step 2: Create Virtual Environment

```bash
python -m venv venv

# Activate virtual environment
# On macOS/Linux:
source venv/bin/activate

# On Windows:
venv\Scripts\activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Configure Environment Variables

Create a `.env` file in the root directory:

```env
# Flask Configuration
FLASK_APP=app.py
FLASK_ENV=development
SECRET_KEY=your-secret-key-here

# Database
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your-password
DB_NAME=ahms_db

# Email Configuration (Gmail)
MAIL_SERVER=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=your-email@gmail.com
MAIL_PASSWORD=your-app-password

# API Keys
GEMINI_API_KEY=your-gemini-api-key
DALLE_API_KEY=your-dalle-api-key
GEOLOCATION_API_KEY=your-geolocation-api-key

# Application Settings
UPLOAD_FOLDER=uploads/
MAX_CONTENT_LENGTH=16777216
DEBUG=True
```

### Step 5: Initialize Database

```bash
# Create database
mysql -u root -p -e "CREATE DATABASE ahms_db;"

# Run migrations (if using Flask-Migrate)
flask db upgrade
```

### Step 6: Run the Application

```bash
python app.py
```

The application will be available at `http://localhost:5000`

---

## 📖 Usage Guide

### Patient Workflow
1. **Register:** Create account with email and date of birth
2. **Upload Documents:** Upload medical reports, test results, or X-rays
3. **View Summaries:** AI automatically generates summaries from uploaded documents
4. **Book Appointments:** Schedule consultations with available doctors
5. **Track History:** Access complete medical history and EMR

### Doctor Workflow
1. **Login:** Access doctor portal with credentials
2. **View Patients:** Browse list of assigned/registered patients
3. **Review Records:** Access patient's complete medical history
4. **Upload Reports:** Add clinical notes and test results
5. **Manage Schedule:** Set availability and manage appointment requests

### Emergency Assistance
1. Click "Emergency Help" button on any page
2. System detects location via GPS
3. AI provides first-aid guidance
4. One-click ambulance request with location sharing

---

## 🧪 Testing & Results

### Test Coverage
- **Clinical Documents:** 40 test cases
- **X-Ray Images:** 20 test cases
- **Load Testing:** Locust + Postman

### Performance Metrics
| Metric | Result |
|--------|--------|
| OCR Accuracy | 90.7% |
| NLP Summary Quality Score | 4.3/5.0 |
| CNN Model Accuracy | 82% |
| Avg. Processing Time (Report → Summary) | < 8 seconds |
| Concurrent Users (Load Test) | 100+ users |
| API Response Time | < 2 seconds |

### Running Tests

```bash
# Unit tests
pytest tests/

# Load testing
locust -f tests/locustfile.py

# API testing with Postman
# Import: postman_collection.json
```

---

## 🔐 Security Features

- **Authentication:** Secure password hashing (bcrypt)
- **Authorization:** Role-based access control (RBAC)
- **Data Encryption:** SSL/TLS for data in transit
- **Input Validation:** XSS and SQL injection prevention
- **HIPAA Compliance:** Audit logs for sensitive operations
- **Secure File Upload:** File type validation and sandboxing

---

## 📈 Future Enhancements

### Planned Features
- **HL7-FHIR Interoperability:** Standards-based healthcare data exchange
- **Mobile Application:** Native iOS/Android apps (Flutter)
- **Predictive Analytics:** ML models for disease risk prediction
- **Voice Assistant:** Speech-to-text medical documentation
- **Federated Learning:** Privacy-preserving distributed AI training
- **Blockchain Integration:** Immutable medical record verification
- **Real-time Notifications:** WebSocket-based alerts
- **Multi-language Support:** Localization for regional hospitals

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 👥 Contributors

### Development Team

| Name | Role | Contributions |
|------|------|---------------|
| **Pravesh Dubey** | AI Engineer | AI pipeline, OCR+NLP+CNN, Appointment system, EMR design |
| **Siddharth N. Allagi** | Frontend Developer | UI/UX, Dashboard design, Document upload module, Bootstrap integration |
| **Veeresh Pattar** | Database Engineer | Database schema, Doctor modules, Emergency integration, Testing |

### Academic Guidance
**Dr. Afroz Pasha**  
Department of Information Science  
Presidency University, Bangalore

---

## 📞 Support & Contact

For issues, questions, or suggestions:
- **GitHub Issues:** [Create an Issue](https://github.com/your-repo/issues)
- **Email:** your-email@example.com
- **Project Repository:** [GitHub Link](https://github.com/your-repo/ahms)

---

## 📄 License

This project is licensed under the **Academic License** - for academic and research purposes only.

**Commercial Use:** Requires explicit written permission from the authors.

```
© 2024 AHMS Project. All rights reserved.
```

---

## 🙏 Acknowledgments

We extend our gratitude to:
- **Presidency University** for academic support and resources
- **Dr. Afroz Pasha** for invaluable guidance and mentorship
- **Open Source Community:** Flask, MySQL, OpenCV, TensorFlow
- **API Providers:** Google AI, OpenAI, Geolocation Services
- **All testers and early adopters** for feedback and suggestions

---

## 📚 Additional Resources

- [Project Documentation](docs/)
- [API Reference](docs/API.md)
- [Database Schema](docs/DATABASE.md)
- [Deployment Guide](docs/DEPLOYMENT.md)
- [Contributing Guide](CONTRIBUTING.md)

---

<div align="center">

**⭐ If this project helped you, please consider giving it a star!**

Made with ❤️ by AHMS Team

</div>
