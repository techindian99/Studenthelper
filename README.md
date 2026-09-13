# 🎓 STUDY HELPER — Aapka AI Teacher (Single File · Gemini Powered)

> **Class 1–12 · CBSE / Bihar Board / ICSE / All Boards · Science · Commerce · Arts**
> Padho • Samjho • Jeeto 🚀 — Made by **One Boy Army**

Ek premium, mobile-first AI teacher chatbot — **Gemini (Google AI Studio)** se powered.
Student kuch bhi pooche — padhai, test paper, career, exam stress — STUDY HELPER simple
bhasha me (Hindi + English) **sateek aur crisp** jawab deta hai (na bahut lamba, na chhota).

**⭐ Sab kuch EK hi `main.py` me** — backend + AI + poora frontend (HTML/CSS/JS embedded)
+ database + security. Deploy ke liye sirf 2 file: `main.py` + `requirements.txt`.

---

## ✨ Features

| Feature | Status |
|---|---|
| 🧠 **Gemini AI** (Google AI Studio) + streaming | ✅ |
| 💬 Unlimited chat, word-by-word streaming | ✅ |
| 🕘 Chat History — localStorage + SQLite mirror | ✅ |
| 📄 File upload (PDF/Word/TXT) | ✅ |
| 🖼️ Image upload (Vision) — AI dekh kar jawab deta hai | ✅ |
| 🚫 **Offline demo HATA diya** — ab sirf real AI | ✅ |
| 🌈 5D UI — glassmorphism, neon, shine, 60fps | ✅ |
| ✨ Splash screen (customizable) | ✅ |
| 🌗 Dark / Light mode | ✅ |
| 📋 Copy, timestamps, typing dots, follow-up chips | ✅ |
| 🛡️ Security — CSP nonce, injection guard, rate limit | ✅ |
| 💤 **Keep-alive system** — server so na jaye | ✅ |

---

## 🔑 Gemini API Key Setup

Apni **Gemini API key** (Google AI Studio se) ko environment me daalo — bas itna hi.

### Local:
```bash
# Windows (CMD)
set GEMINI_API_KEY=AQ.xxxxxxxx...

# Mac / Linux
export GEMINI_API_KEY="AQ.xxxxxxxx..."

python main.py
```

### Render (Deploy):
Environment me add karo: `GEMINI_API_KEY` = apni key.

> **Auto-detect:** key `sk-...` se shuru ho to **OpenAI**, warna **Gemini** automatically
> select hota hai. Force karna ho to env me `PROVIDER=gemini` ya `PROVIDER=openai` daalo.
> Model badalna ho to `OPENAI_MODEL` daalo (default: `gemini-flash-latest` — fast + vision).

---

## 🚀 Deploy — GitHub + Render (FREE)

1. GitHub par **2 file** upload karo: `main.py` + `requirements.txt`.
2. https://render.com → **New + → Web Service** → repo select karo.
3. Settings:
   - **Build Command:** `pip install -r requirements.txt`
   - **Start Command:** `gunicorn main:app --workers 2 --threads 8 --timeout 120`
4. **Environment** me add karo:
   - `GEMINI_API_KEY` = `AQ.xxxx...`
5. **Create** → 2-3 min me live link 🔗

---

## 💤 Keep-Alive — Server Kabhi Band Na Ho

Render **free tier 15 min idle ke baad so jata hai**. Uske liye **3-layer system** lagaya hai:

1. **Frontend heartbeat (built-in):** jitni der browser tab khula hai, app har **8 minute** me
   server ko `ping` karti hai → server awake rehta hai. ✅ (already code me hai)
2. **Server self-ping (built-in):** app har **9 minute** me khud ko ping karti hai.
   (Dusre hosts jaise Railway/Koyeb/VPS par ye kaafi hai.)
3. **External pinger (GUARANTEED — FREE):** Render free par soya hua server khud nahi jag
   sakta, isliye ek **bahar ka pinger** lagao. Ye 2 minute ka kaam hai:
   - https://uptimerobot.com → free account
   - **New monitor** → type: HTTP(s) → URL: `https://tumhara-app.onrender.com/healthz`
   - Interval: **10 minutes** → Save.
   - Ab har 10 min ek request aayegi → server **kabhi nahi soyega**. ✅

> 💡 UptimeRobot ka free plan 5 min interval deta hai — 10 min se kam rakho (15 min se
> neeche hona chahiye). Alternative: cron-job.org (free).

---

## 🎨 Customize (sab `main.py` me comment karke)

| Kya badalna | Kahan (main.py me) |
|---|---|
| **Splash** (naam, tagline, made-by, duration) | HTML me `SPLASH_CONFIG` |
| **Colors / theme** | `<style>` ke `:root` variables |
| **Bot personality / rules / answer length** | `SYSTEM_PROMPT` |
| **AI model / provider** | `CONFIG` (upar) |
| **Upload size limits** | `CONFIG["max_file_bytes"]` / `max_image_bytes` |

---

## 🔒 Security

- **CSP nonce** (har request fresh) — XSS block
- **Prompt-injection guard** — "ignore instructions" jaisi tricks block
- **Rate limiting** per IP — spam/DoS se bachav
- **Client-scoped chats** — doosra user tumhari chat nahi dekh sakta
- **File allow-list + size caps** — sirf PDF/Word/TXT/images, 10MB
- **API key sirf backend me** — frontend me kabhi expose nahi
- **Parameterized SQL** — injection safe

---

## 🆘 Troubleshooting

| Problem | Fix |
|---|---|
| `ModuleNotFoundError: flask` | `pip install -r requirements.txt` |
| "AI key set nahi hai" | Env me `GEMINI_API_KEY` daalo |
| Jawab bahut lamba/chhota | `SYSTEM_PROMPT` me answer-length rules badlo |
| Render 502 | Start command `gunicorn main:app` sahi? |
| Server so jata hai | UptimeRobot monitor lagao (upar dekho) |

**Made with ❤️ by One Boy Army**

