<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pranav Sai Bhagath</title>

<link href="https://fonts.googleapis.com/css2?family=Berkeley+Mono:wght@400;700&family=JetBrains+Mono:ital,wght@0,300;0,400;0,500;0,700;1,400&display=swap" rel="stylesheet">

<style>

:root {
--bg:#1a1a1a;
--surface:#212121;
--border:#333;
--border2:#2a2a2a;
--text:#d4d4d4;
--muted:#6b6b6b;
--accent:#da7756;
--accent2:#c96442;
--green:#4ec9b0;
--blue:#569cd6;
--yellow:#dcdcaa;
--purple:#c586c0;
--string:#ce9178;
--comment:#6a9955;
--white:#f0f0f0;
}

*{margin:0;padding:0;box-sizing:border-box;}

body{
background:var(--bg);
font-family:'JetBrains Mono',monospace;
font-size:13px;
color:var(--text);
min-height:100vh;
display:flex;
align-items:center;
justify-content:center;
padding:40px 20px;
}

.wrapper{
width:100%;
max-width:760px;
}

.window{
background:var(--surface);
border:1px solid var(--border);
border-radius:10px;
overflow:hidden;
}

.titlebar{
background:#2a2a2a;
border-bottom:1px solid var(--border);
padding:12px 16px;
display:flex;
align-items:center;
gap:12px;
}

.dots{display:flex;gap:7px;}

.dot{
width:12px;
height:12px;
border-radius:50%;
}

.red{background:#ff5f57;}
.yellow{background:#febc2e;}
.green{background:#28c840;}

.titlebar-text{
flex:1;
text-align:center;
color:var(--muted);
font-size:12px;
}

.prompt-block{
padding:20px 24px 16px;
border-bottom:1px solid var(--border2);
}

.prompt-line{
display:flex;
align-items:baseline;
gap:8px;
}

.prompt-symbol{
color:var(--green);
font-weight:700;
}

.prompt-cmd{
color:var(--white);
}

.cmd-name{color:var(--accent);font-weight:700;}
.cmd-arg{color:var(--string);}

.cursor{
display:inline-block;
width:8px;
height:14px;
background:var(--accent);
animation:blink 1s infinite;
}

@keyframes blink{
0%,100%{opacity:1}
50%{opacity:0}
}

.response{
padding:20px 24px;
}

.card{
background:#1e1e1e;
border:1px solid var(--border);
border-radius:8px;
overflow:hidden;
}

.card-header{
padding:18px 20px;
border-bottom:1px solid var(--border2);
display:flex;
gap:16px;
}

.avatar{
width:48px;
height:48px;
background:#333;
border-radius:8px;
display:flex;
align-items:center;
justify-content:center;
font-size:20px;
}

.name{
color:var(--white);
font-size:15px;
font-weight:700;
}

.handle{
color:var(--muted);
font-size:11px;
}

.handle a{
color:var(--blue);
text-decoration:none;
}

.badges{
display:flex;
flex-wrap:wrap;
gap:6px;
margin-top:10px;
}

.badge{
padding:2px 8px;
border-radius:4px;
font-size:10px;
font-weight:600;
}

.badge-orange{background:rgba(218,119,86,0.15);color:var(--accent);}
.badge-green{background:rgba(78,201,176,0.12);color:var(--green);}
.badge-blue{background:rgba(86,156,214,0.12);color:var(--blue);}
.badge-purple{background:rgba(197,134,192,0.12);color:var(--purple);}

.fields{
padding:14px 20px;
display:grid;
gap:8px;
}

.field{
display:grid;
grid-template-columns:120px 1fr;
font-size:12px;
}

.field-key{color:var(--blue);}
.field-val{color:var(--text);}

.field-val a{
color:var(--string);
text-decoration:none;
}

.tech-section{
padding:14px 20px;
border-top:1px solid var(--border2);
}

.section-title{
color:var(--comment);
font-size:11px;
margin-bottom:10px;
}

.tech-grid{
display:flex;
flex-wrap:wrap;
gap:6px;
}

.tech-tag{
background:#262626;
border:1px solid #333;
border-radius:4px;
padding:3px 9px;
font-size:11px;
color:#bbb;
}

.links-row{
padding:14px 20px;
border-top:1px solid var(--border2);
display:flex;
flex-wrap:wrap;
gap:8px;
}

.link-chip{
display:flex;
align-items:center;
gap:6px;
padding:5px 12px;
background:#262626;
border:1px solid #333;
border-radius:5px;
color:#aaa;
font-size:11px;
text-decoration:none;
}

.statusbar{
background:var(--accent);
padding:5px 16px;
font-size:11px;
color:#000;
}

</style>
</head>

<body>

<div class="wrapper">
<div class="window">

<div class="titlebar">
<div class="dots">
<div class="dot red"></div>
<div class="dot yellow"></div>
<div class="dot green"></div>
</div>
<div class="titlebar-text">~/pranav-bhagath19</div>
</div>

<div class="prompt-block">
<div class="prompt-line">
<span class="prompt-symbol">❯</span>
<span class="prompt-cmd">
<span class="cmd-name">whois </span>
<span class="cmd-arg">"pranav sai bhagath"</span>
</span>
<span class="cursor"></span>
</div>
</div>

<div class="response">

<div class="card">

<div class="card-header">
<div class="avatar">👨‍💻</div>

<div>
<div class="name">Pranav Sai Bhagath V</div>

<div class="handle">
<a href="https://github.com/pranav-bhagath19">@pranav-bhagath19</a>
·
<a href="https://pranavbhagath.in">pranavbhagath.in</a>
</div>

<div class="badges">
<span class="badge badge-orange">AI/ML Developer</span>
<span class="badge badge-green">GDG AI Lead</span>
<span class="badge badge-blue">Hackathon Builder</span>
<span class="badge badge-purple">Open to Opportunities</span>
</div>

</div>
</div>

<div class="fields">

<div class="field">
<span class="field-key">role</span>
<span class="field-val">AI/ML Developer & Generative AI Specialist</span>
</div>

<div class="field">
<span class="field-key">education</span>
<span class="field-val">2nd Year CSE · VITB Bhimavaram</span>
</div>

<div class="field">
<span class="field-key">position</span>
<span class="field-val">AI Lead @ GDG On Campus</span>
</div>

<div class="field">
<span class="field-key">projects</span>
<span class="field-val">10+ AI/ML projects</span>
</div>

<div class="field">
<span class="field-key">focus</span>
<span class="field-val">Generative AI, Agentic AI, RAG, LLM Fine-tuning</span>
</div>

<div class="field">
<span class="field-key">contact</span>
<span class="field-val">
<a href="mailto:pranavsaibhagath@gmail.com">
pranavsaibhagath@gmail.com
</a>
</span>
</div>

</div>

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
<span class="tech-tag">TypeScript</span>
</div>

</div>

<div class="links-row">

<a class="link-chip" href="https://pranavbhagath.in" target="_blank">
🌐 website
</a>

<a class="link-chip" href="https://github.com/pranav-bhagath19" target="_blank">
💻 github
</a>

<a class="link-chip" href="https://linkedin.com/in/pranav-sai-bhagath" target="_blank">
💼 linkedin
</a>

<a class="link-chip" href="mailto:pranavsaibhagath@gmail.com">
📧 email
</a>

</div>

</div>
</div>

<div class="statusbar">
⚡ building intelligent solutions
</div>

</div>
</div>

</body>
</html>
