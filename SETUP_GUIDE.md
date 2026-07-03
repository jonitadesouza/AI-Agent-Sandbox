# How to Run Smart Tech Navigator
### Complete beginner's guide — zero coding experience needed

---

## What you need (5 things)

1. A laptop or desktop computer
2. Google Chrome browser (download from google.com/chrome if you don't have it)
3. An Anthropic API key (free to get — instructions below)
4. The `index.html` file from this folder
5. A text editor — Notepad (Windows) or TextEdit (Mac) works fine

That's it. No installation. No server. No coding.

---

## Step 1 — Get your Anthropic API key (5 minutes)

1. Go to **console.anthropic.com** in your browser
2. Click **Sign Up** (or Log In if you have an account)
3. Once logged in, click **API Keys** in the left menu
4. Click **Create Key**
5. Give it a name like "STN Demo"
6. Copy the key — it looks like: `sk-ant-api03-xxxxxxxxxxxxxxxx`
7. **Paste it somewhere safe** — you'll need it in the next step

> ⚠️ Free tier gives you $5 of credits — enough for 50+ demo runs.

---

## Step 2 — Add your API key to the app (2 minutes)

1. Find the `index.html` file in this folder
2. Right-click it → Open With → Notepad (Windows) or TextEdit (Mac)
3. Press **Ctrl+F** (or Cmd+F on Mac) to open Find
4. Search for: `'Content-Type': 'application/json'`
5. You'll see this block of code a few lines above it:

```javascript
const res = await fetch('https://api.anthropic.com/v1/messages', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
```

6. Add your API key line so it looks like this:

```javascript
const res = await fetch('https://api.anthropic.com/v1/messages', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'x-api-key': 'sk-ant-api03-YOUR-KEY-HERE',
    'anthropic-version': '2023-06-01',
    'anthropic-dangerous-direct-browser-access': 'true'
  },
```

7. Replace `sk-ant-api03-YOUR-KEY-HERE` with your actual key
8. Save the file (Ctrl+S or Cmd+S)

---

## Step 3 — Open the app (30 seconds)

1. Double-click `index.html`
2. It opens in Google Chrome
3. You should see the Smart Tech Navigator interface

That's it. The app is running.

---

## Step 4 — Run your first demo

1. Click any of the three scenario buttons on the left panel
2. You'll see the business description fill in automatically
3. Click the purple **"Analyse & Recommend"** button
4. Watch the agent reasoning log appear on the right
5. In about 15–30 seconds, your full recommendation report appears

### What you're seeing:
- **Agent log (dark box at top):** The three AI agents talking to each other
- **Extracted requirements card:** What the AI understood from the business description
- **Vendor scorecard:** Ranked vendors with scores
- **Risk assessment:** Overall risk level and what to watch for
- **Implementation Gantt:** Phase-by-phase rollout timeline

---

## Step 5 — Try your own scenario

1. Clear the text area and type your own business need
2. Fill in industry, company size, budget, timeline
3. Click Analyse & Recommend
4. The agent works on your custom scenario

**Example inputs to try:**
- "We are a hospital in Chennai needing patient management software, billing, and appointment scheduling. Budget ₹40 lakhs."
- "Small retail chain with 12 stores needs POS system with inventory sync and loyalty programme. Budget ₹8 lakhs."
- "Law firm of 25 lawyers needs document management, time tracking, and billing. Budget ₹5 lakhs."

---

## Common problems and fixes

**"The button does nothing"**
→ Check that you added the API key correctly in Step 2. Make sure there are no extra spaces.

**"I see an error message"**
→ Your API key might be wrong or your free credits are used up. Go back to console.anthropic.com to check.

**"The page looks broken"**
→ Make sure you're opening it in Google Chrome, not Internet Explorer or Edge.

**"I can't find where to add the API key"**
→ In Notepad, press Ctrl+F and search for `x-api-key` — if it's already there, you've already done this step.

---

## For the demo / presentation

### Best setup:
- Use a laptop connected to a projector or large screen
- Browser zoom at 90% (Ctrl+- once) so everything fits nicely
- Have all three scenarios ready to show
- Pre-run scenario 1 once before your demo so you know the timing

### Talking points while it runs:
- "Watch the agent log — this is three AI agents working in sequence"
- "The intake agent just extracted structured requirements from plain English"
- "Now the research agent is identifying vendors for this specific context"
- "The analysis agent is applying weighted scoring — you can see every dimension"

### If something goes wrong during demo:
- Refresh the page and try again — it takes 15 seconds
- Have a screenshot of a completed run as backup

---

## File structure

```
STN/
├── index.html          ← The entire app (open this)
├── SETUP_GUIDE.md      ← This file
├── PROJECT_WRITEUP.md  ← Full project write-up for submission
└── VIDEO_SCRIPT.md     ← Script for your demo video
```

---

## Submission checklist

- [ ] App runs successfully with at least 2 scenarios
- [ ] API key added and working
- [ ] PROJECT_WRITEUP.md reviewed and customised with your team details
- [ ] VIDEO_SCRIPT.md used to record 3–4 minute demo video
- [ ] Screen recording software ready (OBS free, or Loom, or built-in tools)

**Windows screen record:** Press Win + G → click record
**Mac screen record:** Press Cmd + Shift + 5 → choose record option
