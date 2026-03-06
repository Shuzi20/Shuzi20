<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Shruti Bhanot — AI Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;500;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0e1a;
    --surface: #0f1629;
    --card: #131c35;
    --border: #1e2d52;
    --cyan: #00d4ff;
    --purple: #7c3aed;
    --pink: #f472b6;
    --green: #10b981;
    --yellow: #fbbf24;
    --text: #e2e8f0;
    --muted: #64748b;
    --accent2: #818cf8;
  }
  * { margin: 0; padding: 0; box-sizing: border-box; }
  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,212,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .layout {
    display: grid;
    grid-template-columns: 1fr 400px;
    min-height: 100vh;
    max-width: 1200px;
    margin: 0 auto;
    gap: 0;
    position: relative;
    z-index: 1;
  }

  /* ── LEFT PROFILE PANEL ── */
  .profile-panel {
    padding: 40px 40px 80px;
    border-right: 1px solid var(--border);
    overflow-y: auto;
  }

  .hero { text-align: center; padding: 40px 0 30px; position: relative; }
  .hero-glow {
    position: absolute; top: 0; left: 50%;
    transform: translateX(-50%);
    width: 400px; height: 200px;
    background: radial-gradient(ellipse, rgba(0,212,255,0.1) 0%, transparent 70%);
    pointer-events: none;
  }
  .avatar-ring {
    width: 80px; height: 80px; margin: 0 auto 16px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--cyan), var(--purple), var(--pink));
    padding: 3px; animation: rotateGrad 4s linear infinite;
  }
  @keyframes rotateGrad {
    0%   { filter: hue-rotate(0deg); }
    100% { filter: hue-rotate(360deg); }
  }
  .avatar-inner {
    width: 100%; height: 100%; border-radius: 50%;
    background: var(--bg);
    display: flex; align-items: center; justify-content: center;
    font-size: 30px;
  }
  .hero h1 {
    font-family: 'Syne', sans-serif; font-size: 2.2rem; font-weight: 800;
    background: linear-gradient(135deg, #fff 30%, var(--cyan));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text; letter-spacing: -1px;
  }
  .hero-role { margin-top: 8px; font-size: 0.75rem; color: var(--cyan); letter-spacing: 4px; text-transform: uppercase; }
  .hero-tagline { margin-top: 12px; color: var(--muted); font-size: 0.75rem; line-height: 1.7; }
  .badge-row { display: flex; flex-wrap: wrap; gap: 6px; justify-content: center; margin-top: 18px; }
  .badge {
    padding: 4px 12px; border-radius: 6px; font-size: 0.65rem;
    font-weight: 500; border: 1px solid; letter-spacing: 1px; text-transform: uppercase;
  }
  .badge-cyan { background: rgba(0,212,255,0.08); border-color: rgba(0,212,255,0.4); color: var(--cyan); }
  .badge-purple { background: rgba(124,58,237,0.08); border-color: rgba(124,58,237,0.4); color: var(--accent2); }
  .badge-pink { background: rgba(244,114,182,0.08); border-color: rgba(244,114,182,0.4); color: var(--pink); }
  .badge-green { background: rgba(16,185,129,0.08); border-color: rgba(16,185,129,0.4); color: var(--green); }

  .section { margin-top: 36px; }
  .section-label {
    font-size: 0.65rem; letter-spacing: 4px; text-transform: uppercase;
    color: var(--cyan); margin-bottom: 14px;
    display: flex; align-items: center; gap: 10px;
  }
  .section-label::after { content: ''; flex: 1; height: 1px; background: linear-gradient(90deg, var(--border), transparent); }

  /* Stats */
  .stats-row { display: grid; grid-template-columns: repeat(4, 1fr); gap: 10px; }
  .stat-card {
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 10px; padding: 14px 10px; text-align: center;
    transition: all 0.2s;
  }
  .stat-card:hover { border-color: var(--cyan); box-shadow: 0 4px 20px rgba(0,212,255,0.08); }
  .stat-num { font-family: 'Syne', sans-serif; font-size: 1.3rem; font-weight: 800; color: var(--cyan); }
  .stat-label { font-size: 0.6rem; color: var(--muted); margin-top: 4px; letter-spacing: 1px; text-transform: uppercase; }

  /* Skills */
  .skill-group { margin-bottom: 16px; }
  .skill-group-title { font-size: 0.65rem; letter-spacing: 3px; text-transform: uppercase; color: var(--muted); margin-bottom: 8px; }
  .pills { display: flex; flex-wrap: wrap; gap: 6px; }
  .pill {
    padding: 4px 10px; border-radius: 20px; font-size: 0.68rem;
    border: 1px solid var(--border); background: var(--card); color: var(--text);
    display: flex; align-items: center; gap: 5px; transition: all 0.2s;
  }
  .pill:hover { border-color: var(--cyan); color: var(--cyan); background: rgba(0,212,255,0.06); }
  .pill .dot { width: 6px; height: 6px; border-radius: 50%; }

  /* Projects */
  .project-grid { display: grid; gap: 12px; }
  .project-card {
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 10px; padding: 18px 20px;
    position: relative; overflow: hidden; transition: all 0.25s;
  }
  .project-card:hover { border-color: var(--cyan); transform: translateY(-2px); box-shadow: 0 8px 30px rgba(0,212,255,0.08); }
  .project-card::before {
    content: ''; position: absolute; top: 0; left: 0;
    width: 3px; height: 100%;
    background: linear-gradient(180deg, var(--cyan), var(--purple));
  }
  .project-name { font-family: 'Syne', sans-serif; font-size: 0.88rem; font-weight: 700; color: #fff; margin-bottom: 6px; }
  .project-desc { color: var(--muted); font-size: 0.72rem; line-height: 1.6; margin-bottom: 10px; }
  .project-stack { display: flex; flex-wrap: wrap; gap: 5px; }
  .tag { padding: 2px 8px; border-radius: 4px; font-size: 0.65rem; font-weight: 500; }
  .tag-c { background: rgba(0,212,255,0.12); color: var(--cyan); }
  .tag-p { background: rgba(124,58,237,0.12); color: var(--accent2); }
  .tag-g { background: rgba(16,185,129,0.12); color: var(--green); }
  .tag-y { background: rgba(251,191,36,0.12); color: var(--yellow); }
  .tag-k { background: rgba(244,114,182,0.12); color: var(--pink); }

  /* Experience */
  .timeline { position: relative; padding-left: 20px; }
  .timeline::before {
    content: ''; position: absolute; left: 0; top: 6px; bottom: 0;
    width: 1px; background: linear-gradient(180deg, var(--cyan), var(--purple), transparent);
  }
  .timeline-item {
    position: relative; margin-bottom: 14px; padding: 14px 16px;
    background: var(--surface); border: 1px solid var(--border); border-radius: 10px;
  }
  .timeline-item::before {
    content: ''; position: absolute; left: -24px; top: 18px;
    width: 7px; height: 7px; border-radius: 50%;
    background: var(--cyan); box-shadow: 0 0 8px var(--cyan);
  }
  .exp-header { display: flex; justify-content: space-between; flex-wrap: wrap; gap: 4px; margin-bottom: 2px; }
  .exp-title { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 0.85rem; color: #fff; }
  .exp-date { font-size: 0.65rem; color: var(--cyan); letter-spacing: 1px; }
  .exp-company { font-size: 0.7rem; color: var(--muted); margin-bottom: 8px; }
  .exp-one { font-size: 0.72rem; color: var(--text); opacity: 0.8; line-height: 1.6; padding-left: 12px; position: relative; }
  .exp-one::before { content: '▸'; position: absolute; left: 0; color: var(--cyan); font-size: 0.65rem; }

  /* ── RIGHT CHAT PANEL ── */
  .chat-panel {
    display: flex; flex-direction: column;
    height: 100vh; position: sticky; top: 0;
    background: var(--surface);
  }

  .chat-header {
    padding: 20px 24px 16px;
    border-bottom: 1px solid var(--border);
    background: var(--card);
  }
  .chat-header-top { display: flex; align-items: center; gap: 10px; margin-bottom: 4px; }
  .ai-dot {
    width: 8px; height: 8px; border-radius: 50%; background: var(--green);
    box-shadow: 0 0 8px var(--green); animation: pulse 2s ease-in-out infinite;
  }
  @keyframes pulse { 0%,100%{opacity:1;} 50%{opacity:0.4;} }
  .chat-title { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 0.95rem; color: #fff; }
  .chat-subtitle { font-size: 0.68rem; color: var(--muted); }

  .chat-messages {
    flex: 1; overflow-y: auto; padding: 20px 16px;
    display: flex; flex-direction: column; gap: 14px;
    scrollbar-width: thin; scrollbar-color: var(--border) transparent;
  }

  .msg { display: flex; gap: 10px; animation: fadeUp 0.3s ease; }
  @keyframes fadeUp { from { opacity:0; transform: translateY(8px); } to { opacity:1; transform: translateY(0); } }

  .msg-bot { align-items: flex-start; }
  .msg-user { align-items: flex-start; flex-direction: row-reverse; }

  .msg-avatar {
    width: 28px; height: 28px; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 13px; flex-shrink: 0;
  }
  .msg-avatar-bot { background: linear-gradient(135deg, var(--cyan), var(--purple)); }
  .msg-avatar-user { background: var(--card); border: 1px solid var(--border); }

  .msg-bubble {
    max-width: 78%; padding: 10px 14px; border-radius: 12px;
    font-size: 0.76rem; line-height: 1.65;
  }
  .msg-bubble-bot { background: var(--card); border: 1px solid var(--border); color: var(--text); border-radius: 2px 12px 12px 12px; }
  .msg-bubble-user { background: rgba(0,212,255,0.1); border: 1px solid rgba(0,212,255,0.25); color: var(--text); border-radius: 12px 2px 12px 12px; }

  .typing-indicator { display: flex; gap: 4px; align-items: center; padding: 4px 0; }
  .typing-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--cyan); animation: typingBounce 1.2s ease infinite; }
  .typing-dot:nth-child(2) { animation-delay: 0.2s; }
  .typing-dot:nth-child(3) { animation-delay: 0.4s; }
  @keyframes typingBounce { 0%,60%,100%{transform:translateY(0)} 30%{transform:translateY(-6px)} }

  /* Quick chips */
  .quick-chips {
    padding: 10px 16px;
    display: flex; flex-wrap: wrap; gap: 6px;
    border-top: 1px solid var(--border);
  }
  .chip {
    padding: 5px 12px; border-radius: 20px; font-size: 0.68rem;
    background: var(--card); border: 1px solid var(--border);
    color: var(--muted); cursor: pointer; transition: all 0.2s;
  }
  .chip:hover { border-color: var(--cyan); color: var(--cyan); background: rgba(0,212,255,0.06); }

  /* Input */
  .chat-input-area {
    padding: 12px 16px 16px;
    border-top: 1px solid var(--border);
    background: var(--card);
  }
  .input-row { display: flex; gap: 8px; }
  .chat-input {
    flex: 1; background: var(--surface); border: 1px solid var(--border);
    border-radius: 8px; padding: 10px 14px; font-family: 'JetBrains Mono', monospace;
    font-size: 0.75rem; color: var(--text); outline: none; transition: border 0.2s;
  }
  .chat-input:focus { border-color: var(--cyan); }
  .chat-input::placeholder { color: var(--muted); }
  .send-btn {
    padding: 10px 16px; border-radius: 8px; border: none;
    background: linear-gradient(135deg, var(--cyan), var(--purple));
    color: #fff; font-size: 0.8rem; cursor: pointer;
    transition: opacity 0.2s; font-family: 'JetBrains Mono', monospace;
  }
  .send-btn:hover { opacity: 0.85; }
  .send-btn:disabled { opacity: 0.4; cursor: not-allowed; }

  @media (max-width: 768px) {
    .layout { grid-template-columns: 1fr; }
    .chat-panel { height: 70vh; position: relative; }
    .profile-panel { padding: 24px 16px; }
    .stats-row { grid-template-columns: repeat(2, 1fr); }
  }
</style>
</head>
<body>
<div class="layout">

  <!-- LEFT: PROFILE -->
  <div class="profile-panel">
    <div class="hero">
      <div class="hero-glow"></div>
      <div class="avatar-ring"><div class="avatar-inner">🤖</div></div>
      <h1>Shruti Bhanot</h1>
      <div class="hero-role">AI Engineer · ML · NLP · Voice AI</div>
      <p class="hero-tagline">Building intelligent systems that think, learn, and act</p>
      <div class="badge-row">
        <span class="badge badge-cyan">LLM Agents</span>
        <span class="badge badge-purple">RAG Systems</span>
        <span class="badge badge-pink">Voice AI</span>
        <span class="badge badge-green">Semantic Search</span>
      </div>
    </div>

    <div class="section">
      <div class="section-label">Impact</div>
      <div class="stats-row">
        <div class="stat-card"><div class="stat-num">100K+</div><div class="stat-label">Records/day</div></div>
        <div class="stat-card"><div class="stat-num">6.3M</div><div class="stat-label">ML rows</div></div>
        <div class="stat-card"><div class="stat-num">85%</div><div class="stat-label">AI accuracy</div></div>
        <div class="stat-card"><div class="stat-num">60%</div><div class="stat-label">Time saved</div></div>
      </div>
    </div>

    <div class="section">
      <div class="section-label">Tech Stack</div>
      <div class="skill-group">
        <div class="skill-group-title">🧠 AI / LLM</div>
        <div class="pills">
          <span class="pill"><span class="dot" style="background:#00d4ff"></span>LangChain</span>
          <span class="pill"><span class="dot" style="background:#7c3aed"></span>LLaMA 3 / Groq</span>
          <span class="pill"><span class="dot" style="background:#f472b6"></span>Hugging Face</span>
          <span class="pill"><span class="dot" style="background:#10b981"></span>BERT</span>
          <span class="pill"><span class="dot" style="background:#fbbf24"></span>Qdrant</span>
          <span class="pill"><span class="dot" style="background:#818cf8"></span>Azure ML</span>
          <span class="pill"><span class="dot" style="background:#00d4ff"></span>Scikit-learn</span>
          <span class="pill"><span class="dot" style="background:#f472b6"></span>TensorFlow</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-title">⚙️ Backend</div>
        <div class="pills">
          <span class="pill"><span class="dot" style="background:#00d4ff"></span>Python</span>
          <span class="pill"><span class="dot" style="background:#10b981"></span>FastAPI</span>
          <span class="pill"><span class="dot" style="background:#818cf8"></span>Django</span>
          <span class="pill"><span class="dot" style="background:#f472b6"></span>JWT / OAuth</span>
          <span class="pill"><span class="dot" style="background:#00d4ff"></span>Azure Functions</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-title">🗄️ Data & Cloud</div>
        <div class="pills">
          <span class="pill"><span class="dot" style="background:#00d4ff"></span>PostgreSQL</span>
          <span class="pill"><span class="dot" style="background:#10b981"></span>MySQL</span>
          <span class="pill"><span class="dot" style="background:#f472b6"></span>AWS S3 / Lambda</span>
          <span class="pill"><span class="dot" style="background:#fbbf24"></span>Pandas / NumPy</span>
          <span class="pill"><span class="dot" style="background:#818cf8"></span>Streamlit</span>
          <span class="pill"><span class="dot" style="background:#00d4ff"></span>Next.js</span>
        </div>
      </div>
    </div>

    <div class="section">
      <div class="section-label">Experience</div>
      <div class="timeline">
        <div class="timeline-item">
          <div class="exp-header">
            <div class="exp-title">AI Engineer</div>
            <div class="exp-date">NOV 2025 – JAN 2026</div>
          </div>
          <div class="exp-company">Interbiz Consulting · InsurTech</div>
          <div class="exp-one">Production AI voice agent for IVR — Azure Functions + Azure ML, real-time NLP call routing</div>
        </div>
        <div class="timeline-item">
          <div class="exp-header">
            <div class="exp-title">AI / Backend Intern</div>
            <div class="exp-date">DEC 2024 – JUN 2025</div>
          </div>
          <div class="exp-company">90 North Software · PropTech</div>
          <div class="exp-one">FastAPI + LLM chatbot backend · ETL pipelines processing 100K+ records/day</div>
        </div>
      </div>
    </div>

    <div class="section">
      <div class="section-label">Featured Projects</div>
      <div class="project-grid">
        <div class="project-card">
          <div class="project-name">🤖 AI Interview Assistant</div>
          <div class="project-desc">BERT-powered semantic answer evaluation (85% accuracy), video/audio capture, AWS S3 storage.</div>
          <div class="project-stack">
            <span class="tag tag-p">Django</span>
            <span class="tag tag-c">BERT</span>
            <span class="tag tag-g">Next.js</span>
            <span class="tag tag-k">AWS S3</span>
          </div>
        </div>
        <div class="project-card">
          <div class="project-name">💬 Document Theme Chatbot</div>
          <div class="project-desc">RAG chatbot — 75+ PDFs via Qdrant vectors, LLaMA 3 through Groq, traceable citations.</div>
          <div class="project-stack">
            <span class="tag tag-c">LLaMA 3</span>
            <span class="tag tag-p">LangChain</span>
            <span class="tag tag-g">Qdrant</span>
            <span class="tag tag-y">FastAPI</span>
          </div>
        </div>
        <div class="project-card">
          <div class="project-name">📊 Skylark BI Agent</div>
          <div class="project-desc">LLM agent answering founder-level queries on deal pipeline via Monday.com API + Groq Llama 3.3.</div>
          <div class="project-stack">
            <span class="tag tag-c">Groq Llama 3.3</span>
            <span class="tag tag-p">LLM Agent</span>
            <span class="tag tag-y">Python</span>
          </div>
        </div>
        <div class="project-card">
          <div class="project-name">📰 News Summarizer + Hindi TTS</div>
          <div class="project-desc">End-to-end NLP: live news → VADER sentiment → KeyBERT → Hindi audio via gTTS on Streamlit.</div>
          <div class="project-stack">
            <span class="tag tag-c">VADER</span>
            <span class="tag tag-p">KeyBERT</span>
            <span class="tag tag-g">gTTS</span>
            <span class="tag tag-k">Streamlit</span>
          </div>
        </div>
        <div class="project-card">
          <div class="project-name">🔐 Fraud Detection — 6.3M Records</div>
          <div class="project-desc">ML model achieving 100% recall and 0.9999 ROC-AUC on 6.3M financial transactions.</div>
          <div class="project-stack">
            <span class="tag tag-c">ML</span>
            <span class="tag tag-p">Scikit-learn</span>
            <span class="tag tag-y">Python</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- RIGHT: AI CHAT PANEL -->
  <div class="chat-panel">
    <div class="chat-header">
      <div class="chat-header-top">
        <div class="ai-dot"></div>
        <div class="chat-title">Ask about Shruti</div>
      </div>
      <div class="chat-subtitle">AI assistant trained on her profile · Ask anything!</div>
    </div>

    <div class="chat-messages" id="chatMessages">
      <div class="msg msg-bot">
        <div class="msg-avatar msg-avatar-bot">🤖</div>
        <div class="msg-bubble msg-bubble-bot">
          Hey! 👋 I'm Shruti's AI assistant. Ask me anything about her — projects, skills, experience, or what kind of roles she's looking for!
        </div>
      </div>
    </div>

    <div class="quick-chips" id="quickChips">
      <span class="chip" onclick="sendChip(this)">How many AI projects?</span>
      <span class="chip" onclick="sendChip(this)">What's her stack?</span>
      <span class="chip" onclick="sendChip(this)">Experience summary</span>
      <span class="chip" onclick="sendChip(this)">Is she open to work?</span>
      <span class="chip" onclick="sendChip(this)">Data vs AI projects?</span>
    </div>

    <div class="chat-input-area">
      <div class="input-row">
        <input class="chat-input" id="chatInput" type="text" placeholder="Ask anything about Shruti..." onkeydown="if(event.key==='Enter') sendMessage()" />
        <button class="send-btn" id="sendBtn" onclick="sendMessage()">Send →</button>
      </div>
    </div>
  </div>
</div>

<script>
const PROFILE_CONTEXT = `
You are an AI assistant embedded in Shruti Bhanot's developer portfolio/GitHub profile page.
Answer questions about her in a friendly, concise, first-person-about-her style (refer to her as "Shruti" or "she").

Here is everything about Shruti:

NAME: Shruti Bhanot
ROLE: AI Engineer
GITHUB: github.com/Shuzi20
EMAIL: bhanot.shruti.20@gmail.com
EXPERIENCE: 10 months building AI systems in InsurTech and PropTech domains.

EDUCATION: 
- Master of Computer Science, St. Aloysius College Jabalpur (2022–2024, 70%)
- Bachelor of Science, St. Aloysius College Jabalpur (2019–2022, 71.64%)

WORK EXPERIENCE:
1. AI Engineer — Interbiz Consulting Pvt Ltd (Nov 2025 – Jan 2026) [InsurTech]
   - Deployed production AI voice agent for IVR using Azure Functions and Azure ML
   - Real-time call routing and NLP, evaluated VAPI/Logic Apps architectures
   
2. Data Analyst Intern / AI Backend Engineer — 90 North Software Limited (Dec 2024 – Jun 2025) [PropTech]
   - Built FastAPI backend for AI chatbot with LLM integration + semantic search
   - Automated ETL pipelines processing 100,000+ records/day, reduced manual work by 60%

SKILLS:
- AI/ML/LLM: LangChain, LLaMA 3, Groq, Hugging Face Transformers, BERT, Qdrant (Vector DB), Scikit-learn, TensorFlow, VADER NLP, KeyBERT, gTTS, Azure ML, Vector Embeddings
- Backend: Python, FastAPI, Django, JWT/OAuth, Azure Functions
- Data: PostgreSQL, MySQL, AWS S3/Lambda, Pandas, NumPy, Feature Engineering
- Frontend/Apps: Streamlit, Next.js, React
- Tools: Git, Postman, Jira, Jupyter

PROJECTS (Total: 10 public repositories, 16 total):

AI-RELATED PROJECTS (6):
1. AI Interview Assistant Platform — Django, Next.js, BERT, Hugging Face, PostgreSQL, AWS S3
   - Full-stack mock interview platform, BERT semantic evaluation with 85% accuracy, JWT + Google OAuth
   
2. Document Theme Chatbot — FastAPI, LLaMA 3, Qdrant, LangChain, Next.js
   - RAG chatbot for 75+ PDFs, vector embeddings, traceable citations, dual output formats
   
3. Skylark BI Agent — Python, Groq Llama 3.3, Monday.com API, MIT License
   - LLM-powered BI agent for founder-level business queries on deal pipeline and work orders
   
4. News Summarization + Hindi TTS App — Streamlit, GNews API, VADER, KeyBERT, gTTS
   - Real-time NLP pipeline: fetch → sentiment analysis → keyword extraction → Hindi audio

5. me-api-playground — Python, FastAPI, SQLite/PostgreSQL, React
   - Full-stack developer profile management app
   
6. Ai_Interview — TypeScript (another AI interview related project)

DATA SCIENCE / ML PROJECTS (5):
1. Fraud Detection in Financial Transactions — 6.3M records, XGBoost, 100% recall, 0.9999 ROC-AUC
2. Customer Lifetime Value (CLV) Analysis — Ridge Regression, R²=1.0, FLO e-commerce
3. Customer Segmentation — Clustering, Jupyter Notebook
4. Product Affinity Analysis — Apriori algorithm, association rule mining, e-commerce
5. Customer Sentiment Analysis — VADER + Logistic Regression + Random Forest + XGBoost
6. Time-on-site Analysis — session analysis, bounce rates, A/B testing, heatmaps
7. Customer Acquisition Cost Analysis — CAC, LTV, marketing campaign effectiveness
8. Business Intelligence Reporting — Power BI dashboards, Revenue $44.34M, Profit $43.09M
9. Stock Data of Tesla and Gamestop — Jupyter Notebook

CERTIFICATIONS:
- Power BI for Data Analyst (VOIS)
- Machine Learning (Udemy)
- Advanced Excel (Udemy)

STATS:
- 228 GitHub contributions in last year
- 16 repositories total
- ~6 AI/LLM focused projects
- ~9 Data Science/ML/Analytics projects

She is actively building AI-driven products and is eager to grow within a strong engineering team.
She is particularly interested in: Agentic AI, RAG pipelines, MLOps on AWS, Multilingual NLP.

Keep answers SHORT (2-4 sentences max unless a list is genuinely helpful).
Use emojis occasionally to stay friendly.
If asked about contact, share: bhanot.shruti.20@gmail.com and github.com/Shuzi20
`;

let conversationHistory = [];

async function sendMessage() {
  const input = document.getElementById('chatInput');
  const msg = input.value.trim();
  if (!msg) return;
  input.value = '';
  addMessage(msg, 'user');
  await getBotResponse(msg);
}

function sendChip(el) {
  const msg = el.textContent;
  addMessage(msg, 'user');
  getBotResponse(msg);
}

function addMessage(text, role) {
  const container = document.getElementById('chatMessages');
  const div = document.createElement('div');
  div.className = `msg msg-${role === 'user' ? 'user' : 'bot'}`;
  div.innerHTML = `
    <div class="msg-avatar msg-avatar-${role === 'user' ? 'user' : 'bot'}">${role === 'user' ? '👤' : '🤖'}</div>
    <div class="msg-bubble msg-bubble-${role === 'user' ? 'user' : 'bot'}">${text}</div>
  `;
  container.appendChild(div);
  container.scrollTop = container.scrollHeight;
}

function addTyping() {
  const container = document.getElementById('chatMessages');
  const div = document.createElement('div');
  div.className = 'msg msg-bot';
  div.id = 'typingIndicator';
  div.innerHTML = `
    <div class="msg-avatar msg-avatar-bot">🤖</div>
    <div class="msg-bubble msg-bubble-bot">
      <div class="typing-indicator">
        <div class="typing-dot"></div>
        <div class="typing-dot"></div>
        <div class="typing-dot"></div>
      </div>
    </div>
  `;
  container.appendChild(div);
  container.scrollTop = container.scrollHeight;
}

function removeTyping() {
  const el = document.getElementById('typingIndicator');
  if (el) el.remove();
}

async function getBotResponse(userMsg) {
  const sendBtn = document.getElementById('sendBtn');
  sendBtn.disabled = true;
  addTyping();

  conversationHistory.push({ role: 'user', content: userMsg });

  try {
    const response = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        model: 'claude-sonnet-4-20250514',
        max_tokens: 1000,
        system: PROFILE_CONTEXT,
        messages: conversationHistory
      })
    });

    const data = await response.json();
    const reply = data.content?.[0]?.text || "Sorry, I couldn't fetch a response right now!";
    
    conversationHistory.push({ role: 'assistant', content: reply });
    removeTyping();
    addMessage(reply, 'bot');
  } catch (err) {
    removeTyping();
    addMessage("Oops! Something went wrong. Try again 🙏", 'bot');
  }

  sendBtn.disabled = false;
  document.getElementById('chatInput').focus();
}
</script>
</body>
</html>
