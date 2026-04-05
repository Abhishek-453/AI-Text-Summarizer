# 🤖 AI Text Summarizer

> A full-stack AI-powered web application that summarizes long texts, PDFs, Word documents, and URLs into concise summaries. Supports multilingual translation (English ↔ Hindi), keyword extraction, and bullet-point formatting.

---

## 🌐 Live Demo

**Public URL:** [https://leia-blowsiest-undiligently.ngrok-free.dev](https://leia-blowsiest-undiligently.ngrok-free.dev)

> ⚠️ Note: This URL is active only when the host machine is running all services. A new URL is generated each time ngrok is restarted.

---

## 📌 Project Info

| Detail | Info |
|---|---|
| **University** | Babu Banarasi Das University, Lucknow |
| **Project Type** | Final Year B.Tech Project |
| **Group** | Group 79 |
| **Supervisor** | Ms. Sweety Pal |
| **Contributors** | Sadaf | Sachin | Tanveer

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│   Frontend (Next.js)     :3000                      │
│        │                                            │
│        ▼                                            │
│   Backend (Node.js/Express)  :5000                  │
│        │                   │                        │
│        ▼                   ▼                        │
│   MongoDB Atlas      AI Service (FastAPI)  :8000    │
│   (Cloud DB)         HuggingFace T5-small           │
│                                                     │
└─────────────────────────────────────────────────────┘
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | Next.js 15+, React 19, Tailwind CSS 4, Framer Motion |
| **Backend** | Express.js, TypeScript, MongoDB (Mongoose) |
| **AI Service** | FastAPI, HuggingFace Transformers (T5-small), PyTorch |
| **Database** | MongoDB Atlas (Cloud) |
| **Document Processing** | pdf-parse (PDF), mammoth (DOCX) |
| **Translation** | deep-translator (Google Translate API) |
| **URL Extraction** | newspaper3k, BeautifulSoup4 |
| **Public Tunnel** | ngrok |

---

## ✅ Prerequisites

Make sure the following are installed on your system before running the project:

- **Node.js** v18 or higher → [Download](https://nodejs.org)
- **Python** v3.9 or higher (Miniconda/Anaconda recommended) → [Download](https://www.anaconda.com)
- **Git** → [Download](https://git-scm.com)
- **ngrok** (for public URL) → [Download](https://ngrok.com/download) or install via Microsoft Store
- **MongoDB Atlas account** (free) → [Sign Up](https://mongodb.com/atlas)

---

## 🚀 Installation & First Time Setup

### Step 1 — Clone the Repository

```bash
git clone https://github.com/sachinyadav2390/AI-Text-Summarizer-.git
cd AI-Text-Summarizer-
```

### Step 2 — Install Frontend & Backend Dependencies

```bash
npm install
```

### Step 3 — Install AI Service Dependencies

```bash
cd ai-service
pip install -r requirements.txt
cd ..
```

> ⚠️ First time: This will download the T5-small AI model (~250MB). Make sure you have internet connection.

### Step 4 — Setup Environment Variables

Create a `.env` file in the root project folder:

```bash
# Windows PowerShell
Set-Content .env "MONGODB_URI=mongodb+srv://<username>:<password>@<cluster>.mongodb.net/ai-summarizer?appName=<ClusterName>`nPORT=5000"
```

Or manually create `.env` file with this content:

```
MONGODB_URI=mongodb+srv://your_username:your_password@yourcluster.mongodb.net/ai-summarizer?appName=YourCluster
PORT=5000
```

> 💡 Get your MongoDB Atlas connection string from: Atlas Dashboard → Clusters → Connect → Drivers → Node.js

### Step 5 — Fix db.ts to Load dotenv (Important!)

Open `server/config/db.ts` and make sure it looks like this:

```typescript
import mongoose from "mongoose";
import dotenv from "dotenv";

dotenv.config();

const MONGO_URI = process.env.MONGODB_URI || "mongodb://127.0.0.1:27017/ai-text-summarizer";

export async function connectDB(): Promise<void> {
  try {
    await mongoose.connect(MONGO_URI);
    console.log(`✅ MongoDB connected: ${mongoose.connection.host}`);
  } catch (error) {
    console.error("❌ MongoDB connection failed:", error);
    process.exit(1);
  }
}

export default connectDB;
```

---

## ▶️ How to Run the Project (Every Time)

Every time you want to run the project, open **4 separate terminals** and run the following:

### Terminal 1 — Frontend

```bash
cd AI-Text-Summarizer--main
npm run dev
```

✅ Frontend runs at: `http://localhost:3000`

---

### Terminal 2 — Backend

```bash
cd AI-Text-Summarizer--main
npx ts-node --project server/tsconfig.json server/index.ts
```

✅ Backend runs at: `http://localhost:5000`
✅ You should see: `MongoDB connected: ac-xxxxx.mongodb.net`

---

### Terminal 3 — AI Service

```bash
cd AI-Text-Summarizer--main\ai-service
python main.py
```

✅ AI Service runs at: `http://localhost:8000`
✅ You should see: `Uvicorn running on http://0.0.0.0:8000`

---

### Terminal 4 — ngrok (Public URL)

```bash
ngrok http 3000
```

✅ You will get a public URL like:
```
Forwarding  https://xxxx-xxxx.ngrok-free.app → http://localhost:3000
```

> ⚠️ Share this URL with your teacher/judge. It changes every time ngrok restarts.

---

## 🌐 Service URLs

| Service | Local URL | Description |
|---|---|---|
| Frontend | http://localhost:3000 | Main web app |
| Backend API | http://localhost:5000 | REST API server |
| AI Service | http://localhost:8000 | FastAPI AI engine |
| AI Health Check | http://localhost:8000/health | Check if AI is running |
| Public URL | Generated by ngrok | Share this with others |

---

## 📡 API Endpoints

### Backend (Port 5000)

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/summarize` | Summarize text or URL |
| POST | `/api/upload` | Upload PDF/DOCX file |
| GET | `/api/history` | Get last 20 summaries |
| POST | `/api/contact` | Send contact message |

### AI Service (Port 8000)

| Method | Endpoint | Description |
|---|---|---|
| POST | `/ai/summarize` | Generate abstractive summary |
| POST | `/ai/translate` | Translate text |
| POST | `/ai/keywords` | Extract top 10 keywords |
| GET | `/health` | Check service health |
| POST | `/models/load` | Pre-load AI models |

---

## 🌟 Features

- 📝 **Text Summarization** — Paste any long text and get a concise summary
- 📄 **Document Support** — Upload `.pdf` or `.docx` files directly
- 🔗 **URL Extraction** — Paste any article link for automatic content extraction
- 🌐 **Multilingual** — Auto-detects language, translates to English, summarizes, translates back to Hindi
- ⚡ **Fast** — T5-small model gives results in under 5 seconds on CPU
- 📊 **History** — Last 20 summaries stored in MongoDB Atlas
- 🔑 **Keyword Extraction** — Extracts top 10 relevant keywords
- 📋 **Bullet Points** — Converts summaries to bullet-point format

---

## ⚠️ Common Problems & Fixes

### ❌ Problem 1: `'concurrently' is not recognized`

```
'concurrently' is not recognized as an internal or external command
```

**Fix:**
```bash
npm install
```

---

### ❌ Problem 2: `ModuleNotFoundError: No module named 'torch'`

```
ModuleNotFoundError: No module named 'torch'
```

**Fix:**
```bash
cd ai-service
pip install -r requirements.txt
```

---

### ❌ Problem 3: `MongoDB connection failed: connect ECONNREFUSED 127.0.0.1:27017`

```
MongooseServerSelectionError: connect ECONNREFUSED 127.0.0.1:27017
```

**Cause:** Either MongoDB is not running locally OR `.env` file is not set up correctly.

**Fix Option A — Use MongoDB Atlas (Recommended):**
1. Go to [https://mongodb.com/atlas](https://mongodb.com/atlas)
2. Login → Resume your cluster if paused
3. Click Connect → Drivers → Copy connection string
4. Create `.env` file with:
```
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/ai-summarizer
PORT=5000
```

**Fix Option B — Start Local MongoDB:**
```bash
# Windows
net start MongoDB
```

---

### ❌ Problem 4: `.env` not being read (still connecting to localhost)

**Cause:** `db.ts` file uses `MONGO_URI` but `.env` has `MONGODB_URI` — variable name mismatch. Also `dotenv.config()` was missing.

**Fix:** Update `server/config/db.ts` — add `import dotenv from "dotenv"` and `dotenv.config()` at the top, and change `MONGO_URI` to `MONGODB_URI`.

---

### ❌ Problem 5: `'ngrok' is not recognized`

```
'ngrok' is not recognized as an internal or external command
```

**Fix Option A — Install via winget:**
```bash
winget install ngrok.ngrok
```
Then close and reopen terminal.

**Fix Option B — Install via Microsoft Store:**
Search "ngrok" in Microsoft Store and install.

---

### ❌ Problem 6: ngrok authtoken error

**Fix:**
```bash
ngrok config add-authtoken YOUR_TOKEN_HERE
```
Get your token from: [https://dashboard.ngrok.com/get-started/your-authtoken](https://dashboard.ngrok.com/get-started/your-authtoken)

---

### ❌ Problem 7: Port already in use

```bash
# Find process using port 5000 (Windows)
netstat -ano | findstr :5000
taskkill /PID <PID_NUMBER> /F
```

---

## 📁 Project Structure

```
AI-Text-Summarizer--main/
│
├── src/                        # Next.js Frontend
│   └── app/                    # App Router pages
│
├── server/                     # Node.js Backend
│   ├── config/
│   │   └── db.ts               # MongoDB connection
│   └── index.ts                # Express server entry
│
├── ai-service/                 # Python AI Microservice
│   ├── main.py                 # FastAPI app
│   ├── engine.py               # Summarization logic
│   ├── config.py               # Model configurations
│   └── requirements.txt        # Python dependencies
│
├── .env                        # Environment variables (NOT on GitHub)
├── package.json                # Node.js dependencies
├── next.config.ts              # Next.js configuration
└── README.md                   # This file
```

---

## 🔐 Environment Variables

| Variable | Description | Example |
|---|---|---|
| `MONGODB_URI` | MongoDB Atlas connection string | `mongodb+srv://user:pass@cluster.mongodb.net/db` |
| `PORT` | Backend server port | `5000` |

> ⚠️ Never commit `.env` to GitHub! It is already in `.gitignore`.

---

## 👥 Contributors

| Name | GitHub |
|---|---|
| Sachin Yadav | [@sachinyadav2390](https://github.com/sachinyadav2390) |
| Himanshu Yadav | [@Himanshuyadav6764](https://github.com/Himanshuyadav6764) |

---

## 📄 License

This project was built as a Final Year B.Tech Project at BBD University, Lucknow.

---

*Made with ❤️ by Group 79 — BBD University, Lucknow*
