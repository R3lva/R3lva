<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>R3lva | Portfolio</title>
  <link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;600&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --cyan: #00f5ff;
      --magenta: #ff006e;
      --green: #39ff14;
      --dark: #050810;
      --darker: #020408;
      --card: #0a0f1e;
      --border: rgba(0,245,255,0.15);
      --glow-cyan: 0 0 20px rgba(0,245,255,0.5);
      --glow-mag: 0 0 20px rgba(255,0,110,0.5);
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--darker);
      color: #c8d8e8;
      font-family: 'Rajdhani', sans-serif;
      font-size: 16px;
      overflow-x: hidden;
    }

    /* SCANLINES overlay */
    body::before {
      content: '';
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      background: repeating-linear-gradient(
        0deg,
        transparent,
        transparent 2px,
        rgba(0,0,0,0.08) 2px,
        rgba(0,0,0,0.08) 4px
      );
      pointer-events: none;
      z-index: 9999;
    }

    /* GRID bg */
    body::after {
      content: '';
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      background-image:
        linear-gradient(rgba(0,245,255,0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0,245,255,0.03) 1px, transparent 1px);
      background-size: 50px 50px;
      pointer-events: none;
      z-index: 0;
    }

    /* NAV */
    nav {
      position: fixed;
      top: 0; width: 100%;
      padding: 16px 40px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      background: rgba(2,4,8,0.85);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--border);
      z-index: 100;
    }

    .nav-logo {
      font-family: 'Orbitron', monospace;
      font-weight: 900;
      font-size: 1.3rem;
      color: var(--cyan);
      text-shadow: var(--glow-cyan);
      letter-spacing: 2px;
    }

    .nav-logo span { color: var(--magenta); }

    nav ul {
      list-style: none;
      display: flex;
      gap: 32px;
    }

    nav ul a {
      text-decoration: none;
      color: #7a9bb5;
      font-family: 'Share Tech Mono', monospace;
      font-size: 0.8rem;
      letter-spacing: 2px;
      text-transform: uppercase;
      transition: color 0.3s, text-shadow 0.3s;
    }

    nav ul a:hover {
      color: var(--cyan);
      text-shadow: var(--glow-cyan);
    }

    /* HERO */
    .hero {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 100px 40px 60px;
      position: relative;
      z-index: 1;
      text-align: center;
    }

    /* Banner image */
    .banner-wrapper {
      width: 100%;
      max-width: 860px;
      margin-bottom: 40px;
      border: 1px solid var(--border);
      border-radius: 4px;
      overflow: hidden;
      box-shadow: 0 0 40px rgba(0,245,255,0.12), 0 0 80px rgba(255,0,110,0.06);
      position: relative;
      animation: fadeDown 0.8s ease both;
    }

    .banner-wrapper img {
      width: 100%;
      display: block;
    }

    /* glitch corner decorations */
    .banner-wrapper::before,
    .banner-wrapper::after {
      content: '';
      position: absolute;
      width: 20px; height: 20px;
    }
    .banner-wrapper::before {
      top: -1px; left: -1px;
      border-top: 2px solid var(--cyan);
      border-left: 2px solid var(--cyan);
    }
    .banner-wrapper::after {
      bottom: -1px; right: -1px;
      border-bottom: 2px solid var(--magenta);
      border-right: 2px solid var(--magenta);
    }

    .hero-name {
      font-family: 'Orbitron', monospace;
      font-weight: 900;
      font-size: clamp(2.5rem, 7vw, 5rem);
      color: #fff;
      letter-spacing: 4px;
      animation: fadeUp 0.8s 0.2s ease both;
    }

    .hero-name .accent { color: var(--cyan); text-shadow: var(--glow-cyan); }
    .hero-name .mag { color: var(--magenta); text-shadow: var(--glow-mag); }

    .hero-tagline {
      font-family: 'Share Tech Mono', monospace;
      font-size: 1rem;
      color: var(--green);
      letter-spacing: 3px;
      margin: 12px 0 28px;
      animation: fadeUp 0.8s 0.4s ease both;
    }

    .hero-tagline::before { content: '> '; opacity: 0.5; }

    .hero-desc {
      max-width: 600px;
      font-size: 1.1rem;
      font-weight: 300;
      line-height: 1.7;
      color: #7a9bb5;
      animation: fadeUp 0.8s 0.6s ease both;
    }

    .hero-cta {
      display: flex;
      gap: 16px;
      margin-top: 36px;
      animation: fadeUp 0.8s 0.8s ease both;
      flex-wrap: wrap;
      justify-content: center;
    }

    .btn {
      padding: 12px 28px;
      font-family: 'Share Tech Mono', monospace;
      font-size: 0.85rem;
      letter-spacing: 2px;
      text-transform: uppercase;
      text-decoration: none;
      border: 1px solid var(--cyan);
      color: var(--cyan);
      background: transparent;
      cursor: pointer;
      transition: all 0.3s;
      position: relative;
      overflow: hidden;
    }

    .btn::before {
      content: '';
      position: absolute;
      inset: 0;
      background: var(--cyan);
      transform: translateX(-101%);
      transition: transform 0.3s;
      z-index: -1;
    }

    .btn:hover { color: var(--darker); }
    .btn:hover::before { transform: translateX(0); }

    .btn.secondary {
      border-color: var(--magenta);
      color: var(--magenta);
    }
    .btn.secondary::before { background: var(--magenta); }

    /* SECTION */
    section {
      padding: 100px 40px;
      max-width: 1100px;
      margin: 0 auto;
      position: relative;
      z-index: 1;
    }

    .section-header {
      display: flex;
      align-items: center;
      gap: 16px;
      margin-bottom: 60px;
    }

    .section-num {
      font-family: 'Share Tech Mono', monospace;
      font-size: 0.75rem;
      color: var(--magenta);
      letter-spacing: 3px;
    }

    .section-title {
      font-family: 'Orbitron', monospace;
      font-weight: 700;
      font-size: 1.8rem;
      color: #fff;
      letter-spacing: 3px;
    }

    .section-line {
      flex: 1;
      height: 1px;
      background: linear-gradient(90deg, var(--border), transparent);
    }

    /* ABOUT */
    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 60px;
      align-items: start;
    }

    .about-text p {
      color: #8aa0b8;
      line-height: 1.8;
      font-size: 1.05rem;
      margin-bottom: 16px;
    }

    .about-text p strong { color: var(--cyan); }

    .terminal {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 4px;
      overflow: hidden;
    }

    .terminal-bar {
      background: #0d1627;
      padding: 10px 16px;
      display: flex;
      align-items: center;
      gap: 8px;
      border-bottom: 1px solid var(--border);
    }

    .dot { width: 10px; height: 10px; border-radius: 50%; }
    .dot.r { background: #ff5f57; }
    .dot.y { background: #febc2e; }
    .dot.g { background: #28c840; }

    .terminal-title {
      font-family: 'Share Tech Mono', monospace;
      font-size: 0.7rem;
      color: #4a6080;
      margin-left: 8px;
      letter-spacing: 1px;
    }

    .terminal-body {
      padding: 20px;
      font-family: 'Share Tech Mono', monospace;
      font-size: 0.82rem;
      line-height: 2;
    }

    .t-line { display: flex; gap: 10px; }
    .t-prompt { color: var(--green); }
    .t-cmd { color: #c8d8e8; }
    .t-out { color: var(--cyan); padding-left: 20px; }
    .t-out.mag { color: var(--magenta); }
    .t-cursor { display: inline-block; width: 8px; height: 14px; background: var(--cyan); animation: blink 1s step-end infinite; vertical-align: middle; }

    /* SKILLS */
    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 24px;
    }

    .skill-card {
      background: var(--card);
      border: 1px solid var(--border);
      padding: 28px;
      position: relative;
      transition: border-color 0.3s, box-shadow 0.3s;
      overflow: hidden;
    }

    .skill-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0;
      width: 3px; height: 100%;
      background: var(--cyan);
      transform: scaleY(0);
      transform-origin: bottom;
      transition: transform 0.3s;
    }

    .skill-card:hover { border-color: rgba(0,245,255,0.3); box-shadow: var(--glow-cyan); }
    .skill-card:hover::before { transform: scaleY(1); }

    .skill-card.mag::before { background: var(--magenta); }
    .skill-card.mag:hover { border-color: rgba(255,0,110,0.3); box-shadow: var(--glow-mag); }
    .skill-card.green::before { background: var(--green); }
    .skill-card.green:hover { border-color: rgba(57,255,20,0.3); box-shadow: 0 0 20px rgba(57,255,20,0.4); }

    .skill-icon {
      font-size: 1.8rem;
      margin-bottom: 14px;
    }

    .skill-name {
      font-family: 'Orbitron', monospace;
      font-size: 0.85rem;
      font-weight: 700;
      color: var(--cyan);
      letter-spacing: 2px;
      margin-bottom: 10px;
    }

    .skill-card.mag .skill-name { color: var(--magenta); }
    .skill-card.green .skill-name { color: var(--green); }

    .skill-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 12px;
    }

    .tag {
      font-family: 'Share Tech Mono', monospace;
      font-size: 0.7rem;
      padding: 4px 10px;
      border: 1px solid var(--border);
      color: #5a7a94;
      letter-spacing: 1px;
    }

    /* PROJECTS */
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
      gap: 24px;
    }

    .project-card {
      background: var(--card);
      border: 1px solid var(--border);
      padding: 28px;
      transition: all 0.3s;
      position: relative;
      overflow: hidden;
    }

    .project-card::after {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(135deg, rgba(0,245,255,0.03), transparent 60%);
      opacity: 0;
      transition: opacity 0.3s;
    }

    .project-card:hover { border-color: rgba(0,245,255,0.25); transform: translateY(-4px); box-shadow: 0 20px 40px rgba(0,0,0,0.4), var(--glow-cyan); }
    .project-card:hover::after { opacity: 1; }

    .project-top {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      margin-bottom: 16px;
    }

    .project-label {
      font-family: 'Share Tech Mono', monospace;
      font-size: 0.7rem;
      color: var(--magenta);
      letter-spacing: 2px;
      text-transform: uppercase;
    }

    .project-links { display: flex; gap: 12px; }

    .project-links a {
      color: #4a6080;
      font-size: 1.1rem;
      text-decoration: none;
      transition: color 0.3s;
    }

    .project-links a:hover { color: var(--cyan); }

    .project-title {
      font-family: 'Orbitron', monospace;
      font-size: 1.1rem;
      font-weight: 700;
      color: #e0eaf4;
      margin-bottom: 10px;
    }

    .project-desc {
      color: #5a7a94;
      font-size: 0.95rem;
      line-height: 1.6;
      margin-bottom: 16px;
    }

    /* CONTACT */
    .contact-wrapper {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 60px;
      align-items: center;
    }

    .contact-text h3 {
      font-family: 'Orbitron', monospace;
      font-size: 1.5rem;
      color: #fff;
      margin-bottom: 16px;
    }

    .contact-text p {
      color: #5a7a94;
      line-height: 1.8;
      margin-bottom: 28px;
    }

    .social-links {
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .social-link {
      display: flex;
      align-items: center;
      gap: 16px;
      padding: 14px 20px;
      background: var(--card);
      border: 1px solid var(--border);
      text-decoration: none;
      color: #7a9bb5;
      font-family: 'Share Tech Mono', monospace;
      font-size: 0.85rem;
      letter-spacing: 1px;
      transition: all 0.3s;
    }

    .social-link:hover {
      border-color: var(--cyan);
      color: var(--cyan);
      box-shadow: var(--glow-cyan);
      padding-left: 28px;
    }

    .social-link .s-icon { font-size: 1.2rem; }
    .social-link .s-arr { margin-left: auto; opacity: 0; transition: opacity 0.3s; }
    .social-link:hover .s-arr { opacity: 1; }

    /* FOOTER */
    footer {
      text-align: center;
      padding: 40px;
      border-top: 1px solid var(--border);
      font-family: 'Share Tech Mono', monospace;
      font-size: 0.75rem;
      color: #2a4060;
      letter-spacing: 2px;
      position: relative;
      z-index: 1;
    }

    footer span { color: var(--magenta); }

    /* ANIMATIONS */
    @keyframes fadeDown {
      from { opacity: 0; transform: translateY(-30px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    @keyframes blink {
      50% { opacity: 0; }
    }

    @keyframes glitch {
      0%, 100% { clip-path: none; transform: none; }
      20% { clip-path: polygon(0 20%, 100% 20%, 100% 25%, 0 25%); transform: translateX(-3px); }
      40% { clip-path: polygon(0 60%, 100% 60%, 100% 65%, 0 65%); transform: translateX(3px); }
      60% { clip-path: polygon(0 40%, 100% 40%, 100% 50%, 0 50%); transform: translateX(-2px); }
      80% { clip-path: none; transform: translateX(2px); }
    }

    .glitch-hover:hover { animation: glitch 0.4s steps(1) 1; }

    /* RESPONSIVE */
    @media (max-width: 768px) {
      nav { padding: 14px 20px; }
      nav ul { gap: 16px; }
      .about-grid, .contact-wrapper { grid-template-columns: 1fr; }
      section { padding: 70px 20px; }
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav>
    <div class="nav-logo"><span>R3</span>lva</div>
    <ul>
      <li><a href="#about">Sobre mí</a></li>
      <li><a href="#skills">Skills</a></li>
      <li><a href="#projects">Proyectos</a></li>
      <li><a href="#contact">Contacto</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <div class="hero">
    <div class="banner-wrapper">
      <img src="https://i.imgur.com/ty5K6aR.png" alt="Relva Banner" onerror="this.style.display='none'"/>
    </div>

    <h1 class="hero-name glitch-hover"><span class="mag">R3</span><span class="accent">lva</span></h1>
    <p class="hero-tagline">Backend Developer · Ethical Hacker · Purple Team</p>
    <p class="hero-desc">
      Especialista en seguridad ofensiva y defensiva. Construyo sistemas robustos y los rompo para hacerlos más fuertes. Pentesting, análisis de vulnerabilidades y desarrollo backend son mi campo de batalla.
    </p>
    <div class="hero-cta">
      <a href="#projects" class="btn">Ver Proyectos</a>
      <a href="#contact" class="btn secondary">Contactar</a>
    </div>
  </div>

  <!-- ABOUT -->
  <section id="about">
    <div class="section-header">
      <span class="section-num">01 //</span>
      <h2 class="section-title">SOBRE MÍ</h2>
      <div class="section-line"></div>
    </div>

    <div class="about-grid">
      <div class="about-text">
        <p>Soy <strong>Relva</strong>, desarrollador backend y entusiasta de la ciberseguridad con enfoque en el equipo púrpura — combinando mentalidad ofensiva (Red Team) y defensiva (Blue Team).</p>
        <p>Me especializo en <strong>pentesting</strong>, análisis de vulnerabilidades, scripting de automatización y construcción de herramientas de seguridad. Creo que para defender un sistema, primero hay que saber cómo atacarlo.</p>
        <p>Fuera de la terminal, estudio continuamente nuevas técnicas de ataque y defensa, contribuyo a proyectos open source y participo en CTFs.</p>
      </div>
      <div class="terminal">
        <div class="terminal-bar">
          <div class="dot r"></div>
          <div class="dot y"></div>
          <div class="dot g"></div>
          <span class="terminal-title">r3lva@kali ~ $</span>
        </div>
        <div class="terminal-body">
          <div class="t-line"><span class="t-prompt">$</span><span class="t-cmd">whoami</span></div>
          <div class="t-out">relva — pentester & backend dev</div>
          <div class="t-line"><span class="t-prompt">$</span><span class="t-cmd">cat focus.txt</span></div>
          <div class="t-out">→ Ethical Hacking</div>
          <div class="t-out">→ Purple Team Ops</div>
          <div class="t-out">→ Backend Security</div>
          <div class="t-line"><span class="t-prompt">$</span><span class="t-cmd">cat status.txt</span></div>
          <div class="t-out mag">[ DISPONIBLE PARA PROYECTOS ]</div>
          <div class="t-line"><span class="t-prompt">$</span><span class="t-cmd"><span class="t-cursor"></span></span></div>
        </div>
      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section id="skills">
    <div class="section-header">
      <span class="section-num">02 //</span>
      <h2 class="section-title">ARSENAL</h2>
      <div class="section-line"></div>
    </div>

    <div class="skills-grid">
      <div class="skill-card">
        <div class="skill-icon">🔓</div>
        <div class="skill-name">PENTESTING</div>
        <p style="color:#5a7a94; font-size:0.9rem;">Pruebas de penetración en redes, aplicaciones web y sistemas. Identificación y explotación de vulnerabilidades.</p>
        <div class="skill-tags">
          <span class="tag">Metasploit</span>
          <span class="tag">Burp Suite</span>
          <span class="tag">Nmap</span>
          <span class="tag">SQLMap</span>
        </div>
      </div>

      <div class="skill-card mag">
        <div class="skill-icon">🛡️</div>
        <div class="skill-name">PURPLE TEAM</div>
        <p style="color:#5a7a94; font-size:0.9rem;">Integración de técnicas ofensivas y defensivas. SIEM, análisis de logs, threat hunting y respuesta a incidentes.</p>
        <div class="skill-tags">
          <span class="tag">MITRE ATT&CK</span>
          <span class="tag">Splunk</span>
          <span class="tag">Wireshark</span>
          <span class="tag">IDS/IPS</span>
        </div>
      </div>

      <div class="skill-card green">
        <div class="skill-icon">⚙️</div>
        <div class="skill-name">BACKEND DEV</div>
        <p style="color:#5a7a94; font-size:0.9rem;">Desarrollo de APIs, scripts de automatización y herramientas de seguridad personalizadas.</p>
        <div class="skill-tags">
          <span class="tag">Python</span>
          <span class="tag">Node.js</span>
          <span class="tag">Bash</span>
          <span class="tag">Docker</span>
        </div>
      </div>

      <div class="skill-card">
        <div class="skill-icon">🕵️</div>
        <div class="skill-name">OSINT</div>
        <p style="color:#5a7a94; font-size:0.9rem;">Recolección de inteligencia en fuentes abiertas. Reconocimiento pasivo y análisis de superficie de ataque.</p>
        <div class="skill-tags">
          <span class="tag">Maltego</span>
          <span class="tag">Shodan</span>
          <span class="tag">theHarvester</span>
          <span class="tag">Recon-ng</span>
        </div>
      </div>

      <div class="skill-card mag">
        <div class="skill-icon">🌐</div>
        <div class="skill-name">WEB SECURITY</div>
        <p style="color:#5a7a94; font-size:0.9rem;">Análisis y explotación de vulnerabilidades OWASP Top 10. XSS, SQLi, SSRF, broken auth y más.</p>
        <div class="skill-tags">
          <span class="tag">OWASP</span>
          <span class="tag">FFUF</span>
          <span class="tag">Nikto</span>
          <span class="tag">ZAP</span>
        </div>
      </div>

      <div class="skill-card green">
        <div class="skill-icon">🐧</div>
        <div class="skill-name">LINUX / SCRIPTING</div>
        <p style="color:#5a7a94; font-size:0.9rem;">Administración de sistemas Linux, automatización con scripts y hardening de servidores.</p>
        <div class="skill-tags">
          <span class="tag">Kali Linux</span>
          <span class="tag">Bash</span>
          <span class="tag">Python</span>
          <span class="tag">Cron</span>
        </div>
      </div>
    </div>
  </section>

  <!-- PROJECTS -->
  <section id="projects">
    <div class="section-header">
      <span class="section-num">03 //</span>
      <h2 class="section-title">PROYECTOS</h2>
      <div class="section-line"></div>
    </div>

    <div class="projects-grid">
      <div class="project-card">
        <div class="project-top">
          <span class="project-label">// Tool</span>
          <div class="project-links">
            <a href="https://github.com/R3lva" title="GitHub">⌗</a>
          </div>
        </div>
        <h3 class="project-title">NetRecon Tool</h3>
        <p class="project-desc">Herramienta de reconocimiento automatizado de redes. Escaneo de puertos, detección de servicios y generación de reportes en formato HTML/JSON.</p>
        <div class="skill-tags">
          <span class="tag">Python</span><span class="tag">Nmap</span><span class="tag">CLI</span>
        </div>
      </div>

      <div class="project-card">
        <div class="project-top">
          <span class="project-label">// Script</span>
          <div class="project-links">
            <a href="https://github.com/R3lva" title="GitHub">⌗</a>
          </div>
        </div>
        <h3 class="project-title">LogHunter</h3>
        <p class="project-desc">Analizador de logs para detección de patrones de intrusión. Integración con alertas en tiempo real y correlación de eventos sospechosos.</p>
        <div class="skill-tags">
          <span class="tag">Python</span><span class="tag">Regex</span><span class="tag">SIEM</span>
        </div>
      </div>

      <div class="project-card">
        <div class="project-top">
          <span class="project-label">// CTF</span>
          <div class="project-links">
            <a href="https://github.com/R3lva" title="GitHub">⌗</a>
          </div>
        </div>
        <h3 class="project-title">CTF Writeups</h3>
        <p class="project-desc">Documentación detallada de resolución de desafíos CTF. Técnicas de pwn, web, criptografía y forense con explicaciones paso a paso.</p>
        <div class="skill-tags">
          <span class="tag">CTF</span><span class="tag">Writeups</span><span class="tag">HackTheBox</span>
        </div>
      </div>
    </div>

    <div style="text-align:center; margin-top: 40px;">
      <a href="https://github.com/R3lva" class="btn" target="_blank">Ver todos en GitHub</a>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact">
    <div class="section-header">
      <span class="section-num">04 //</span>
      <h2 class="section-title">CONTACTO</h2>
      <div class="section-line"></div>
    </div>

    <div class="contact-wrapper">
      <div class="contact-text">
        <h3>¿Hablamos?</h3>
        <p>Disponible para proyectos freelance, colaboraciones en seguridad, CTFs y oportunidades laborales. Si tienes un sistema que necesita ser puesto a prueba — aquí estoy.</p>
        <a href="https://github.com/R3lva" class="btn" target="_blank">github.com/R3lva</a>
      </div>

      <div class="social-links">
        <a href="https://github.com/R3lva" class="social-link" target="_blank">
          <span class="s-icon">🐙</span>
          <span>GitHub — @R3lva</span>
          <span class="s-arr">→</span>
        </a>
        <a href="#" class="social-link">
          <span class="s-icon">💬</span>
          <span>Discord — @R3lva</span>
          <span class="s-arr">→</span>
        </a>
        <a href="#" class="social-link">
          <span class="s-icon">📧</span>
          <span>Email — relva@proton.me</span>
          <span class="s-arr">→</span>
        </a>
        <a href="#" class="social-link">
          <span class="s-icon">🔗</span>
          <span>LinkedIn — Relva</span>
          <span class="s-arr">→</span>
        </a>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <p>// DESIGNED & BUILT BY <span>RELVA</span> · @R3LVA · 2025 //</p>
  </footer>

</body>
</html>
