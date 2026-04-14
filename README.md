# JobSync AI 🚀

[![JobSync AI](https://img.shields.io/badge/JobSync%20AI-ATS%20Optimizer-brightgreen)](https://jobsync-ai.vercel.app/)

**Sync your resume to any Job Description in <30 seconds.** AI-powered, ATS-optimized PDF generation. Upload once, reuse forever. Free forever.

## 🎯 Features

| Feature | Description |
|---------|-------------|
| **⚡ Instant** | Resume generation in 20-30 seconds |
| **🎯 ATS-Optimized** | 98% ATS pass rate with exact JD keywords |
| **🧠 Smart** | Gemini AI rewrites for relevance without sounding robotic |
| **📄 PDF Output** | Professional LaTeX-compiled PDFs (not Word docs) |
| **🔄 Returning Users** | One-time upload — just paste new JDs |
| **📐 Clean Design** | Single-page app with custom animations, dark mode |
| **🔒 Private** | No data selling. Email-based user tracking only |

## 🏗️ Architecture

```
Frontend (index.html) ──► n8n Webhooks ──► Gemini AI ──► LaTeX ──► ConvertHub ──► PDF
     ↓                                                   ↓
Google Sheets (User DB)                         Professional Resume PDF
```

**Flow:**
```
1. User enters email → Check if existing in Google Sheets
2. New: Upload PDF → Extract text → Save user
3. Paste JD → Gemini optimizes → LaTeX → PDF compile
4. Download ATS-ready resume
```

## 📱 Live Demo

Open `index.html` in browser:
```
npx serve .
```
- Uses mock loading (25s) for demo
- Replace webhook URLs with your n8n instance

## 🚀 Quick Start (Production)

### Backend (n8n Workflow)
1. Import `Resume Personalizer – ATS Optimizer (ConvertHub) (2).json` to n8n
2. Update credentials:
   - Google Sheets API
   - Google Gemini (PaLM) API
   - ConvertHub API key
3. Copy webhook URLs:
   ```
   CHECK_EMAIL = https://your-n8n.com/webhook/check-email
   GENERATE = https://your-n8n.com/webhook/resume-generator
   ```

### Frontend
```bash
# Update webhooks in index.html script section
const WEBHOOK_CHECK_EMAIL = 'YOUR_CHECK_URL';
const WEBHOOK_GENERATE = 'YOUR_GENERATE_URL';

# Deploy
npx serve .  # Local
vercel .     # Production
```

## 🛠️ Tech Stack

| Layer | Tech |
|-------|------|
| **Frontend** | HTML/CSS/JS, Custom cursor, GSAP-like animations |
| **Backend** | n8n workflows, Google Sheets (user DB) |
| **AI** | Google Gemini (PaLM 2) for semantic optimization |
| **PDF** | LaTeX → LuaLaTeX → ConvertHub API |
| **PDF Parse** | n8n PDF Extract node |
| **Fonts** | Syne, DM Mono, DM Sans (Google Fonts) |
| **Deploy** | Vercel/Netlify (frontend), n8n.cloud/self-hosted |

## 📁 Project Structure

```
JobSync-AI/
├── index.html           # Full landing page + app
└── Resume Personalizer – ATS Optimizer (ConvertHub) (2).json  # n8n workflow
```

## 🎨 Design

- **Dark theme**: `--bg: #050508`, accent `#6af0a0`
- **Custom cursor**: Blend-mode + ring follower
- **Grid + noise overlay**: Subtle background texture
- **Floating orbs**: Glowing ambient elements
- **Smooth reveals**: Intersection Observer
- **Modal flow**: Multi-step app experience

## 🔍 Key Optimizations

**ATS Compliance:**
```
✅ No tables/images/columns
✅ Linear text flow  
✅ Exact JD keywords injected
✅ Semantic rewrites (not keyword stuffing)
✅ 1-page strict limit (LaTeX geometry tweaks)
```

**LaTeX Template:** Custom 1-page resume with:
- 0.4\" margins, 10pt font
- Tight spacing (`\\titlespacing`, `\\parskip=1pt`)
- `\\href{}` for contact links
- No page numbers

## 📈 Stats (Landing Page)

```
98% ATS Pass Rate    <30s Generation    Free Forever
```

## 👨‍💻 Author

**Aditya Jaiswal**  
AI Automation Engineer · B.Tech CS-AI (AKTU)  
[LinkedIn](https://www.linkedin.com/in/adityajaiswal25/) | [GitHub](https://github.com/adityajaiswal25) | [aditya.jaiswal25003@gmail.com](mailto:aditya.jaiswal25003@gmail.com)

Built in Bengaluru, India 🇮🇳

## 🚀 Deploy Your Own

```bash
# 1. Fork this repo
# 2. Deploy frontend to Vercel/Netlify
# 3. Deploy n8n workflow (Railway/Docker)
# 4. Update webhook URLs
# 5. Go live!
```

---

**⭐ Star if you found this useful!**  
**Built for job seekers, by a job seeker.**

