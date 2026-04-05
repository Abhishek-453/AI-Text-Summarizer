# 🚀 AI Text Summarizer — Project Start Guide

---

## ⚠️ Step 0 — MongoDB Atlas Check karo (SABSE PEHLE)

👉 **https://cloud.mongodb.com** pe jao

Agar cluster paused dikhe → **"Resume"** button click karo → 2-3 min wait karo

---

## Step 1 — Terminal 1 : Frontend

```bash
cd C:\Users\HP\Downloads\Ai-text\AI-Text-Summarizer--main
npm run dev
```

✅ Yeh dikhega:
```
▲ Next.js 16.1.6
✓ Ready on http://localhost:3000
```

---

## Step 2 — Terminal 2 : Backend

```bash
cd C:\Users\HP\Downloads\Ai-text\AI-Text-Summarizer--main
npx ts-node --project server/tsconfig.json server/index.ts
```

✅ Yeh dikhega:
```
✅ MongoDB connected
✅ Backend server running on http://localhost:5000
```

---

## Step 3 — Terminal 3 : AI Service

```bash
cd C:\Users\HP\Downloads\Ai-text\AI-Text-Summarizer--main\ai-service
python main.py
```

✅ Yeh dikhega:
```
AI Summarization Engine Starting...
Uvicorn running on http://0.0.0.0:8000
```

---

## Step 4 — Terminal 4 : Public URL (ngrok)

```bash
ngrok http 3000
```

✅ Yeh dikhega:
```
Forwarding  https://xxxx.ngrok-free.app → localhost:3000
```

> 🌐 Woh https:// URL copy karo — yahi public link hai!

---

## ✅ Sab Sahi Chal Raha Hai — Checklist

| Service | Port | Success Message |
|---------|------|----------------|
| Frontend | 3000 | `Ready on http://localhost:3000` |
| Backend | 5000 | `MongoDB connected` |
| AI Service | 8000 | `Uvicorn running on http://0.0.0.0:8000` |
| ngrok | — | `Forwarding https://xxxx.ngrok-free.app` |

---

## ❌ Common Errors & Quick Fix

| Error | Fix |
|-------|-----|
| `MongoDB connection failed` | Atlas pe cluster Resume karo |
| `'ngrok' is not recognized` | Naya terminal kholo |
| `No module named 'torch'` | `cd ai-service` → `pip install -r requirements.txt` |
| `'concurrently' is not recognized` | `npm install` run karo |

---

## 🔗 Important Links

| Kya | Link |
|-----|------|
| Local App | http://localhost:3000 |
| MongoDB Atlas | https://cloud.mongodb.com |
| GitHub Repo | https://github.com/Abhishek-453/AI-Text-Summarizer |

---

> 💡 **Yaad Rakho:** Jab tak yeh 4 terminals chal rahi hain aur laptop on hai —
> tabhi public ngrok URL kaam karega!
