# Main Character OS ⚔️ — OpenAI Version

> Your life is an RPG. Time to actually play it.

---

## ⚡ Deploy in 5 minutes

```bash
# 1. Install
npm install

# 2. Set your key
cp .env.example .env.local
# Edit .env.local → paste your OPENAI_API_KEY

# 3. Run
npm run dev
# → http://localhost:3000

# 4. Deploy to Vercel
npx vercel
# Add OPENAI_API_KEY in Vercel dashboard → Settings → Environment Variables
```

---

## 🔑 API key

Get your OpenAI key at **[platform.openai.com/api-keys](https://platform.openai.com/api-keys)**

You need a funded account (add $5–10 credit). The app uses:

| API call | Model | Est. cost per call |
|----------|-------|-------------------|
| Character creation | gpt-4o | ~$0.01 |
| Life audit | gpt-4o | ~$0.015 |
| Karaoke | gpt-4o | ~$0.015 |
| Startup forge | gpt-4o | ~$0.02 |
| Voice (TTS) | tts-1 | ~$0.002 |

A full demo session costs roughly **$0.10 total**.

---

## 🎮 Modes

| Mode | What it does |
|------|-------------|
| ⚔️ Quest | Voice/text input → RPG character class + quest board |
| 🔥 Life Audit | Upload screenshots or paste data → brutal roast + 7-day plan |
| 🎵 Karaoke | Vent about your day → AI turns it into a song + CBT card |
| 🚀 Startup Forge | Dumb idea → full pitch + VC roast + landing page copy |

---

## 🔊 Voice

**Voice input** uses the browser's built-in Web Speech API. Works in Chrome and Edge.

**Voice output** uses **OpenAI TTS** (`tts-1` model, `onyx` voice) — no extra key needed, it uses your `OPENAI_API_KEY`. Falls back to browser speechSynthesis if TTS fails.

To change the voice, edit `app/api/speak/route.ts` and change `voice` to one of:
`alloy` | `echo` | `fable` | `onyx` | `nova` | `shimmer`

---

## 📁 Files

```
app/
├── page.tsx              # Full UI
├── layout.tsx
├── globals.css
└── api/
    ├── quest/route.ts    # gpt-4o character creation
    ├── audit/route.ts    # gpt-4o vision + life audit
    ├── karaoke/route.ts  # gpt-4o therapy karaoke
    ├── startup/route.ts  # gpt-4o startup validation
    └── speak/route.ts    # OpenAI TTS (tts-1)
```

---

## 🐛 Troubleshooting

**"Failed to create character"** → Check `OPENAI_API_KEY` in `.env.local`, make sure the key has credits

**"Insufficient quota"** → Add credit at [platform.openai.com/settings/billing](https://platform.openai.com/settings/billing)

**Voice input not working** → Use Chrome or Edge (Firefox doesn't support Web Speech API)

**Image upload not working in audit** → Make sure files are JPG/PNG under 20MB
