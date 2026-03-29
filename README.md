<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>crtrace</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet" />
  <style>
    :root {
      --bg:      #0e0e0e;
      --surface: #141414;
      --border:  #222;
      --text:    #d4d4d4;
      --muted:   #555;
      --dim:     #333;
      --accent:  #e0e0e0;
      --mono:    'Share Tech Mono', monospace;
      --sans:    'DM Sans', sans-serif;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: var(--sans);
      font-size: 15px;
      line-height: 1.7;
      overflow-x: hidden;
    }

    /* NAV */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 1.2rem 3rem;
      border-bottom: 1px solid var(--border);
      background: rgba(14,14,14,0.92);
      backdrop-filter: blur(8px);
    }
    .nav-logo {
      font-family: var(--mono);
      font-size: 0.78rem;
      color: var(--muted);
      letter-spacing: 0.15em;
      text-transform: uppercase;
    }
    nav ul {
      list-style: none;
      display: flex;
      gap: 2.5rem;
    }
    nav ul a {
      font-family: var(--mono);
      font-size: 0.7rem;
      color: var(--muted);
      text-decoration: none;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      transition: color 0.2s;
    }
    nav ul a:hover { color: var(--text); }

    /* HERO */
    .hero {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 10rem 3rem 6rem;
      max-width: 900px;
    }
    .hero-tag {
      font-family: var(--mono);
      font-size: 0.7rem;
      color: var(--muted);
      letter-spacing: 0.2em;
      text-transform: uppercase;
      margin-bottom: 2rem;
    }
    .hero h1 {
      font-family: var(--sans);
      font-weight: 300;
      font-size: clamp(2.8rem, 6vw, 5rem);
      line-height: 1.1;
      letter-spacing: -0.02em;
      color: var(--accent);
      margin-bottom: 2rem;
    }
    .hero h1 em {
      font-style: normal;
      color: var(--muted);
    }
    .hero-desc {
      font-family: var(--mono);
      font-size: 0.8rem;
      color: var(--muted);
      max-width: 480px;
      line-height: 2;
      margin-bottom: 3rem;
    }
    .hero-cta {
      display: flex;
      gap: 1rem;
    }

    /* BUTTONS */
    .btn {
      font-family: var(--mono);
      font-size: 0.7rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      padding: 0.7rem 1.6rem;
      text-decoration: none;
      border: 1px solid;
      transition: all 0.2s;
      cursor: pointer;
      display: inline-block;
    }
    .btn-solid {
      background: var(--text);
      border-color: var(--text);
      color: var(--bg);
    }
    .btn-solid:hover {
      background: transparent;
      color: var(--text);
    }
    .btn-ghost {
      background: transparent;
      border-color: var(--border);
      color: var(--muted);
    }
    .btn-ghost:hover {
      border-color: var(--dim);
      color: var(--text);
    }

    /* TERMINAL */
    .terminal {
      background: var(--surface);
      border: 1px solid var(--border);
      margin-top: 4rem;
      padding: 1.5rem;
      font-family: var(--mono);
      font-size: 0.75rem;
      line-height: 2;
      max-width: 520px;
    }
    .t-prompt { color: var(--dim); }
    .t-cmd    { color: var(--text); }
    .t-out    { color: var(--muted); padding-left: 1rem; }
    .t-cursor {
      display: inline-block;
      width: 7px;
      height: 0.9em;
      background: var(--muted);
      vertical-align: text-bottom;
      animation: blink 1.1s step-end infinite;
    }
    @keyframes blink { 50% { opacity: 0; } }

    /* DIVIDER */
    .divider {
      width: 100%;
      height: 1px;
      background: var(--border);
    }

    /* SECTIONS */
    section {
      padding: 6rem 3rem;
      max-width: 900px;
      margin: 0 auto;
    }
    .section-label {
      font-family: var(--mono);
      font-size: 0.65rem;
      letter-spacing: 0.25em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 3rem;
      display: flex;
      align-items: center;
      gap: 1rem;
    }
    .section-label::after {
      content: '';
      flex: 1;
      height: 1px;
      background: var(--border);
    }

    /* ABOUT */
    .about-text p {
      color: var(--muted);
      font-size: 0.95rem;
      font-weight: 300;
      margin-bottom: 1.2rem;
      max-width: 600px;
    }
    .about-text strong { color: var(--text); font-weight: 500; }

    /* SKILLS */
    .skills-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 3rem;
    }
    .skill-group-label {
      font-family: var(--mono);
      font-size: 0.65rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 1.5rem;
      padding-bottom: 0.8rem;
      border-bottom: 1px solid var(--border);
    }
    .skill-list {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 0.9rem;
    }
    .skill-list li {
      font-family: var(--mono);
      font-size: 0.78rem;
      color: var(--muted);
      display: flex;
      align-items: center;
      gap: 0.8rem;
      transition: color 0.2s;
    }
    .skill-list li:hover { color: var(--text); }
    .skill-list li::before {
      content: '';
      width: 4px;
      height: 4px;
      border-radius: 50%;
      background: var(--dim);
      flex-shrink: 0;
    }

    /* CROSBREAKER */
    .cros-block {
      border: 1px solid var(--border);
      padding: 2.5rem;
    }
    .cros-name {
      font-family: var(--mono);
      font-size: 1.1rem;
      color: var(--text);
      letter-spacing: 0.08em;
      text-transform: uppercase;
      margin-bottom: 1.2rem;
    }
    .cros-desc {
      font-size: 0.9rem;
      font-weight: 300;
      color: var(--muted);
      max-width: 520px;
      line-height: 1.9;
      margin-bottom: 2rem;
    }
    .cros-actions { display: flex; gap: 1rem; flex-wrap: wrap; }
    .cros-meta {
      margin-top: 2rem;
      padding-top: 1.5rem;
      border-top: 1px solid var(--border);
      display: flex;
      gap: 2.5rem;
      flex-wrap: wrap;
    }
    .cros-meta-key {
      font-family: var(--mono);
      font-size: 0.6rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--dim);
      display: block;
      margin-bottom: 0.2rem;
    }
    .cros-meta-val {
      font-family: var(--mono);
      font-size: 0.75rem;
      color: var(--muted);
    }

    /* FOOTER */
    footer {
      border-top: 1px solid var(--border);
      padding: 1.8rem 3rem;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      flex-wrap: wrap;
      gap: 2rem;
    }
    .footer-left, .footer-right {
      font-family: var(--mono);
      font-size: 0.65rem;
      color: var(--dim);
      letter-spacing: 0.1em;
    }

    /* ANIMATIONS */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(18px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    .hero > * { animation: fadeUp 0.6s ease both; }
    .hero > *:nth-child(1) { animation-delay: 0.05s; }
    .hero > *:nth-child(2) { animation-delay: 0.18s; }
    .hero > *:nth-child(3) { animation-delay: 0.3s; }
    .hero > *:nth-child(4) { animation-delay: 0.42s; }
    .hero > *:nth-child(5) { animation-delay: 0.55s; }

    /* RESPONSIVE */
    @media (max-width: 640px) {
      nav { padding: 1rem 1.5rem; }
      nav ul { display: none; }
      .hero, section { padding-left: 1.5rem; padding-right: 1.5rem; }
      .skills-grid { grid-template-columns: 1fr; gap: 2rem; }
      footer { padding: 1.5rem; }
    }
  </style>
</head>
<body>

<nav>
  <div class="nav-logo">crtrace</div>
  <ul>
    <li><a href="#about">about</a></li>
    <li><a href="#skills">skills</a></li>
    <li><a href="#crosbreaker">crosbreaker</a></li>
  </ul>
</nav>

<div class="hero">
  <div class="hero-tag">Security Researcher · ChromeOS · Android</div>
  <h1>About me.</h1>
  <p class="hero-desc">
    Beginner developer and security researcher. ChromeOS and Android.
  </p>
  <div class="hero-cta">
    <a href="#skills" class="btn btn-solid">Skills</a>
    <a href="#crosbreaker" class="btn btn-ghost">Crosbreaker</a>
  </div>

</div>

<div class="divider"></div>

<section id="about">
  <div class="section-label">About</div>
  <div class="about-text">
    <p>
      I'm a <strong>Google enthusiast</strong> focused on ChromeOS and Android.
    </p>
    <p>
      My work is in <strong>beginner Chromebook development</strong> and <strong>security research</strong>.
    </p>
    <p>
      I'm interested in <strong>Google's Vulnerability Reward Program (VRP)</strong>, researching security bugs in ChromeOS and Android and responsibly reporting them to Google.
    </p>
    <p>
      I also work with <strong>Chromebook unenrollment</strong>, exploring how managed and enterprise-enrolled devices can be freed from policy restrictions.
    </p>
    <p>
      Outside of tech, I follow <strong>politics and economics</strong> closely.
    </p>
  </div>
</section>

<div class="divider"></div>

<section id="skills">
  <div class="section-label">Skills</div>
  <div class="skills-grid">
    <div>
      <div class="skill-group-label">Proficient</div>
      <ul class="skill-list">
        <li>Bash scripting &amp; automation</li>
        <li>Beginner Chromebook development</li>
        <li>ChromeOS security research</li>
        <li>Firmware &amp; kernel exploration</li>
        <li>Research — Politics &amp; Economics</li>
      </ul>
    </div>
    <div>
      <div class="skill-group-label">In Progress</div>
      <ul class="skill-list">
        <li>HTML, CSS &amp; JavaScript</li>
        <li>Reverse Engineering</li>
        <li>C and C++</li>
        <li>Rust</li>
        <li>Assembly</li>
        <li>Low-level programming</li>
      </ul>
    </div>
  </div>
</section>

<div class="divider"></div>

<section id="crosbreaker">
  <div class="section-label">Community</div>
  <div class="cros-block">
    <div class="cros-name">Crosbreaker</div>
    <p class="cros-desc">
      A community for people who push ChromeOS and Android hardware past its
      designed limits. Security researchers, low-level tinkerers, and Google
      enthusiasts — all in one place. I'm a member. Come see what we're
      working on, and join us if it sounds like your kind of thing.
    </p>
    <div class="cros-actions">
      <a href="https://crosbreaker.dev" target="_blank" rel="noopener" class="btn btn-solid">Visit crosbreaker.dev</a>
      <a href="https://discord.gg/crosbreaker-1375357349425971231" target="_blank" rel="noopener" class="btn btn-ghost">Join the Discord</a>
    </div>
    <div class="cros-meta">
      <div>
        <span class="cros-meta-key">Website</span>
        <span class="cros-meta-val">crosbreaker.dev</span>
      </div>
      <div>
        <span class="cros-meta-key">Community</span>
        <span class="cros-meta-val">Discord</span>
      </div>
      <div>
        <span class="cros-meta-key">Status</span>
        <span class="cros-meta-val">Active member</span>
      </div>
    </div>
  </div>
</section>

<footer>
  <div class="footer-left">crtrace — google enthusiast &amp; low-level dev</div>
  <div class="footer-right">member of crosbreaker</div>
</footer>

</body>
</html>
