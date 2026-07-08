<p align="center">
  <h1 align="center">🌾 DhanSathi — Smart Farming & Financial Companion</h1>
  <p align="center">
    <em>An AI-powered Android app that empowers Indian farmers with government scheme eligibility, crop guidance, income analysis, and financial tracking — all in their own language.</em>
  </p>
  <p align="center">
    <img src="https://img.shields.io/badge/Platform-Android-3DDC84?logo=android&logoColor=white" alt="Android">
    <img src="https://img.shields.io/badge/Language-Kotlin-7F52FF?logo=kotlin&logoColor=white" alt="Kotlin">
    <img src="https://img.shields.io/badge/UI-Jetpack%20Compose-4285F4?logo=jetpackcompose&logoColor=white" alt="Jetpack Compose">
    <img src="https://img.shields.io/badge/Backend-FastAPI-009688?logo=fastapi&logoColor=white" alt="FastAPI">
    <img src="https://img.shields.io/badge/AI-Groq%20LLaMA%203.3-FF6F00?logo=meta&logoColor=white" alt="Groq AI">
    <img src="https://img.shields.io/badge/Database-Firebase-FFCA28?logo=firebase&logoColor=black" alt="Firebase">
    <img src="https://img.shields.io/badge/Local%20DB-Room-00796B" alt="Room">
  </p>
</p>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Architecture](#-architecture)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Screenshots & Screens](#-screenshots--screens)
- [Backend API Documentation](#-backend-api-documentation)
- [Data Sources](#-data-sources)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Android App Setup](#android-app-setup)
  - [Backend Server Setup](#backend-server-setup)
- [Environment Variables](#-environment-variables)
- [Deployment](#-deployment)
- [Multilingual Support](#-multilingual-support)
- [Contributors](#-contributors)
- [License](#-license)

---

## 🌟 Overview

**DhanSathi** (meaning *"Wealth Companion"*) is a full-stack mobile application built to serve Indian farmers — especially those in rural Maharashtra. It combines **AI-driven agricultural advisory**, **government scheme discovery**, **seasonal income planning**, and **day-to-day financial tracking** into a single, easy-to-use Android app with multilingual support (English, Hindi, and Marathi).

The app connects to a **FastAPI backend** powered by **Groq's LLaMA 3.3 70B** model for intelligent, context-aware responses, and uses **Firebase** for authentication, cloud storage, and push notifications with **Room** for offline-first local data persistence.

---

## ✨ Key Features

### 🔐 Authentication & User Management
- **Phone-based OTP Authentication** via Firebase Auth
- **User Profile Management** — name, state, land holding, crops grown, income level
- **Session Management** with automatic lifecycle tracking
- **Google Sign-In** support

### 🏠 Dashboard
- Centralized overview of farm activities, income summary, and quick actions
- Quick-access navigation to all major features
- Real-time status cards and summary widgets

### 🌱 Farm Guidance (AI-Powered)
- **Crop-specific advice** powered by LLaMA 3.3 AI model
- **Yield Prediction** — estimated output based on land size and crop data
- **Cost Estimation** — total cultivation cost breakdown
- **Price Prediction** — expected market selling price
- **Profit Estimation** — projected profit with best/worst case scenarios
- **Risk Analysis** — potential threats and mitigation strategies
- **Step-by-Step Roadmap** — planting-to-harvest guidance
- Supports **10 major Maharashtra crops**: Cotton, Sugarcane, Onion, Tur, Gram, Maize, Soybean, Groundnut, Jowar, and Pomegranate

### 🏛️ Government Schemes Eligibility Checker
- Automatically checks farmer eligibility against **7+ government schemes**:
  - PM-KISAN (₹6,000/year direct benefit)
  - PMFBY (Crop Insurance)
  - Maharashtra Farm Pond Subsidy
  - Micro Irrigation / Drip Subsidy (PMKSY)
  - Agricultural Mechanization Subsidy
  - Interest Subvention on Crop Loans
  - Maharashtra Horticulture & Onion Storage Support
- Shows **required documents**, **application links**, and **AI-generated eligibility justifications**

### 📊 Seasonal Income Analysis
- Analyzes **irregular & seasonal income patterns** for farmers
- **Monthly income predictions** based on source seasonality
- **Safe spending limits** calculated per month
- **Recommended savings** strategy
- **AI-generated insights** on income seasonality and financial planning
- Month-by-month savings roadmap with surplus/deficit flagging

### 💰 Cash Diary (Track Money)
- **Record income & expenses** with categories (Farm Income, Daily Wage, Food & Grocery, Transport, Medical, Education, Utilities, etc.)
- Track **total income, total expenses, and balance**
- **Voice-based transaction entry** — speak naturally to log transactions (e.g., "Sold vegetables for 500 rupees today")
- AI-powered **voice transaction parsing** in English, Hindi, and Marathi
- Delete transactions
- Cloud-synced to Firebase with offline Room support

### 📈 Analytics Dashboard
- Visual charts and breakdowns of financial data
- Income vs Expense trends
- Category-wise spending analysis

### 🤖 AI Saathi (Chatbot)
- **Bilingual chatbot** (English + Marathi) for farming guidance
- Context-aware responses on crops, schemes, financial advice
- **Smart follow-up suggestions** based on conversation topics
- Powered by Groq LLaMA 3.3 70B Versatile model

### 🧭 Navigation Assistant
- AI-powered **in-app navigation chatbot** to help users find features
- Knowledge-base driven with page descriptions and common actions
- Suggests relevant pages and auto-navigates

### 🎤 Voice Input
- **Speech-to-Text** for hands-free interaction
- Voice commands for transaction logging
- Multi-language voice recognition (English, Hindi, Marathi)

### 📚 Learning Center
- Educational content about modern farming techniques
- Tutorials, articles, and guides on government programs

### 🎫 Support Tickets System
- **Create support tickets** for issues and queries
- Track ticket status (Open, In Progress, Resolved, Closed)
- View all user tickets with priority and category tagging
- Admin dashboard for managing all tickets

### 🔔 Notifications
- **Firebase Cloud Messaging (FCM)** for push notifications
- **Notification Scheduler** for periodic reminders
- Configurable **notification preferences**

### 📤 Data Export
- Export financial and farm data for record-keeping

### ⚙️ Settings & Preferences
- Language settings
- Voice settings
- Theme preferences
- DataStore-based persistent preferences

---

## 🏗 Architecture

```
┌──────────────────────────────────────────────────────────────┐
│                     ANDROID APP (Kotlin)                     │
│                                                              │
│  ┌──────────┐  ┌──────────────┐  ┌────────────────────────┐ │
│  │  Screens  │  │  ViewModels  │  │     Navigation Graph   │ │
│  │ (Compose) │──│  (State Mgmt)│──│  (Jetpack Navigation)  │ │
│  └──────────┘  └──────────────┘  └────────────────────────┘ │
│        │                │                                    │
│  ┌─────┴────────────────┴──────────────────────────────────┐ │
│  │                    DATA LAYER                           │ │
│  │  ┌────────────┐  ┌──────────┐  ┌───────────────────┐   │ │
│  │  │ Repositories│  │ Room DB  │  │  DataStore Prefs  │   │ │
│  │  └──────┬─────┘  └────┬─────┘  └───────────────────┘   │ │
│  │         │              │                                 │ │
│  │  ┌──────┴──────┐  ┌───┴────┐                            │ │
│  │  │  Retrofit   │  │  DAOs  │                            │ │
│  │  │  API Client │  │        │                            │ │
│  │  └──────┬──────┘  └────────┘                            │ │
│  └─────────┼───────────────────────────────────────────────┘ │
│            │                                                  │
│  ┌─────────┴──────────────────────────────────────────────┐  │
│  │               SERVICES                                  │  │
│  │  Firebase Messaging · Notification Scheduler            │  │
│  │  Session Manager · Sync Manager                         │  │
│  └─────────────────────────────────────────────────────────┘  │
└──────────────────────────┬───────────────────────────────────┘
                           │ HTTPS (Retrofit)
                           ▼
┌──────────────────────────────────────────────────────────────┐
│                  FASTAPI BACKEND (Python)                     │
│                                                              │
│  ┌────────────────────────────────────────────────────────┐  │
│  │  Endpoints:                                            │  │
│  │  /schemes · /farm-help · /seasonal-income · /chat      │  │
│  │  /navigation-chat · /profile · /transactions           │  │
│  │  /parse-voice-transaction · /tickets                   │  │
│  │  /voice-input · /voice-output                          │  │
│  └───────────────────────┬────────────────────────────────┘  │
│                          │                                    │
│  ┌───────────────┐  ┌────┴──────┐  ┌──────────────────────┐ │
│  │  Groq LLM     │  │ Firebase  │  │  CSV/JSON            │ │
│  │  (LLaMA 3.3)  │  │ Firestore │  │  Data Files          │ │
│  └───────────────┘  └───────────┘  └──────────────────────┘ │
└──────────────────────────────────────────────────────────────┘
```

---

## 🛠 Tech Stack

### Android App (Frontend)
| Technology | Purpose |
|---|---|
| **Kotlin** | Primary language |
| **Jetpack Compose** | Declarative UI framework |
| **Material 3** | Design system |
| **Navigation Compose** | Screen-to-screen navigation |
| **Firebase Auth** | Phone OTP authentication |
| **Firebase Firestore** | Cloud database |
| **Firebase Cloud Messaging** | Push notifications |
| **Room Database** | Local offline storage |
| **Retrofit + Gson** | REST API communication |
| **OkHttp** | HTTP client with logging |
| **DataStore Preferences** | Local key-value storage |
| **WorkManager** | Background sync tasks |
| **Google Play Services Auth** | Google Sign-In |

### Backend Server
| Technology | Purpose |
|---|---|
| **Python 3.10+** | Server language |
| **FastAPI** | REST API framework |
| **Uvicorn** | ASGI server |
| **LangChain** | LLM orchestration framework |
| **Groq (LLaMA 3.3 70B)** | AI model for intelligent responses |
| **Firebase Admin SDK** | Server-side Firestore access |
| **Pandas** | Crop data processing |
| **Pydantic** | Request/response validation |
| **SpeechRecognition** | Speech-to-text processing |
| **pyttsx3 / gTTS** | Text-to-speech generation |

---


## 🔌 Backend API Documentation

Base URL: `http://localhost:8000`

### Health Check
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/` | API health check and endpoint listing |

### User Profile
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/profile` | Create or update user profile |
| `GET` | `/profile/{user_id}` | Retrieve user profile |

### Government Schemes
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/schemes` | Check scheme eligibility based on farmer info |

### Farm Guidance
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/farm-help` | Get AI-powered crop analysis, yield predictions, cost estimates, profit projections, risk analysis, and step-by-step roadmap |

### Seasonal Income
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/seasonal-income` | Analyze seasonal income patterns with savings recommendations |

### AI Chatbot
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/chat` | General farming chatbot (bilingual) |
| `POST` | `/navigation-chat` | Navigation assistant chatbot |

### Transactions
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/transactions` | Add a new transaction |
| `GET` | `/transactions/{user_id}` | Get all user transactions |
| `DELETE` | `/transactions/{transaction_id}` | Delete a transaction |

### Voice
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/voice-input` | Convert speech to text |
| `POST` | `/voice-output` | Convert text to speech |
| `POST` | `/parse-voice-transaction` | Parse voice input into structured transaction |

### Support Tickets
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/tickets` | Create a support ticket |
| `GET` | `/tickets/{user_id}` | Get user's tickets |
| `GET` | `/tickets/admin/all` | Get all tickets (admin) |

---

## 📊 Data Sources

### Crop Database (`crop_data.csv`)
Contains detailed data for **10 major Maharashtra crops**:

| Crop | Region | Season |
|------|--------|--------|
| Cotton (BT) | Vidarbha/Marathwada | Kharif |
| Sugarcane | Western Maharashtra | Annual |
| Onion (Red/Nashik) | Nashik | Rabi/Zaid |
| Tur (Arhar) | Marathwada/Khandesh | Kharif |
| Gram (Chana) | Vidarbha/Rainfed | Rabi |
| Maize | Central Maharashtra | Kharif |
| Soybean | Marathwada | Kharif |
| Groundnut | Western Maharashtra | Kharif/Rabi |
| Jowar (Sorghum) | Marathwada | Kharif/Rabi |
| Pomegranate | Nashik | Perennial |

Each crop entry includes: yield per acre, cultivation cost, MSP 2025, market price range, sowing/harvest months, irrigation needs, water requirements, and risk factors.

### Government Schemes (`schemes.json`)
7 central and state-level agricultural schemes with eligibility rules, benefits, required documents, and application links.

### Navigation Knowledge Base (`navigation_kb.json`)
14 page definitions with descriptions, features, and paths for the AI navigation assistant.

---

## 🚀 Getting Started

### Prerequisites

- **Android Studio** Hedgehog (2023.1.1) or later
- **JDK 11** or higher
- **Android SDK 35** (compileSdk) with minSdk 24
- **Python 3.10+**
- **Groq API Key** (free at [console.groq.com](https://console.groq.com))
- **Firebase Project** with Authentication (Phone) and Firestore enabled

### Android App Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/mad-mini.git
   cd mad-mini/myminiproject
   ```

2. **Open in Android Studio**
   - File → Open → Select the `myminiproject` directory

3. **Configure Firebase**
   - Place your `google-services.json` in `myminiproject/app/`
   - Enable **Phone Authentication** in Firebase Console
   - Enable **Cloud Firestore** database
   - Enable **Cloud Messaging** for push notifications

4. **Update API Base URL**
   - Open `ApiClient.kt` and update the base URL to your backend server address

5. **Build & Run**
   ```bash
   ./gradlew assembleDebug
   ```
   Or click ▶️ Run in Android Studio targeting an emulator or physical device (API 24+).

### Backend Server Setup

1. **Navigate to server directory**
   ```bash
   cd mad-mini/server
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate        # Linux/Mac
   venv\Scripts\activate           # Windows
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**
   ```bash
   # Create .env file
   GROQ_API_KEY=your_groq_api_key_here
   ```

5. **Add Firebase Admin credentials**
   - Place your Firebase service account key as `firebase-key.json` in the `server/` directory

6. **Run the server**
   ```bash
   python main.py
   ```
   Or using uvicorn directly:
   ```bash
   uvicorn main:app --host 0.0.0.0 --port 8000 --reload
   ```

7. **Verify**
   - Open `http://localhost:8000` — you should see the API status JSON
   - Interactive docs at `http://localhost:8000/docs` (Swagger UI)

---

## 🔑 Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `GROQ_API_KEY` | API key from [Groq Console](https://console.groq.com) for LLaMA 3.3 access | ✅ Yes |

---

## 🚢 Deployment

### Backend Deployment

The backend includes a `Procfile` for easy deployment to platforms like **Heroku**, **Render**, or **Railway**:

```
web: uvicorn main:app --host 0.0.0.0 --port $PORT
```

**Deploy to Render:**
1. Push the `server/` directory to a Git repository
2. Create a new Web Service on [Render](https://render.com)
3. Set the build command: `pip install -r requirements.txt`
4. Set the start command: `uvicorn main:app --host 0.0.0.0 --port $PORT`
5. Add `GROQ_API_KEY` as an environment variable

### Android APK Build
```bash
cd myminiproject
./gradlew assembleRelease
```
The APK will be available at `app/build/outputs/apk/release/`.

---

## 🌐 Multilingual Support

DhanSathi supports three languages across the app and AI responses:

| Language | Code | Coverage |
|----------|------|----------|
| 🇬🇧 English | `english` | Full — all features and AI responses |
| 🇮🇳 Hindi | `hindi` | AI responses, farm guidance, schemes, income analysis |
| 🇮🇳 Marathi | `marathi` | AI responses, chatbot, schemes data, voice transaction parsing |

The AI chatbot automatically provides **bilingual responses** (English + Marathi) for maximum accessibility. Voice transaction parsing supports natural language input in all three languages.

---

## 📄 License

This project is built for academic and educational purposes.

---

<p align="center">
  <strong>🌾 Empowering Farmers, One App at a Time 🌾</strong>
</p>
