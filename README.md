# AI Map Reporter — ArcGIS Maps SDK for JavaScript 5.0

> **⚡ Uses the brand new `arcgis-assistant` AI component (beta) — released February 2026**

Ask natural language questions about your web map data. The AI agent answers, the map responds, and the browser **speaks the answer aloud** via the Web Speech API.

---

## What makes this unique

This is the **first community sample** that combines the new `arcgis-assistant` AI component (SDK 5.0 beta) with browser `SpeechSynthesis` — creating a fully voice-narrated AI map experience. The official Esri sample shows the assistant UI alone. This adds:

| Addition | Why it matters |
|----------|---------------|
| 🔊 Voice narration toggle | Speaks every AI response aloud via Web Speech API |
| 📋 Transcript sidebar | Logs the full conversation history on the left panel |
| ↗ Suggested prompts | One-click example queries to demonstrate AI capabilities |
| ⚠ Graceful credential gate | Works as a UI demo without credentials; activates fully when configured |

---

## APIs & Concepts Demonstrated

```javascript
// SDK 5.0 — single script tag loads everything
<script type="module" src="https://js.arcgis.com/5.0/"></script>

// AI components — arcgis-assistant web component
<arcgis-assistant id="ai-assistant"></arcgis-assistant>

// Register the Data Exploration Agent
const agent = new DataExplorationAgent({ view });
assistant.agents = [agent];

// Listen for AI responses
assistant.addEventListener("arcgisAssistantMessage", (e) => {
  speak(e.detail.content); // Web Speech API
});

// Browser Speech Synthesis
const utterance = new SpeechSynthesisUtterance(text);
window.speechSynthesis.speak(utterance);
```

---

## Setup — Add Your Credentials

Open `index.html` and fill in the `CONFIG` block near the top of the `<script>` section:

```javascript
const CONFIG = {
  portalUrl:  "https://YOUR_ORG.maps.arcgis.com",  // your ArcGIS Online org URL
  oauthAppId: "YOUR_CLIENT_ID",                     // OAuth app Client ID
  webMapId:   "YOUR_WEBMAP_ITEM_ID",                // web map item ID in your org
};
```

### Requirements

| Requirement | Details |
|-------------|---------|
| ArcGIS Online account | **Named user** in an org — not trial, not public |
| OAuth app registered | Register at [developers.arcgis.com](https://developers.arcgis.com) → add your redirect URI |
| Web map with feature layers | Any web map from your org — works best with layers that have rich attributes |

> **Note:** API keys cannot currently be used with AI components. A signed-in named user with the necessary org privileges is required. This is a beta limitation Esri is actively evaluating.

---

## How to run

No build step required. Open `index.html` in a browser:

```bash
# Simple local server
npx serve .
# or
python -m http.server 8000
```

Without credentials: the UI, voice toggle, transcript panel, and suggested prompts all work — the AI agent chat panel is hidden until credentials are configured.

With credentials: sign in with your ArcGIS Online account when prompted → the full AI agent activates.

---

## Example prompts to try

- *"What city has the largest population?"*
- *"How many cities are in California?"*
- *"Show only cities with population over 500,000"*
- *"What cities are within 50 miles of Chicago?"*
- *"Zoom to the state of Texas"*

---

## SDK Version

ArcGIS Maps SDK for JavaScript **5.0** (CDN) — AI Components **beta**

> ⚡ SDK 5.0 was released **February 2026**. The AI components package was announced **February 24, 2026**. This sample was built in **March 2026** — one of the earliest community contributions using this API.

---

## Author

Ariful Islam — Support Analyst II, Esri Developer Products
[portfolio-o58a.vercel.app](https://portfolio-o58a.vercel.app)
