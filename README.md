<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pranav Sai Bhagath —   Code Style</title>
<link href="https://fonts.googleapis.com/css2?family=Berkeley+Mono:wght@400;700&family=JetBrains+Mono:ital,wght@0,300;0,400;0,500;0,700;1,400&display=swap" rel="stylesheet">
<style>
  :root {
    --bg:        #1a1a1a;
    --surface:   #212121;
    --border:    #333333;
    --border2:   #2a2a2a;
    --text:      #d4d4d4;
    --muted:     #6b6b6b;
    --accent:    #da7756;   /*   Code orange */
    --accent2:   #c96442;
    --green:     #4ec9b0;
    --blue:      #569cd6;
    --yellow:    #dcdcaa;
    --purple:    #c586c0;
    --string:    #ce9178;
    --comment:   #6a9955;
    --white:     #f0f0f0;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    font-family: 'JetBrains Mono', 'Fira Code', monospace;
    font-size: 13px;
    line-height: 1.6;
    color: var(--text);
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 40px 20px;
  }

  /* Noise texture overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
    opacity: 0.4;
  }

  .wrapper {
    width: 100%;
    max-width: 760px;
    position: relative;
    z-index: 1;
  }

  /* ── WINDOW CHROME ── */
  .window {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
    box-shadow:
      0 0 0 1px rgba(255,255,255,0.04),
      0 32px 80px rgba(0,0,0,0.7),
      0 8px 24px rgba(0,0,0,0.5);
  }

  .titlebar {
    background: #2a2a2a;
    border-bottom: 1px solid var(--border);
    padding: 12px 16px;
    display: flex;
    align-items: center;
    gap: 12px;
    user-select: none;
  }

  .dots { display: flex; gap: 7px; }
  .dot {
    width: 12px; height: 12px; border-radius: 50%;
    opacity: 0.9;
    position: relative;
  }
  .dot.red    { background: #ff5f57; }
  .dot.yellow { background: #febc2e; }
  .dot.green  { background: #28c840; }

  .titlebar-text {
    flex: 1;
    text-align: center;
    color: var(--muted);
    font-size: 12px;
    letter-spacing: 0.03em;
    margin-right: 54px; /* offset dots width */
  }

  .titlebar-text span { color: #888; }

  /* ── TERMINAL BODY ── */
  .terminal {
    padding: 0;
  }

  /* ── PROMPT BLOCK ── */
  .prompt-block {
    padding: 20px 24px 16px;
    border-bottom: 1px solid var(--border2);
    animation: fadeIn 0.4s ease;
  }

  .prompt-line {
    display: flex;
    align-items: baseline;
    gap: 8px;
    margin-bottom: 4px;
  }

  .prompt-symbol {
    color: var(--green);
    font-size: 13px;
    font-weight: 700;
    flex-shrink: 0;
  }

  .prompt-cmd {
    color: var(--white);
    font-size: 13px;
  }

  .prompt-cmd .cmd-name { color: var(--accent); font-weight: 700; }
  .prompt-cmd .cmd-arg  { color: var(--string); }

  .cursor {
    display: inline-block;
    width: 8px; height: 14px;
    background: var(--accent);
    margin-left: 2px;
    vertical-align: middle;
    animation: blink 1.1s step-end infinite;
    border-radius: 1px;
  }

  /* ── RESPONSE CARD ── */
  .response {
    padding: 20px 24px;
    border-bottom: 1px solid var(--border2);
    animation: slideUp 0.5s ease 0.2s both;
  }

  .response-header {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 16px;
  }

  .      -icon {
    width: 28px; height: 28px;
    background: linear-gradient(135deg, var(--accent) 0%, var(--accent2) 100%);
    border-radius: 6px;
    display: flex; align-items: center; justify-content: center;
    font-size: 14px;
    flex-shrink: 0;
    box-shadow: 0 2px 8px rgba(218,119,86,0.3);
  }

  .response-label {
    color: var(--accent);
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 0.06em;
    text-transform: uppercase;
  }

  /* ── CARD BOX ── */
  .card {
    background: #1e1e1e;
    border: 1px solid var(--border);
    border-radius: 8px;
    overflow: hidden;
    position: relative;
  }

  .card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2), transparent);
  }

  .card-header {
    padding: 18px 20px 14px;
    border-bottom: 1px solid var(--border2);
    display: flex;
    align-items: flex-start;
    gap: 16px;
  }

  .avatar {
    width: 48px; height: 48px;
    background: linear-gradient(135deg, #2d2d2d, #333);
    border: 2px solid var(--border);
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-size: 20px;
    flex-shrink: 0;
  }

  .name-block {}
  .name {
    color: var(--white);
    font-size: 15px;
    font-weight: 700;
    letter-spacing: 0.01em;
    margin-bottom: 2px;
  }

  .handle {
    color: var(--muted);
    font-size: 11px;
  }
  .handle a { color: var(--blue); text-decoration: none; }
  .handle a:hover { text-decoration: underline; }

  .badges {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-top: 10px;
  }

  .badge {
    padding: 2px 8px;
    border-radius: 4px;
    font-size: 10px;
    font-weight: 600;
    letter-spacing: 0.05em;
    text-transform: uppercase;
  }
  .badge-orange { background: rgba(218,119,86,0.15); color: var(--accent); border: 1px solid rgba(218,119,86,0.3); }
  .badge-green  { background: rgba(78,201,176,0.12); color: var(--green);  border: 1px solid rgba(78,201,176,0.25); }
  .badge-blue   { background: rgba(86,156,214,0.12); color: var(--blue);   border: 1px solid rgba(86,156,214,0.25); }
  .badge-purple { background: rgba(197,134,192,0.12);color: var(--purple); border: 1px solid rgba(197,134,192,0.25); }

  /* ── FIELDS ── */
  .fields {
    padding: 14px 20px;
    display: grid;
    gap: 8px;
  }

  .field {
    display: grid;
    grid-template-columns: 120px 1fr;
    gap: 8px;
    align-items: baseline;
    font-size: 12px;
  }

  .field-key  { color: var(--blue); }
  .field-colon{ color: var(--muted); }
  .field-val  { color: var(--text); }
  .field-val a{ color: var(--string); text-decoration: none; }
  .field-val a:hover { text-decoration: underline; }
  .field-val .str  { color: var(--string); }
  .field-val .arr  { color: var(--yellow); }
  .field-val .num  { color: #b5cea8; }
  .field-val .kw   { color: var(--purple); }

  /* ── DIVIDER ── */
  .divider {
    border: none;
    border-top: 1px solid var(--border2);
    margin: 0 20px;
  }

  /* ── TECH GRID ── */
  .tech-section {
    padding: 14px 20px;
  }

  .section-title {
    color: var(--comment);
    font-size: 11px;
    margin-bottom: 10px;
    letter-spacing: 0.04em;
  }

  .tech-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }

  .tech-tag {
    background: #262626;
    border: 1px solid #333;
    border-radius: 4px;
    padding: 3px 9px;
    font-size: 11px;
    color: #bbb;
    transition: border-color 0.15s, color 0.15s;
    cursor: default;
  }
  .tech-tag:hover {
    border-color: var(--accent);
    color: var(--accent);
  }

  /* ── ACHIEVEMENTS ── */
  .achievements {
    padding: 14px 20px;
    border-top: 1px solid var(--border2);
  }

  .ach-row {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 5px 0;
    font-size: 11.5px;
    border-bottom: 1px solid rgba(255,255,255,0.03);
  }
  .ach-row:last-child { border-bottom: none; }

  .ach-icon { font-size: 14px; flex-shrink: 0; width: 20px; text-align: center; }
  .ach-name { color: var(--text); flex: 1; }
  .ach-result {
    font-size: 10px;
    font-weight: 700;
    letter-spacing: 0.06em;
    padding: 2px 7px;
    border-radius: 3px;
  }
  .winner  { background: rgba(254,188,46,0.12); color: #febc2e; border: 1px solid rgba(254,188,46,0.25); }
  .runner  { background: rgba(78,201,176,0.10); color: var(--green); border: 1px solid rgba(78,201,176,0.2); }

  /* ── LINKS ── */
  .links-row {
    padding: 14px 20px;
    border-top: 1px solid var(--border2);
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .link-chip {
    display: flex;
    align-items: center;
    gap: 6px;
    padding: 5px 12px;
    background: #262626;
    border: 1px solid #333;
    border-radius: 5px;
    color: #aaa;
    font-size: 11px;
    text-decoration: none;
    transition: all 0.15s;
  }
  .link-chip:hover {
    background: #2d2d2d;
    border-color: var(--accent);
    color: var(--white);
  }
  .link-chip .icon { font-size: 13px; }

  /* ── STATUS BAR ── */
  .statusbar {
    background: var(--accent);
    padding: 5px 16px;
    display: flex;
    align-items: center;
    gap: 16px;
    font-size: 11px;
    color: rgba(0,0,0,0.85);
    font-weight: 600;
    letter-spacing: 0.02em;
  }

  .status-item { display: flex; align-items: center; gap: 5px; }
  .status-sep  { color: rgba(0,0,0,0.3); }

  /* ── TOOL USE BLOCK ── */
  .tool-block {
    margin: 0 24px 16px;
    background: #1a1a1a;
    border: 1px solid var(--border2);
    border-left: 3px solid var(--accent);
    border-radius: 0 6px 6px 0;
    padding: 10px 14px;
    font-size: 11.5px;
    animation: slideUp 0.5s ease 0.1s both;
  }

  .tool-name { color: var(--yellow); margin-bottom: 4px; }
  .tool-name span { color: var(--muted); font-size: 10px; margin-left: 6px; }
  .tool-args { color: var(--muted); font-size: 11px; }
  .tool-args em { color: var(--string); font-style: normal; }

  /* ── ANIMATIONS ── */
  @keyframes blink {
    0%, 100% { opacity: 1; }
    50%       { opacity: 0; }
  }

  @keyframes fadeIn {
    from { opacity: 0; }
    to   { opacity: 1; }
  }

  @keyframes slideUp {
    from { opacity: 0; transform: translateY(8px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* Scrollbar */
  ::-webkit-scrollbar { width: 6px; height: 6px; }
  ::-webkit-scrollbar-track { background: #1a1a1a; }
  ::-webkit-scrollbar-thumb { background: #333; border-radius: 3px; }
  ::-webkit-scrollbar-thumb:hover { background: #444; }
</style>
</head>
<body>

<div class="wrapper">
  <div class="window">

    <!-- Title Bar -->
    <div class="titlebar">
      <div class="dots">
        <div class="dot red"></div>
        <div class="dot yellow"></div>
        <div class="dot green"></div>
      </div>
      <div class="titlebar-text">  — <span>~/pranav-bhagath19</span></div>
    </div>

    <!-- Terminal -->
    <div class="terminal">

      <!-- Prompt -->
      <div class="prompt-block">
        <div class="prompt-line">
          <span class="prompt-symbol">❯</span>
          <span class="prompt-cmd">
            <span class="cmd-name">  </span><span class="cmd-arg">"who is pranav sai bhagath?"</span>
          </span>
          <span class="cursor"></span>
        </div>
      </div>

      <!-- Tool use -->
      <div class="tool-block">
        <div class="tool-name">⚙ fetch_profile <span>· running</span></div>
        <div class="tool-args">url: <em>"https://pranavbhagath.in"</em></div>
      </div>

      <!-- Response -->
      <div class="response">
        <div class="response-header">
          <div class="      -icon">◆</div>
          <div class="response-label"> </div>
        </div>

        <!-- Card -->
        <div class="card">

          <!-- Card Header -->
          <div class="card-header">
            <div class="avatar">👨‍💻</div>
            <div class="name-block">
              <div class="name">Pranav Sai Bhagath V</div>
              <div class="handle">
                <a href="https://github.com/pranav-bhagath19">@pranav-bhagath19</a>
                &nbsp;·&nbsp;
                <a href="https://pranavbhagath.in">pranavbhagath.in</a>
              </div>
              <div class="badges">
                <span class="badge badge-orange">AI/ML Developer</span>
                <span class="badge badge-green">GDG AI Lead</span>
                <span class="badge badge-blue">5× Hackathon Winner</span>
                <span class="badge badge-purple">Open to Opportunities</span>
              </div>
            </div>
          </div>

          <!-- Fields -->
          <div class="fields">
            <div class="field">
              <span class="field-key">role</span>
              <span class="field-val"><span class="str">"AI/ML Developer & Generative AI Specialist"</span></span>
            </div>
            <div class="field">
              <span class="field-key">education</span>
              <span class="field-val"><span class="str">"2nd Year CSE · VITB, Bhimavaram"</span></span>
            </div>
            <div class="field">
              <span class="field-key">position</span>
              <span class="field-val"><span class="str">"AI Lead @ GDG On Campus VITB"</span></span>
            </div>
            <div class="field">
              <span class="field-key">projects</span>
              <span class="field-val"><span class="num">10</span><span class="kw">+</span> <span class="arr">// AI/ML projects shipped</span></span>
            </div>
            <div class="field">
              <span class="field-key">focus</span>
              <span class="field-val"><span class="arr">[</span> <span class="str">"Generative AI"</span>, <span class="str">"Agentic AI"</span>, <span class="str">"LLM Fine-tuning"</span>, <span class="str">"RAG"</span> <span class="arr">]</span></span>
            </div>
            <div class="field">
              <span class="field-key">contact</span>
              <span class="field-val"><a href="mailto:24pa1a5762@vishnu.edu.in"><span class="str">"24pa1a5762@vishnu.edu.in"</span></a></span>
            </div>
          </div>

          <hr class="divider">

          <!-- Tech Stack -->
          <div class="tech-section">
            <div class="section-title">// tech stack</div>
            <div class="tech-grid">
              <span class="tech-tag">Python</span>
              <span class="tech-tag">PyTorch</span>
              <span class="tech-tag">TensorFlow</span>
              <span class="tech-tag">LangChain</span>
              <span class="tech-tag">RAG</span>
              <span class="tech-tag">FastAPI</span>
              <span class="tech-tag">Flutter</span>
              <span class="tech-tag">Firebase</span>
              <span class="tech-tag">Vertex AI</span>
              <span class="tech-tag">Azure ML</span>
              <span class="tech-tag">Docker</span>
              <span class="tech-tag">Pinecone</span>
              <span class="tech-tag">n8n</span>
              <span class="tech-tag">Qiskit</span>
              <span class="tech-tag">TypeScript</span>
            </div>
          </div>

          <!-- Achievements -->
          <div class="achievements">
            <div class="section-title">// achievements.log</div>
            <div class="ach-row">
              <span class="ach-icon">🏆</span>
              <span class="ach-name">Smart India Hackathon 2025 · IIC VITB</span>
              <span class="ach-result winner">WINNER</span>
            </div>
            <div class="ach-row">
              <span class="ach-icon">🏆</span>
              <span class="ach-name">BizVit 2026 · E-Cell VITB</span>
              <span class="ach-result winner">WINNER</span>
            </div>
            <div class="ach-row">
              <span class="ach-icon">🏆</span>
              <span class="ach-name">Abhinava Hackathon · ISTE VITB</span>
              <span class="ach-result winner">WINNER</span>
            </div>
            <div class="ach-row">
              <span class="ach-icon">🥈</span>
              <span class="ach-name">Hackoddysey 1.0 · IIC VITB</span>
              <span class="ach-result runner">RUNNER-UP</span>
            </div>
            <div class="ach-row">
              <span class="ach-icon">🥈</span>
              <span class="ach-name">Code Slayer 24hr Hackathon · AI&DS VITB</span>
              <span class="ach-result runner">RUNNER-UP</span>
            </div>
          </div>

          <!-- Links -->
          <div class="links-row">
            <a class="link-chip" href="https://pranavbhagath.in" target="_blank">
              <span class="icon">🌐</span> pranavbhagath.in
            </a>
            <a class="link-chip" href="https://github.com/pranav-bhagath19" target="_blank">
              <span class="icon">💻</span> github
            </a>
            <a class="link-chip" href="https://linkedin.com/in/pranav-sai-bhagath" target="_blank">
              <span class="icon">💼</span> linkedin
            </a>
            <a class="link-chip" href="mailto:24pa1a5762@vishnu.edu.in">
              <span class="icon">📧</span> email
            </a>
            <a class="link-chip" href="tel:+918500164309">
              <span class="icon">📱</span> +91 85001 64309
            </a>
          </div>

        </div>
      </div>
    </div>

    <!-- Status Bar -->
    <div class="statusbar">
      <span class="status-item">◆       -sonnet-4</span>
      <span class="status-sep">·</span>
      <span class="status-item">✓ profile fetched</span>
      <span class="status-sep">·</span>
      <span class="status-item">⚡ building intelligent solutions</span>
    </div>

  </div>
</div>

</body>
</html>
