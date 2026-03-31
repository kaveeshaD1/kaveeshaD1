<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GitHub Profile — Tech Stack</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --border: #1e1e2e;
    --accent1: #7fff6e;
    --accent2: #ff6eb4;
    --accent3: #6eb4ff;
    --accent4: #ffcd6e;
    --text: #e8e8f0;
    --muted: #555570;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    min-height: 100vh;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    padding: 40px 20px;
    overflow-x: hidden;
  }

  /* Animated background grid */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(var(--border) 1px, transparent 1px),
      linear-gradient(90deg, var(--border) 1px, transparent 1px);
    background-size: 48px 48px;
    opacity: 0.4;
    pointer-events: none;
    z-index: 0;
  }

  .wrapper {
    position: relative;
    z-index: 1;
    width: 100%;
    max-width: 860px;
  }

  /* ── Profile header ── */
  .profile-header {
    display: flex;
    align-items: center;
    gap: 28px;
    margin-bottom: 48px;
    animation: slideDown .6s ease both;
  }

  .avatar-ring {
    position: relative;
    flex-shrink: 0;
  }

  .avatar-ring::before {
    content: '';
    position: absolute;
    inset: -3px;
    border-radius: 50%;
    background: conic-gradient(var(--accent1), var(--accent2), var(--accent3), var(--accent4), var(--accent1));
    animation: spin 4s linear infinite;
    z-index: -1;
  }

  .avatar {
    width: 80px; height: 80px;
    border-radius: 50%;
    background: var(--surface);
    border: 3px solid var(--bg);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 32px;
    position: relative;
  }

  .profile-text h1 {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(22px, 4vw, 32px);
    letter-spacing: -0.5px;
    line-height: 1.1;
  }

  .profile-text h1 span {
    background: linear-gradient(90deg, var(--accent1), var(--accent3));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .profile-text p {
    font-family: 'Space Mono', monospace;
    font-size: 12px;
    color: var(--muted);
    margin-top: 6px;
  }

  .status-badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    background: rgba(127,255,110,.08);
    border: 1px solid rgba(127,255,110,.25);
    color: var(--accent1);
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    padding: 4px 10px;
    border-radius: 20px;
    margin-top: 10px;
  }

  .status-badge::before {
    content: '';
    width: 7px; height: 7px;
    border-radius: 50%;
    background: var(--accent1);
    animation: pulse 1.5s ease-in-out infinite;
  }

  /* ── Stats row ── */
  .stats {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
    margin-bottom: 44px;
    animation: slideDown .65s ease both;
  }

  .stat-card {
    flex: 1;
    min-width: 130px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 16px 20px;
    position: relative;
    overflow: hidden;
    transition: transform .2s, border-color .2s;
  }

  .stat-card:hover {
    transform: translateY(-3px);
    border-color: var(--accent3);
  }

  .stat-card::after {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent3), var(--accent2));
  }

  .stat-card .num {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 26px;
    line-height: 1;
    color: #fff;
  }

  .stat-card .label {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    color: var(--muted);
    margin-top: 4px;
    text-transform: uppercase;
    letter-spacing: .08em;
  }

  /* ── Section ── */
  .section {
    margin-bottom: 36px;
    animation: fadeUp .5s ease both;
  }

  .section-header {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 16px;
  }

  .section-icon {
    width: 28px; height: 28px;
    border-radius: 7px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 14px;
  }

  .section-title {
    font-weight: 800;
    font-size: 13px;
    letter-spacing: .12em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .section-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  /* ── Tag grid ── */
  .tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .tag {
    display: inline-flex;
    align-items: center;
    gap: 7px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 8px 14px;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: .06em;
    text-transform: uppercase;
    cursor: default;
    position: relative;
    overflow: hidden;
    transition: all .22s cubic-bezier(.4,0,.2,1);
  }

  .tag::before {
    content: '';
    position: absolute;
    inset: 0;
    opacity: 0;
    transition: opacity .22s;
  }

  .tag:hover {
    transform: translateY(-2px) scale(1.04);
    border-color: var(--tag-accent, var(--accent3));
    color: var(--tag-accent, var(--accent3));
    box-shadow: 0 0 16px -2px var(--tag-accent, var(--accent3));
  }

  .tag:hover::before { opacity: .07; background: var(--tag-accent, var(--accent3)); }

  .tag-dot {
    width: 8px; height: 8px;
    border-radius: 2px;
    background: var(--tag-accent, #444);
    flex-shrink: 0;
    transition: background .22s;
  }

  .tag:hover .tag-dot { background: var(--tag-accent, var(--accent3)); }

  /* colour overrides per category */
  .lang .tag   { --tag-accent: var(--accent1); }
  .front .tag  { --tag-accent: var(--accent3); }
  .back .tag   { --tag-accent: var(--accent2); }
  .css .tag    { --tag-accent: var(--accent4); }
  .tools .tag  { --tag-accent: #b06eff; }

  /* stagger */
  .tag:nth-child(1)  { animation-delay: .04s }
  .tag:nth-child(2)  { animation-delay: .08s }
  .tag:nth-child(3)  { animation-delay: .12s }
  .tag:nth-child(4)  { animation-delay: .16s }
  .tag:nth-child(5)  { animation-delay: .20s }
  .tag:nth-child(6)  { animation-delay: .24s }
  .tag:nth-child(7)  { animation-delay: .28s }
  .tag:nth-child(8)  { animation-delay: .32s }
  .tag:nth-child(9)  { animation-delay: .36s }
  .tag { animation: popIn .4s ease both; }

  /* section stagger */
  .section:nth-child(1) { animation-delay: .1s }
  .section:nth-child(2) { animation-delay: .2s }
  .section:nth-child(3) { animation-delay: .3s }
  .section:nth-child(4) { animation-delay: .4s }
  .section:nth-child(5) { animation-delay: .5s }

  /* ── Keyframes ── */
  @keyframes slideDown {
    from { opacity: 0; transform: translateY(-20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(14px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes popIn {
    from { opacity: 0; transform: scale(.85); }
    to   { opacity: 1; transform: scale(1); }
  }
  @keyframes spin { to { transform: rotate(360deg); } }
  @keyframes pulse {
    0%,100% { opacity: 1; transform: scale(1); }
    50%      { opacity: .5; transform: scale(1.4); }
  }
</style>
</head>
<body>
<div class="wrapper">

  <!-- Profile header -->
  <div class="profile-header">
    <div class="avatar-ring">
      <div class="avatar">🧑‍💻</div>
    </div>
    <div class="profile-text">
      <h1>Alex <span>Devion</span></h1>
      <p>@alexdevion · Full-Stack Engineer</p>
      <div class="status-badge">Available for work</div>
    </div>
  </div>

  <!-- Stats -->
  <div class="stats">
    <div class="stat-card">
      <div class="num">247</div>
      <div class="label">Repositories</div>
    </div>
    <div class="stat-card">
      <div class="num">1.4k</div>
      <div class="label">Followers</div>
    </div>
    <div class="stat-card">
      <div class="num">3.2k</div>
      <div class="label">Contributions</div>
    </div>
    <div class="stat-card">
      <div class="num">58</div>
      <div class="label">Stars earned</div>
    </div>
  </div>

  <!-- Languages -->
  <div class="section lang">
    <div class="section-header">
      <div class="section-icon" style="background:rgba(127,255,110,.1)">⟨/⟩</div>
      <span class="section-title">Languages</span>
      <div class="section-line"></div>
    </div>
    <div class="tags">
      <span class="tag"><span class="tag-dot"></span>Python</span>
      <span class="tag"><span class="tag-dot"></span>JavaScript</span>
      <span class="tag"><span class="tag-dot"></span>TypeScript</span>
      <span class="tag"><span class="tag-dot"></span>Dart</span>
      <span class="tag"><span class="tag-dot"></span>C#</span>
      <span class="tag"><span class="tag-dot"></span>C++</span>
      <span class="tag"><span class="tag-dot"></span>Java</span>
      <span class="tag"><span class="tag-dot"></span>PHP</span>
    </div>
  </div>

  <!-- Frontend -->
  <div class="section front">
    <div class="section-header">
      <div class="section-icon" style="background:rgba(110,180,255,.1)">◈</div>
      <span class="section-title">Frontend</span>
      <div class="section-line"></div>
    </div>
    <div class="tags">
      <span class="tag"><span class="tag-dot"></span>React</span>
      <span class="tag"><span class="tag-dot"></span>Next.js</span>
      <span class="tag"><span class="tag-dot"></span>Flutter</span>
      <span class="tag"><span class="tag-dot"></span>Redux</span>
      <span class="tag"><span class="tag-dot"></span>HTML5</span>
      <span class="tag"><span class="tag-dot"></span>CSS3</span>
      <span class="tag"><span class="tag-dot"></span>Sass</span>
      <span class="tag"><span class="tag-dot"></span>Material UI</span>
    </div>
  </div>

  <!-- Backend -->
  <div class="section back">
    <div class="section-header">
      <div class="section-icon" style="background:rgba(255,110,180,.1)">⚙</div>
      <span class="section-title">Backend</span>
      <div class="section-line"></div>
    </div>
    <div class="tags">
      <span class="tag"><span class="tag-dot"></span>Node.js</span>
      <span class="tag"><span class="tag-dot"></span>Express.js</span>
      <span class="tag"><span class="tag-dot"></span>Django</span>
      <span class="tag"><span class="tag-dot"></span>Laravel</span>
      <span class="tag"><span class="tag-dot"></span>Spring Boot</span>
      <span class="tag"><span class="tag-dot"></span>MySQL</span>
      <span class="tag"><span class="tag-dot"></span>ASP.NET</span>
    </div>
  </div>

  <!-- CSS Frameworks -->
  <div class="section css">
    <div class="section-header">
      <div class="section-icon" style="background:rgba(255,205,110,.1)">✦</div>
      <span class="section-title">CSS Frameworks</span>
      <div class="section-line"></div>
    </div>
    <div class="tags">
      <span class="tag"><span class="tag-dot"></span>Tailwind CSS</span>
      <span class="tag"><span class="tag-dot"></span>Bootstrap</span>
    </div>
  </div>

  <!-- Tools -->
  <div class="section tools">
    <div class="section-header">
      <div class="section-icon" style="background:rgba(176,110,255,.1)">⊞</div>
      <span class="section-title">Tools & Platforms</span>
      <div class="section-line"></div>
    </div>
    <div class="tags">
      <span class="tag"><span class="tag-dot"></span>Git</span>
      <span class="tag"><span class="tag-dot"></span>Docker</span>
      <span class="tag"><span class="tag-dot"></span>VS Code</span>
      <span class="tag"><span class="tag-dot"></span>Figma</span>
      <span class="tag"><span class="tag-dot"></span>Postman</span>
      <span class="tag"><span class="tag-dot"></span>Linux</span>
    </div>
  </div>

</div>
</body>
</html>
