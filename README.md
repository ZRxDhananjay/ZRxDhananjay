<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DHANANJAY KUMAR — Android Developer</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;700;900&family=Exo+2:wght@300;400;600;800&display=swap');

  :root {
    --cyan: #00f5ff;
    --magenta: #ff00aa;
    --green: #00ff88;
    --yellow: #ffd700;
    --dark: #030a0e;
    --card: #040f14;
    --border: rgba(0,245,255,0.15);
    --glow-cyan: 0 0 20px rgba(0,245,255,0.5), 0 0 60px rgba(0,245,255,0.2);
    --glow-magenta: 0 0 20px rgba(255,0,170,0.5), 0 0 60px rgba(255,0,170,0.2);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--dark);
    color: #c0d8e0;
    font-family: 'Exo 2', sans-serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    position: fixed; width: 12px; height: 12px;
    background: var(--cyan); border-radius: 50%;
    pointer-events: none; z-index: 9999;
    transform: translate(-50%,-50%);
    transition: width 0.2s, height 0.2s, background 0.2s;
    box-shadow: var(--glow-cyan);
  }
  .cursor-ring {
    position: fixed; width: 36px; height: 36px;
    border: 1px solid var(--cyan); border-radius: 50%;
    pointer-events: none; z-index: 9998;
    transform: translate(-50%,-50%);
    transition: all 0.12s ease-out;
    opacity: 0.6;
  }

  /* Scanlines overlay */
  body::before {
    content: '';
    position: fixed; inset: 0; z-index: 9990;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.05) 2px,
      rgba(0,0,0,0.05) 4px
    );
    pointer-events: none;
    animation: scanMove 8s linear infinite;
  }
  @keyframes scanMove { from { background-position: 0 0; } to { background-position: 0 100vh; } }

  /* Grid background */
  body::after {
    content: '';
    position: fixed; inset: 0; z-index: 0;
    background-image:
      linear-gradient(rgba(0,245,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,245,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
  }

  .container { max-width: 960px; margin: 0 auto; padding: 0 24px; position: relative; z-index: 1; }

  /* ── HEADER ── */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column; justify-content: center; align-items: center;
    text-align: center; position: relative; overflow: hidden; padding: 60px 24px;
  }

  .hero-bg-rings {
    position: absolute; inset: 0; display: flex; align-items: center; justify-content: center;
    pointer-events: none;
  }
  .ring {
    position: absolute; border-radius: 50%;
    border: 1px solid;
    animation: ringPulse 4s ease-in-out infinite;
  }
  .ring:nth-child(1) { width: 300px; height: 300px; border-color: rgba(0,245,255,0.15); animation-delay: 0s; }
  .ring:nth-child(2) { width: 500px; height: 500px; border-color: rgba(255,0,170,0.1); animation-delay: 0.8s; }
  .ring:nth-child(3) { width: 700px; height: 700px; border-color: rgba(0,245,255,0.07); animation-delay: 1.6s; }
  .ring:nth-child(4) { width: 900px; height: 900px; border-color: rgba(255,0,170,0.05); animation-delay: 2.4s; }
  @keyframes ringPulse {
    0%, 100% { transform: scale(1); opacity: 0.6; }
    50% { transform: scale(1.04); opacity: 1; }
  }

  .status-badge {
    display: inline-flex; align-items: center; gap: 8px;
    border: 1px solid var(--green);
    padding: 6px 16px; border-radius: 2px;
    font-family: 'Share Tech Mono', monospace;
    font-size: 11px; color: var(--green);
    text-transform: uppercase; letter-spacing: 3px;
    margin-bottom: 28px;
    animation: badgePulse 2s ease-in-out infinite;
  }
  .status-dot { width: 6px; height: 6px; background: var(--green); border-radius: 50%; animation: blink 1s infinite; }
  @keyframes blink { 0%,100% { opacity: 1; } 50% { opacity: 0; } }
  @keyframes badgePulse { 0%,100% { box-shadow: 0 0 8px rgba(0,255,136,0.3); } 50% { box-shadow: 0 0 20px rgba(0,255,136,0.6); } }

  .hero-name {
    font-family: 'Orbitron', monospace;
    font-size: clamp(42px, 8vw, 92px);
    font-weight: 900;
    letter-spacing: 6px;
    line-height: 1;
    margin-bottom: 8px;
    background: linear-gradient(135deg, #ffffff 0%, var(--cyan) 40%, var(--magenta) 70%, var(--cyan) 100%);
    background-size: 300% 300%;
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    animation: nameGlow 4s ease infinite;
    position: relative;
  }
  @keyframes nameGlow {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }

  .hero-title {
    font-family: 'Share Tech Mono', monospace;
    font-size: clamp(12px, 2vw, 16px);
    color: var(--cyan);
    letter-spacing: 6px;
    text-transform: uppercase;
    margin-bottom: 36px;
    opacity: 0.85;
  }

  .hero-stats {
    display: flex; gap: 40px; flex-wrap: wrap; justify-content: center;
    margin-bottom: 48px;
  }
  .stat-item { text-align: center; }
  .stat-value {
    font-family: 'Orbitron', monospace; font-size: 28px; font-weight: 700;
    color: var(--cyan); display: block;
    text-shadow: var(--glow-cyan);
  }
  .stat-label {
    font-family: 'Share Tech Mono', monospace; font-size: 10px;
    text-transform: uppercase; letter-spacing: 2px; color: #5a8a99; margin-top: 4px;
  }

  .cta-row { display: flex; gap: 16px; flex-wrap: wrap; justify-content: center; }
  .btn {
    font-family: 'Share Tech Mono', monospace; font-size: 12px;
    letter-spacing: 2px; text-transform: uppercase;
    padding: 12px 28px; text-decoration: none;
    border: 1px solid; cursor: none; transition: all 0.3s;
    position: relative; overflow: hidden;
  }
  .btn::before {
    content: ''; position: absolute; inset: 0;
    transform: translateX(-100%); transition: transform 0.3s;
  }
  .btn:hover::before { transform: translateX(0); }
  .btn:hover { color: var(--dark); }
  .btn-cyan { color: var(--cyan); border-color: var(--cyan); }
  .btn-cyan::before { background: var(--cyan); }
  .btn-magenta { color: var(--magenta); border-color: var(--magenta); }
  .btn-magenta::before { background: var(--magenta); }
  .btn span { position: relative; z-index: 1; }

  /* ── SECTIONS ── */
  section { padding: 80px 0; }
  .section-header {
    display: flex; align-items: center; gap: 16px; margin-bottom: 48px;
  }
  .section-label {
    font-family: 'Share Tech Mono', monospace; font-size: 10px;
    letter-spacing: 4px; text-transform: uppercase; color: var(--magenta);
  }
  .section-title {
    font-family: 'Orbitron', monospace; font-size: clamp(20px, 4vw, 30px);
    font-weight: 700; color: #fff; letter-spacing: 2px;
  }
  .section-line { flex: 1; height: 1px; background: linear-gradient(90deg, var(--border), transparent); }

  /* ── SKILLS GRID ── */
  .skills-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(80px, 1fr)); gap: 16px; }
  .skill-pill {
    border: 1px solid var(--border);
    background: var(--card);
    padding: 16px 8px; text-align: center;
    transition: all 0.3s; cursor: none;
    position: relative; overflow: hidden;
    clip-path: polygon(0 0, calc(100% - 8px) 0, 100% 8px, 100% 100%, 8px 100%, 0 calc(100% - 8px));
  }
  .skill-pill::before {
    content: ''; position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(0,245,255,0.05), transparent);
    opacity: 0; transition: opacity 0.3s;
  }
  .skill-pill:hover { border-color: var(--cyan); transform: translateY(-4px); box-shadow: var(--glow-cyan); }
  .skill-pill:hover::before { opacity: 1; }
  .skill-icon { font-size: 28px; display: block; margin-bottom: 8px; }
  .skill-name { font-family: 'Share Tech Mono', monospace; font-size: 9px; color: var(--cyan); letter-spacing: 1px; text-transform: uppercase; }

  /* ── SKILL BARS ── */
  .skill-bars { display: flex; flex-direction: column; gap: 20px; }
  .bar-row { display: grid; grid-template-columns: 180px 1fr 48px; align-items: center; gap: 16px; }
  .bar-label { font-family: 'Share Tech Mono', monospace; font-size: 12px; color: #a0c8d8; }
  .bar-track { height: 6px; background: rgba(0,245,255,0.08); border-radius: 0; position: relative; overflow: hidden; }
  .bar-fill {
    height: 100%; background: linear-gradient(90deg, var(--cyan), var(--magenta));
    border-radius: 0; transform-origin: left;
    animation: barGrow 1.5s cubic-bezier(0.4,0,0.2,1) forwards;
    transform: scaleX(0);
    box-shadow: 0 0 8px rgba(0,245,255,0.4);
  }
  @keyframes barGrow { to { transform: scaleX(1); } }
  .bar-pct { font-family: 'Orbitron', monospace; font-size: 11px; color: var(--cyan); text-align: right; }

  /* ── PROJECTS ── */
  .projects-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; }
  @media (max-width: 640px) { .projects-grid { grid-template-columns: 1fr; } }

  .project-card {
    border: 1px solid var(--border);
    background: var(--card);
    padding: 28px;
    position: relative; overflow: hidden;
    clip-path: polygon(0 0, calc(100% - 16px) 0, 100% 16px, 100% 100%, 0 100%);
    transition: all 0.3s; cursor: none;
  }
  .project-card::after {
    content: ''; position: absolute;
    top: 0; right: 0; width: 0; height: 0;
    border-style: solid;
    border-width: 0 16px 16px 0;
    border-color: transparent var(--cyan) transparent transparent;
    transition: border-color 0.3s;
  }
  .project-card:hover { border-color: var(--cyan); transform: translateY(-6px); box-shadow: 0 24px 48px rgba(0,0,0,0.5), var(--glow-cyan); }
  .project-card:hover::after { border-color: transparent var(--magenta) transparent transparent; }

  .project-status {
    display: inline-flex; align-items: center; gap: 6px;
    font-family: 'Share Tech Mono', monospace; font-size: 10px;
    letter-spacing: 2px; text-transform: uppercase;
    margin-bottom: 12px;
  }
  .status-complete { color: var(--green); }
  .status-wip { color: var(--yellow); }
  .status-dot-sm { width: 5px; height: 5px; border-radius: 50%; animation: blink 1.2s infinite; }

  .project-title {
    font-family: 'Orbitron', monospace; font-size: 18px; font-weight: 700;
    color: #fff; margin-bottom: 12px; letter-spacing: 1px;
  }
  .project-desc { font-size: 13px; line-height: 1.7; color: #7a9aaa; margin-bottom: 20px; }
  .tag-row { display: flex; flex-wrap: wrap; gap: 8px; }
  .tag {
    font-family: 'Share Tech Mono', monospace; font-size: 10px;
    padding: 4px 10px; border: 1px solid rgba(0,245,255,0.2);
    color: var(--cyan); letter-spacing: 1px; text-transform: uppercase;
    transition: all 0.2s;
  }
  .tag:hover { background: rgba(0,245,255,0.1); border-color: var(--cyan); }

  /* ── TIMELINE ── */
  .timeline { position: relative; padding-left: 32px; }
  .timeline::before {
    content: ''; position: absolute; left: 8px; top: 0; bottom: 0; width: 1px;
    background: linear-gradient(to bottom, var(--cyan), var(--magenta), transparent);
  }
  .timeline-item { position: relative; margin-bottom: 32px; }
  .timeline-dot {
    position: absolute; left: -28px; top: 4px;
    width: 12px; height: 12px; background: var(--dark);
    border: 2px solid var(--cyan); border-radius: 50%;
    box-shadow: var(--glow-cyan);
  }
  .timeline-year {
    font-family: 'Share Tech Mono', monospace; font-size: 10px;
    color: var(--magenta); letter-spacing: 2px; margin-bottom: 4px;
  }
  .timeline-title {
    font-family: 'Orbitron', monospace; font-size: 14px; color: #fff;
    font-weight: 700; margin-bottom: 4px;
  }
  .timeline-sub { font-size: 12px; color: #5a7a88; }

  /* ── CERTS ── */
  .certs-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); gap: 20px; }
  .cert-card {
    border: 1px solid var(--border); background: var(--card);
    padding: 20px 24px; display: flex; align-items: flex-start; gap: 16px;
    transition: all 0.3s; cursor: none;
    clip-path: polygon(0 0, 100% 0, 100% calc(100% - 10px), calc(100% - 10px) 100%, 0 100%);
  }
  .cert-card:hover { border-color: var(--magenta); box-shadow: var(--glow-magenta); transform: translateY(-3px); }
  .cert-icon { font-size: 28px; flex-shrink: 0; }
  .cert-name { font-family: 'Orbitron', monospace; font-size: 12px; color: #fff; font-weight: 700; margin-bottom: 4px; }
  .cert-issuer { font-family: 'Share Tech Mono', monospace; font-size: 10px; color: var(--magenta); letter-spacing: 1px; }
  .cert-date { font-size: 10px; color: #4a6a78; margin-top: 2px; }

  /* ── CONTACT ── */
  .contact-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 16px; }
  .contact-link {
    display: flex; align-items: center; gap: 14px;
    border: 1px solid var(--border); background: var(--card);
    padding: 16px 20px; text-decoration: none;
    transition: all 0.3s; cursor: none;
    position: relative; overflow: hidden;
    clip-path: polygon(0 0, calc(100% - 10px) 0, 100% 10px, 100% 100%, 10px 100%, 0 calc(100% - 10px));
  }
  .contact-link::before {
    content: ''; position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(0,245,255,0.05), transparent);
    opacity: 0; transition: opacity 0.3s;
  }
  .contact-link:hover { border-color: var(--cyan); transform: translateY(-3px); box-shadow: var(--glow-cyan); }
  .contact-link:hover::before { opacity: 1; }
  .contact-icon { font-size: 22px; flex-shrink: 0; }
  .contact-label { font-family: 'Share Tech Mono', monospace; font-size: 10px; color: #5a8a99; text-transform: uppercase; letter-spacing: 1px; }
  .contact-value { font-size: 12px; color: var(--cyan); }

  /* ── PHILOSOPHY ── */
  .terminal-block {
    border: 1px solid var(--border); background: var(--card);
    padding: 32px; position: relative;
    font-family: 'Share Tech Mono', monospace;
  }
  .terminal-header {
    display: flex; align-items: center; gap: 8px; margin-bottom: 24px;
    padding-bottom: 12px; border-bottom: 1px solid var(--border);
  }
  .t-dot { width: 10px; height: 10px; border-radius: 50%; }
  .t-red { background: #ff5f57; }
  .t-yellow { background: #febc2e; }
  .t-green { background: #28c840; }
  .t-title { font-size: 11px; color: #4a6a78; letter-spacing: 2px; margin-left: 8px; }

  .code-line { font-size: 13px; line-height: 2; }
  .c-comment { color: #3a5a68; }
  .c-keyword { color: var(--magenta); }
  .c-string { color: var(--green); }
  .c-func { color: var(--cyan); }
  .c-var { color: var(--yellow); }
  .c-punct { color: #a0c0cc; }

  /* ── FOOTER ── */
  footer {
    border-top: 1px solid var(--border);
    padding: 40px 0; text-align: center;
  }
  .footer-name {
    font-family: 'Orbitron', monospace; font-size: 20px;
    font-weight: 900; letter-spacing: 6px;
    background: linear-gradient(90deg, var(--cyan), var(--magenta));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    margin-bottom: 8px;
  }
  .footer-sub {
    font-family: 'Share Tech Mono', monospace; font-size: 10px;
    color: #2a4a58; letter-spacing: 4px; text-transform: uppercase;
  }

  /* ── SCROLL ANIMATIONS ── */
  .reveal {
    opacity: 0; transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }
  .reveal-left { opacity: 0; transform: translateX(-30px); transition: opacity 0.7s ease, transform 0.7s ease; }
  .reveal-left.visible { opacity: 1; transform: translateX(0); }

  /* stagger children */
  .stagger > * { opacity: 0; transform: translateY(20px); transition: opacity 0.5s ease, transform 0.5s ease; }
  .stagger.visible > *:nth-child(1) { opacity:1; transform:translateY(0); transition-delay:0.05s; }
  .stagger.visible > *:nth-child(2) { opacity:1; transform:translateY(0); transition-delay:0.1s; }
  .stagger.visible > *:nth-child(3) { opacity:1; transform:translateY(0); transition-delay:0.15s; }
  .stagger.visible > *:nth-child(4) { opacity:1; transform:translateY(0); transition-delay:0.2s; }
  .stagger.visible > *:nth-child(5) { opacity:1; transform:translateY(0); transition-delay:0.25s; }
  .stagger.visible > *:nth-child(6) { opacity:1; transform:translateY(0); transition-delay:0.3s; }
  .stagger.visible > *:nth-child(7) { opacity:1; transform:translateY(0); transition-delay:0.35s; }
  .stagger.visible > *:nth-child(8) { opacity:1; transform:translateY(0); transition-delay:0.4s; }
  .stagger.visible > *:nth-child(9) { opacity:1; transform:translateY(0); transition-delay:0.45s; }
  .stagger.visible > *:nth-child(10) { opacity:1; transform:translateY(0); transition-delay:0.5s; }

  /* Glitch effect for nav */
  .nav-glitch {
    position: relative;
    animation: glitchShift 6s infinite;
  }
  @keyframes glitchShift {
    0%, 92%, 100% { clip-path: none; transform: none; }
    93% { clip-path: polygon(0 20%, 100% 20%, 100% 40%, 0 40%); transform: translateX(4px); }
    94% { clip-path: polygon(0 60%, 100% 60%, 100% 80%, 0 80%); transform: translateX(-4px); }
    95% { clip-path: none; transform: none; }
  }

  /* Floating particles */
  .particles { position: absolute; inset: 0; overflow: hidden; pointer-events: none; }
  .particle {
    position: absolute; width: 2px; height: 2px;
    background: var(--cyan); border-radius: 50%;
    animation: float linear infinite;
    opacity: 0;
  }
  @keyframes float {
    0% { transform: translateY(100vh) translateX(0); opacity: 0; }
    10% { opacity: 0.6; }
    90% { opacity: 0.4; }
    100% { transform: translateY(-10vh) translateX(var(--dx)); opacity: 0; }
  }

  /* Nav */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 16px 40px;
    background: rgba(3,10,14,0.9);
    border-bottom: 1px solid var(--border);
    backdrop-filter: blur(12px);
  }
  .nav-logo {
    font-family: 'Orbitron', monospace; font-size: 14px; font-weight: 900;
    color: var(--cyan); letter-spacing: 3px; text-shadow: var(--glow-cyan);
  }
  .nav-links { display: flex; gap: 32px; }
  .nav-link {
    font-family: 'Share Tech Mono', monospace; font-size: 11px;
    text-decoration: none; color: #5a8a99; letter-spacing: 2px;
    text-transform: uppercase; transition: color 0.2s;
  }
  .nav-link:hover { color: var(--cyan); }

  @media (max-width: 600px) {
    nav { padding: 12px 20px; }
    .nav-links { gap: 16px; }
    .bar-row { grid-template-columns: 120px 1fr 40px; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<nav>
  <div class="nav-logo nav-glitch">DK</div>
  <div class="nav-links">
    <a href="#skills" class="nav-link">Skills</a>
    <a href="#projects" class="nav-link">Projects</a>
    <a href="#education" class="nav-link">Education</a>
    <a href="#contact" class="nav-link">Contact</a>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="particles" id="particles"></div>
  <div class="hero-bg-rings">
    <div class="ring"></div><div class="ring"></div><div class="ring"></div><div class="ring"></div>
  </div>

  <div class="status-badge">
    <span class="status-dot"></span>
    System Online — Available for Opportunities
  </div>

  <h1 class="hero-name">DHANANJAY<br>KUMAR</h1>
  <p class="hero-title">Android Developer · Mobile Engineer · Tech Innovator</p>

  <div class="hero-stats">
    <div class="stat-item">
      <span class="stat-value">3+</span>
      <span class="stat-label">Projects Deployed</span>
    </div>
    <div class="stat-item">
      <span class="stat-value">2</span>
      <span class="stat-label">Publications</span>
    </div>
    <div class="stat-item">
      <span class="stat-value">3</span>
      <span class="stat-label">Certifications</span>
    </div>
    <div class="stat-item">
      <span class="stat-value">92%</span>
      <span class="stat-label">Android Mastery</span>
    </div>
  </div>

  <div class="cta-row">
    <a href="mailto:dhananjayjob43@gmail.com" class="btn btn-cyan"><span>⚡ Hire Me</span></a>
    <a href="#projects" class="btn btn-magenta"><span>◉ View Work</span></a>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="container">
    <div class="section-header reveal">
      <div>
        <div class="section-label">// 001 — Arsenal</div>
        <h2 class="section-title">TECHNICAL SKILLS</h2>
      </div>
      <div class="section-line"></div>
    </div>

    <div class="skills-grid stagger" style="margin-bottom: 48px;">
      <div class="skill-pill"><span class="skill-icon">🤖</span><span class="skill-name">Android</span></div>
      <div class="skill-pill"><span class="skill-icon">☕</span><span class="skill-name">Java</span></div>
      <div class="skill-pill"><span class="skill-icon">🎯</span><span class="skill-name">Kotlin</span></div>
      <div class="skill-pill"><span class="skill-icon">🔥</span><span class="skill-name">Firebase</span></div>
      <div class="skill-pill"><span class="skill-icon">🐍</span><span class="skill-name">Python</span></div>
      <div class="skill-pill"><span class="skill-icon">🌐</span><span class="skill-name">HTML5</span></div>
      <div class="skill-pill"><span class="skill-icon">🎨</span><span class="skill-name">CSS3</span></div>
      <div class="skill-pill"><span class="skill-icon">🗃️</span><span class="skill-name">SQL</span></div>
      <div class="skill-pill"><span class="skill-icon">🌿</span><span class="skill-name">Git</span></div>
      <div class="skill-pill"><span class="skill-icon">💻</span><span class="skill-name">VS Code</span></div>
    </div>

    <div class="skill-bars reveal">
      <div class="bar-row">
        <span class="bar-label">Android Development</span>
        <div class="bar-track"><div class="bar-fill" style="width:92%; animation-delay:0.1s;"></div></div>
        <span class="bar-pct">92%</span>
      </div>
      <div class="bar-row">
        <span class="bar-label">Java & Kotlin</span>
        <div class="bar-track"><div class="bar-fill" style="width:88%; animation-delay:0.2s;"></div></div>
        <span class="bar-pct">88%</span>
      </div>
      <div class="bar-row">
        <span class="bar-label">Dart / Flutter</span>
        <div class="bar-track"><div class="bar-fill" style="width:88%; animation-delay:0.3s;"></div></div>
        <span class="bar-pct">88%</span>
      </div>
      <div class="bar-row">
        <span class="bar-label">Firebase Integration</span>
        <div class="bar-track"><div class="bar-fill" style="width:95%; animation-delay:0.4s;"></div></div>
        <span class="bar-pct">95%</span>
      </div>
      <div class="bar-row">
        <span class="bar-label">UI / UX Design</span>
        <div class="bar-track"><div class="bar-fill" style="width:85%; animation-delay:0.5s;"></div></div>
        <span class="bar-pct">85%</span>
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="container">
    <div class="section-header reveal">
      <div>
        <div class="section-label">// 002 — Mission Log</div>
        <h2 class="section-title">ACTIVE PROJECTS</h2>
      </div>
      <div class="section-line"></div>
    </div>

    <div class="projects-grid stagger">
      <div class="project-card">
        <div class="project-status status-complete">
          <span class="status-dot-sm" style="background:var(--green);"></span> Complete
        </div>
        <div class="project-title">🐝 CareerBee</div>
        <p class="project-desc">Career-oriented Android platform bridging job seekers and employers. Real-time auth, job posting, application management with Firebase Realtime Database integration.</p>
        <div class="tag-row">
          <span class="tag">Android</span><span class="tag">Java</span><span class="tag">Firebase</span><span class="tag">XML</span>
        </div>
      </div>

      <div class="project-card">
        <div class="project-status status-complete">
          <span class="status-dot-sm" style="background:var(--green);"></span> Complete
        </div>
        <div class="project-title">✨ FairyFlix</div>
        <p class="project-desc">Engaging short story collection app with intuitive UI, Firebase backend, dynamic content loading, and seamless WebView integration for immersive reading.</p>
        <div class="tag-row">
          <span class="tag">Android</span><span class="tag">Kotlin</span><span class="tag">Firebase</span><span class="tag">WebView</span>
        </div>
      </div>

      <div class="project-card">
        <div class="project-status status-complete">
          <span class="status-dot-sm" style="background:var(--green);"></span> Complete
        </div>
        <div class="project-title">🎓 AcadEase</div>
        <p class="project-desc">Online educational platform with academic resources — notes, video lectures, and assessments for self-paced learning. Full backend on Firebase.</p>
        <div class="tag-row">
          <span class="tag">Android</span><span class="tag">Java</span><span class="tag">Firebase</span>
        </div>
      </div>

      <div class="project-card" style="border-style: dashed; opacity: 0.7;">
        <div class="project-status" style="color: var(--yellow);">
          <span class="status-dot-sm" style="background:var(--yellow);"></span> Initializing
        </div>
        <div class="project-title">🚀 Next Mission</div>
        <p class="project-desc">Classified. New project loading... Stand by for deployment. Something extraordinary is being built.</p>
        <div class="tag-row">
          <span class="tag">?</span><span class="tag">?</span><span class="tag">?</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- EDUCATION -->
<section id="education">
  <div class="container">
    <div class="section-header reveal">
      <div>
        <div class="section-label">// 003 — Training Matrix</div>
        <h2 class="section-title">EDUCATION</h2>
      </div>
      <div class="section-line"></div>
    </div>

    <div class="timeline reveal">
      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-year">2023 — 2026 · ACTIVE</div>
        <div class="timeline-title">B.Tech — Computer Science & IT</div>
        <div class="timeline-sub">Jharkhand Rai University · Final Year</div>
      </div>
      <div class="timeline-item">
        <div class="timeline-dot" style="border-color:var(--magenta); box-shadow: var(--glow-magenta);"></div>
        <div class="timeline-year">2018 — 2020</div>
        <div class="timeline-title">Diploma — Electrical Engineering</div>
        <div class="timeline-sub">Vidya Memorial Institute of Technology</div>
      </div>
      <div class="timeline-item">
        <div class="timeline-dot" style="border-color:#5a8a99;"></div>
        <div class="timeline-year">2017 — 2018</div>
        <div class="timeline-title">Intermediate — Science</div>
        <div class="timeline-sub">Premchand High School</div>
      </div>
      <div class="timeline-item">
        <div class="timeline-dot" style="border-color:#3a5a68;"></div>
        <div class="timeline-year">2014 — 2015</div>
        <div class="timeline-title">Matriculation</div>
        <div class="timeline-sub">Kendriya Vidyalaya No-1, HEC</div>
      </div>
    </div>
  </div>
</section>

<!-- CERTIFICATIONS -->
<section>
  <div class="container">
    <div class="section-header reveal">
      <div>
        <div class="section-label">// 004 — Credentials</div>
        <h2 class="section-title">CERTIFICATIONS</h2>
      </div>
      <div class="section-line"></div>
    </div>

    <div class="certs-grid stagger">
      <div class="cert-card">
        <div class="cert-icon">🤖</div>
        <div>
          <div class="cert-name">Android Development</div>
          <div class="cert-issuer">CodeZeal Pvt. Ltd.</div>
          <div class="cert-date">Sep 2025</div>
        </div>
      </div>
      <div class="cert-card">
        <div class="cert-icon">🧠</div>
        <div>
          <div class="cert-name">AI/ML Internship</div>
          <div class="cert-issuer">NIAMT</div>
          <div class="cert-date">Jul 2025</div>
        </div>
      </div>
      <div class="cert-card">
        <div class="cert-icon">🌐</div>
        <div>
          <div class="cert-name">Web Development</div>
          <div class="cert-issuer">Internshala</div>
          <div class="cert-date">Aug 2024</div>
        </div>
      </div>
    </div>

    <div style="margin-top:40px;" class="reveal">
      <div class="section-header" style="margin-bottom:24px;">
        <div>
          <div class="section-label">// 005 — Research</div>
          <h2 class="section-title" style="font-size:20px;">PUBLICATIONS</h2>
        </div>
        <div class="section-line"></div>
      </div>
      <div class="terminal-block" style="margin-bottom:16px;">
        <div class="code-line"><span class="c-comment">// Publication 01</span></div>
        <div class="code-line"><span class="c-keyword">conference</span> <span class="c-punct">→</span> <span class="c-string">"RAISD2025"</span></div>
        <div class="code-line"><span class="c-var">publisher</span> <span class="c-punct">=</span> <span class="c-string">"Atlantis Press"</span></div>
        <div class="code-line"><span class="c-var">paperID</span> <span class="c-punct">=</span> <span class="c-func">RAISD202512118</span></div>
        <div class="code-line"><span class="c-comment">// International Conference on Recent Advances in AI for Sustainable Development</span></div>
      </div>
      <div class="terminal-block">
        <div class="code-line"><span class="c-comment">// Publication 02</span></div>
        <div class="code-line"><span class="c-keyword">journal</span> <span class="c-punct">→</span> <span class="c-string">"IJSEA, Vol. 14(12), 2025"</span></div>
        <div class="code-line"><span class="c-var">doi</span> <span class="c-punct">=</span> <span class="c-func">10.7753/IJSEA1412.1014</span></div>
        <div class="code-line"><span class="c-comment">// Leveraging AI and RT-PCR for Enhanced Diagnosis of COVID-19</span></div>
      </div>
    </div>
  </div>
</section>

<!-- PHILOSOPHY -->
<section>
  <div class="container">
    <div class="section-header reveal">
      <div>
        <div class="section-label">// 006 — Core Protocol</div>
        <h2 class="section-title">DEVELOPER PHILOSOPHY</h2>
      </div>
      <div class="section-line"></div>
    </div>

    <div class="terminal-block reveal">
      <div class="terminal-header">
        <div class="t-dot t-red"></div>
        <div class="t-dot t-yellow"></div>
        <div class="t-dot t-green"></div>
        <span class="t-title">developer_mindset.kt</span>
      </div>
      <div class="code-line"><span class="c-keyword">class</span> <span class="c-func">DeveloperMindset</span> <span class="c-punct">{</span></div>
      <div class="code-line">&nbsp;&nbsp;<span class="c-keyword">val</span> <span class="c-var">passion</span> <span class="c-punct">=</span> <span class="c-string">"Creating user-friendly applications"</span></div>
      <div class="code-line">&nbsp;&nbsp;<span class="c-keyword">val</span> <span class="c-var">focus</span> <span class="c-punct">=</span> <span class="c-func">listOf</span><span class="c-punct">(</span><span class="c-string">"Clean Code"</span><span class="c-punct">,</span> <span class="c-string">"Scalable Architecture"</span><span class="c-punct">,</span> <span class="c-string">"Performance"</span><span class="c-punct">)</span></div>
      <div class="code-line">&nbsp;&nbsp;<span class="c-keyword">val</span> <span class="c-var">learning</span> <span class="c-punct">=</span> <span class="c-string">"Continuous"</span></div>
      <div class="code-line">&nbsp;&nbsp;<span class="c-keyword">val</span> <span class="c-var">goal</span> <span class="c-punct">=</span> <span class="c-string">"Build impactful mobile solutions"</span></div>
      <div class="code-line">&nbsp;&nbsp;</div>
      <div class="code-line">&nbsp;&nbsp;<span class="c-keyword">fun</span> <span class="c-func">currentMission</span><span class="c-punct">() =</span></div>
      <div class="code-line">&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-string">"Transforming ideas into elegant Android applications"</span></div>
      <div class="code-line">&nbsp;&nbsp;</div>
      <div class="code-line">&nbsp;&nbsp;<span class="c-keyword">fun</span> <span class="c-func">futureVision</span><span class="c-punct">() =</span></div>
      <div class="code-line">&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-string">"Leading innovative mobile development projects"</span></div>
      <div class="code-line"><span class="c-punct">}</span></div>
      <div class="code-line">&nbsp;</div>
      <div class="code-line"><span class="c-comment">// Output: "Building the future, one commit at a time"</span></div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="container">
    <div class="section-header reveal">
      <div>
        <div class="section-label">// 007 — Network</div>
        <h2 class="section-title">CONNECT</h2>
      </div>
      <div class="section-line"></div>
    </div>

    <div class="contact-grid stagger">
      <a href="mailto:dhananjayjob43@gmail.com" class="contact-link">
        <div class="contact-icon">📧</div>
        <div>
          <div class="contact-label">Gmail</div>
          <div class="contact-value">dhananjayjob43@gmail.com</div>
        </div>
      </a>
      <a href="https://www.linkedin.com/in/dhananjay-kumar" class="contact-link" target="_blank">
        <div class="contact-icon">🔗</div>
        <div>
          <div class="contact-label">LinkedIn</div>
          <div class="contact-value">dhananjay-kumar</div>
        </div>
      </a>
      <a href="tel:+917091943902" class="contact-link">
        <div class="contact-icon">📞</div>
        <div>
          <div class="contact-label">Phone</div>
          <div class="contact-value">+91 70919 43902</div>
        </div>
      </a>
      <a href="#" class="contact-link">
        <div class="contact-icon">📍</div>
        <div>
          <div class="contact-label">Location</div>
          <div class="contact-value">Ranchi, Jharkhand, India</div>
        </div>
      </a>
    </div>
  </div>
</section>

<footer>
  <div class="container">
    <div class="footer-name">DHANANJAY KUMAR</div>
    <div class="footer-sub">Android Developer · Building the future, one commit at a time</div>
  </div>
</footer>

<script>
  // Cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
  function animCursor() {
    cursor.style.left = mx + 'px'; cursor.style.top = my + 'px';
    rx += (mx - rx) * 0.15; ry += (my - ry) * 0.15;
    ring.style.left = rx + 'px'; ring.style.top = ry + 'px';
    requestAnimationFrame(animCursor);
  }
  animCursor();
  document.querySelectorAll('a, button, .skill-pill, .project-card, .cert-card').forEach(el => {
    el.addEventListener('mouseenter', () => { cursor.style.width='20px'; cursor.style.height='20px'; cursor.style.background='var(--magenta)'; });
    el.addEventListener('mouseleave', () => { cursor.style.width='12px'; cursor.style.height='12px'; cursor.style.background='var(--cyan)'; });
  });

  // Particles
  const pc = document.getElementById('particles');
  for(let i = 0; i < 30; i++) {
    const p = document.createElement('div');
    p.className = 'particle';
    const x = Math.random() * 100;
    const dur = 8 + Math.random() * 12;
    const delay = Math.random() * 10;
    const dx = (Math.random() - 0.5) * 200;
    p.style.cssText = `left:${x}%;--dx:${dx}px;animation-duration:${dur}s;animation-delay:${delay}s;${Math.random()>0.5?'background:var(--magenta)':''}`;
    pc.appendChild(p);
  }

  // Scroll reveal
  const io = new IntersectionObserver(entries => {
    entries.forEach(e => { if(e.isIntersecting) { e.target.classList.add('visible'); } });
  }, { threshold: 0.1 });
  document.querySelectorAll('.reveal, .reveal-left, .stagger').forEach(el => io.observe(el));

  // Skill bars retrigger on scroll into view
  const barObserver = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if(e.isIntersecting) {
        e.target.querySelectorAll('.bar-fill').forEach(b => {
          b.style.animation = 'none';
          b.offsetHeight; // reflow
          b.style.animation = '';
        });
      }
    });
  }, { threshold: 0.3 });
  document.querySelectorAll('.skill-bars').forEach(el => barObserver.observe(el));
</script>
</body>
</html>
