# 🎧 Sync Suno

Apne dost ke saath same YouTube song ek saath, ek time pe suno — chahe wo kitni bhi door ho.

**Made by Lokesh Patel · Lopa Studios**

---

## Features

- 🎵 Room banao ya kisi ke room mein join karo (simple code jaise `SUNO-4821`)
- 🔗 Ek link share karo, dost seedha room mein aa jayega
- ▶️ Play / Pause / Seek dono devices pe automatically sync
- 📃 YouTube link se song add karo — playlist/queue bhi bana sakte ho
- 🎧 Audio-only experience (video hidden, sirf gaana sunayi dega)
- 📱 Mobile-first design, koi app install nahi karna

## Kaise kaam karta hai

- Player ke liye **YouTube IFrame API** use hota hai (video hidden rehta hai, sirf audio chalta hai)
- Song **search karne** ke liye **YouTube Data API v3** use hoti hai — gaane ka naam type karo, results mil jaate hai, tap karke queue mein add ho jaata hai
- Sync ke liye **kvdb.io** (free, no-signup key-value store) use hota hai — har 1.5 second mein state check hoti hai aur dono devices sync ho jaate hai
- Koi backend server nahi chahiye — pura static site hai

## YouTube API Key kaise banaye (zaroori step)

Search feature ke liye ek free YouTube Data API v3 key chahiye:

1. [console.cloud.google.com](https://console.cloud.google.com) pe jao aur login karo
2. Naya project banao (upar left "Select Project" → "New Project")
3. Left menu se "APIs & Services" → "Library" → search karo **"YouTube Data API v3"** → Enable dabao
4. "APIs & Services" → "Credentials" → "Create Credentials" → "API Key"
5. Jo key mile, usko copy karo
6. `index.html` file kholo, andar `YT_API_KEY = "PASTE_YOUR_YOUTUBE_API_KEY_HERE"` dhundo aur apni key paste karo
7. File save karke GitHub pe push karo

**Free quota:** Google roz 10,000 units free deta hai, ek search ~100 units leti hai — matlab roz ~100 searches free (kaafi hai normal use ke liye).

## Deploy kaise kare (Vercel + GitHub)

1. API key daalne ke baad, is folder ko apne GitHub repo mein upload karo
2. [vercel.com](https://vercel.com) pe jao → "Add New Project" → apna GitHub repo select karo
3. Framework preset: **Other** (kyunki yeh plain HTML hai)
4. Deploy dabao — bas 30 second mein live ho jayega

## Tech Stack

- Vanilla HTML / CSS / JavaScript (koi framework nahi)
- YouTube IFrame Player API
- kvdb.io (realtime sync backend, keyless)

## Note

- Agar kabhi kvdb.io down ho ya rate-limit lage, toh sync backend easily kisi aur keyless KV service se replace ho sakta hai (jaise jsonbin.io) — sirf `KV_BASE` variable change karna hoga script mein.
- Yeh app kisi bhi public YouTube video/song ke saath kaam karta hai.

---

Built with ❤️ by **Lokesh Patel** — Lopa Studios
