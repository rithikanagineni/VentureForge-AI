# ⚡ VentureForge AI

### Your AI Startup Copilot

**Turn raw startup ideas into complete, actionable business blueprints — powered by IBM Granite Foundation Models on IBM Cloud (watsonx.ai).**

---

## 📌 About The Project

**VentureForge AI** is a production-ready AI SaaS application built for the **IBM SkillsBuild Internship** (organised by Edunet Foundation) — problem statement: **Startup Blueprint Generator Agent** powered by IBM Granite Foundation Models and IBM Cloud services.

The app is an intelligent AI Startup Copilot that helps entrepreneurs move from **idea → validation → investor readiness**. Users describe their idea in simple terms, and specialized AI agents instantly produce structured business plans, pitch decks, market research, funding strategies, financial projections, and more — all generated dynamically by IBM Granite (no hardcoded responses).

### ✨ Key Highlights

- 🤖 **15+ specialized AI agents**, each with its own prompt-engineering strategy
- 🧠 **Automatic intent detection** — ask any startup question, the right agent handles it
- 📊 **Structured interactive outputs** — health score gauges, investor verdict panels, pitch deck slider, interactive roadmap timeline
- 💾 **Full persistence** — report history, saved startup projects, live search
- 📄 **One-click exports** — branded PDF reports, Markdown downloads, clipboard copy
- 🌙 **Dark / Light mode** with accent themes, compact layout, and reduced-motion support

---

## 🚀 Features

### Core AI Agents

| Agent | Description |
|---|---|
| 🔍 **Idea Validation** | Verdict, confidence score, risks & 5 validation experiments |
| 📋 **Business Plan** | Full investor-ready business plan with milestones |
| 📊 **Market Research** | TAM / SAM / SOM sizing, trends, segmentation |
| ⚔️ **Competitor Analysis** | Comparison table, positioning & white-space strategy |
| 🧭 **SWOT Analysis** | 2×2 analysis + strategic recommendations |
| 💰 **Funding Advisor** | Funding options, ticket sizes, govt schemes, roadmap |
| 📈 **Revenue Model** | Revenue streams, pricing tiers, unit economics |
| 📣 **Marketing Strategy** | Channels, 90-day launch plan, growth loops, KPIs |
| 🎤 **Investor Pitch** | 11-slide pitch outline + elevator pitch |
| 🧑 **Customer Persona** | Detailed buyer personas with pain points & triggers |
| 🗺️ **Roadmap Generator** | Phased execution plan with interactive timeline UI |
| 🧩 **Business Model Canvas** | All 9 BMC building blocks |
| ✏️ **Name Generator** | Startup names, taglines, domain notes |
| 💹 **Financial Projections** | 3-year P&L, burn rate, break-even, runway |
| ⚖️ **Legal & Compliance** | Registration, IP, data privacy, government schemes |

### 🏆 Advanced Features

| Feature | Description |
|---|---|
| 🏥 **Startup Health Score** | Strict JSON from Granite rendered as an animated circular gauge with 8 dimension bars, strengths / risks / next actions |
| 💼 **Investor Decision Simulator** | 3 investor profiles (Angel, Seed VC, Series A VC) deliver Invest / Pass / Conditional verdicts with conviction ratings, ticket sizes & probing questions |
| 📈 **Pitch Deck Generator** | 10-slide presentation with slide navigator, speaker notes, visual suggestions & Markdown export |
| 📅 **Interactive Startup Roadmap** | Clickable phase timeline with progress tracking, milestones & navigation |
| 💼 **One-click Investor Pack** | Generates 6 core investor reports in a single click (multi-agent workflow) |
| 🎯 **AI Mentor Recommendations** | Personalized next-step suggestions derived from your report history |
| 📊 **Business Health Dashboard** | Donut chart of core-report completion, weekly activity bar chart, top-agent usage breakdown |

### Platform & UX Features

- 💬 **Chat-style generation** with live typing animation
- 💾 **Saved Projects** — pin, load & delete startup profiles (PostgreSQL backed)
- 🔎 **History Search** — debounced server-side search + agent filters
- ⌨️ **Ctrl+Enter** keyboard shortcut to generate
- 🌙 **Dark mode** + 3 accent themes (Violet / Ocean / Sunset)
- 📁 Export reports as **PDF**, **Markdown**, **JSON** (history)
- 📋 Copy any response with one click
- 🛡️ Complete **error handling** — missing API key, IBM API errors, timeouts, network failures, empty prompts

---

## 🧰 Tech Stack

| Layer | Technology |
|---|---|
| **AI Model** | IBM Granite-4-h-small  |
| **AI Platform** | IBM watsonx.ai (IBM Cloud) + IAM authentication |
| **Framework** | Next.js 16 (App Router, Turbopack) |
| **Language** | TypeScript, React 19 |
| **Database** | PostgreSQL 16 + Drizzle ORM |
| **Styling** | Tailwind CSS 4 |
| **PDF Export** | jsPDF |
| **Markdown** | react-markdown + remark-gfm |

---

## 🏗️ How It Works (Agent Workflow)

```
User Prompt + Startup Profile Form
        │
        ├─── Intent Detection ───────────────► Best-fit Agent
        └─── Direct Agent (Quick Action / Advanced Button)
        │
        ▼
Agent-Specific Prompt Engineering (persona + directive + startup context)
        │
        ▼
IBM Cloud IAM ──(API key)──► Bearer Token (cached)
        │
        ▼
IBM watsonx.ai ──► IBM Granite-4-h-small text generation
        │
        ▼
JSON parsing (structured agents) / Markdown rendering (report agents)
        │
        ▼
Interactive UI + PostgreSQL persistence + PDF / MD / Copy export
```

IBM Architecture: 
               VentureForge AI

         User
           │
           ▼
     Next.js Frontend
           │
           ▼
      API Routes
           │
           ▼
 IBM watsonx.ai Runtime
           │
           ▼
 IBM Granite 4 H Small
           │
           ▼
 Structured Business Reports

---

## ⚙️ Getting Started

### 1️⃣ Prerequisites

- **Node.js v18.17+** (v20+ recommended)
- **PostgreSQL 16** — local install, Docker, or free cloud (Neon / Supabase)
- **IBM Cloud Lite account** with watsonx.ai access

### 2️⃣ Clone & Install

```bash
git clone https://github.com/<your-username>/ventureforge-ai.git
cd ventureforge-ai
npm install
```

### 3️⃣ Start PostgreSQL

```bash
# Easiest option: Docker
docker run --name vf-postgres -e POSTGRES_PASSWORD=postgres \
  -e POSTGRES_DB=app_db -p 5432:5432 -d postgres:16
```

### 4️⃣ Configure Environment

Create a `.env.local` file:

```env

WATSONX_API_KEY=your_ibm_cloud_api_key
WATSONX_PROJECT_ID=your_watsonx_project_id
WATSONX_URL=https://eu-de.ml.cloud.ibm.com
WATSONX_MODEL_ID=ibm/granite-4-h-small
```

<summary>🔑 <b>How to get IBM watsonx.ai credentials (free — IBM Cloud Lite)</b></summary>

1. Sign up at [cloud.ibm.com](https://cloud.ibm.com) (no credit card required)
2. Create an API key at `cloud.ibm.com/iam/apikeys` → **Create an IBM Cloud API key**
3. Launch [watsonx.ai](https://dataplatform.cloud.ibm.com/wx/home?context=wx)

### 5️⃣ Create Database Tables

```bash
npx drizzle-kit push
```

### 6️⃣ Run the App

```bash
npm run dev
```

Open **[http://localhost:3000](http://localhost:3000)** 🎉

---

## 📜 Available Scripts

| Command | Purpose |
|---|---|
| `npm run dev` | Start development server (hot reload) |
| `npm run build` | Production build |
| `npm run start` | Start production server |
| `npm run lint` | ESLint check |
| `npx drizzle-kit push` | Sync schema to database |
| `npx next typegen` | Regenerate Next.js route types |


---

## 💬 Example Prompts

Try asking the Copilot things like:

- *"Generate startup ideas for college students"*
- *"Validate my AI-powered fitness coaching app"*
- *"Create a full business plan for my edtech startup"*
- *"Generate an investor pitch deck for a SaaS tool"*
- *"Do a SWOT analysis for my D2C skincare brand"*
- *"What funding options and government schemes fit my ₹10L budget?"*
- *"Build financial projections with break-even analysis"*
- *"Suggest startup names and taglines for a food delivery app"*
- *"Simulate whether investors would fund my fintech idea"*
- *"Create a 12-month product roadmap"*
- *"Build customer personas for B2B sales"*
- *"What legal steps do I need to register my company in India?"*

---

## ⚠️ Error Handling

| Scenario | Behavior |
|---|---|
| **Missing IBM API key / project ID** | Clear error: IBM Granite configuration required |
| **IBM IAM authentication failure** | "Check your API key" guidance |
| **IBM Granite API error** | Status code + reason surfaced to user |
| **Timeout (45s)** | Friendly retry message |
| **No internet / network failure** | "Check your connection" — no corrupted output |
| **Empty prompt + empty form** | Validates before any API call is made |

---

## 🔮 Roadmap / Future Enhancements

- [ ] Team workspaces with shared startup projects & comments
- [ ] Streaming token-by-token responses via watsonx.ai streaming API
- [ ] RAG with real startup portals, incubator databases & policy PDFs uploaded by user
- [ ] Pitch deck export to PowerPoint (.pptx)
- [ ] Investor / incubator directory with warm-intro tracking
- [ ] Multi-language support via Granite multilingual models

---

## 🙏 Acknowledgements

- **IBM watsonx.ai** — IBM Granite 3 foundation model access
- **IBM Cloud Lite** — free tier services used in this project


**Built with ⚙️ by VentureForge AI Team · Powered by IBM Granite**

⭐ If this project helped you, please consider giving it a star!
