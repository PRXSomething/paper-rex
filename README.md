<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>PAPER REX - How We Won Our First Trophy | VCT Masters Toronto Documentary Showcase</title>
  
  <!-- Fonts & Icons -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Teko:wght@500;700&family=Space+Grotesk:wght@400;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  
  <!-- Canvas Confetti Library for Hype Button -->
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

  <style>
    :root {
      --prx-pink: #FF4655;
      --prx-cyan: #00F0FF;
      --prx-yellow: #FFE600;
      --bg-dark: #07090e;
      --bg-card: rgba(18, 22, 33, 0.85);
      --bg-card-hover: rgba(26, 32, 48, 0.95);
      --text-main: #FFFFFF;
      --text-muted: #A0AABF;
      --border-glow: rgba(255, 70, 85, 0.3);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background-color: var(--bg-dark);
      color: var(--text-main);
      font-family: 'Space Grotesk', sans-serif;
      min-height: 100vh;
      overflow-x: hidden;
      position: relative;
    }

    /* --- BACKGROUND PATTERNS & PRX LOGO OVERLAYS --- */
    .bg-grid {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background-image: 
        linear-gradient(to right, rgba(255, 255, 255, 0.03) 1px, transparent 1px),
        linear-gradient(to bottom, rgba(255, 255, 255, 0.03) 1px, transparent 1px);
      background-size: 40px 40px;
      z-index: 0;
      pointer-events: none;
    }

    .bg-slash-pattern {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background: repeating-linear-gradient(
        -45deg,
        rgba(255, 70, 85, 0.02),
        rgba(255, 70, 85, 0.02) 15px,
        transparent 15px,
        transparent 30px
      );
      z-index: 0;
      pointer-events: none;
    }

    .bg-watermark-logo {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 80vw;
      max-width: 900px;
      opacity: 0.03;
      z-index: 0;
      pointer-events: none;
      filter: drop-shadow(0 0 20px var(--prx-pink));
    }

    .floating-logo {
      position: fixed;
      z-index: 0;
      pointer-events: none;
      opacity: 0.08;
      filter: drop-shadow(0 0 15px var(--prx-cyan));
      animation: floatAnim 12s infinite ease-in-out alternate;
    }

    .floating-logo-1 {
      top: 10%;
      left: 3%;
      width: 180px;
      animation-duration: 10s;
    }

    .floating-logo-2 {
      bottom: 15%;
      right: 3%;
      width: 220px;
      animation-duration: 14s;
      animation-delay: -3s;
    }

    @keyframes floatAnim {
      0% { transform: translateY(0) rotate(0deg); }
      50% { transform: translateY(-25px) rotate(4deg); }
      100% { transform: translateY(15px) rotate(-3deg); }
    }

    /* --- CONTAINER & LAYOUT --- */
    .app-container {
      position: relative;
      z-index: 1;
      max-width: 1300px;
      margin: 0 auto;
      padding: 20px 24px 80px;
    }

    /* --- HEADER / HERO --- */
    header {
      text-align: center;
      padding: 40px 0 30px;
      position: relative;
    }

    .brand-badge {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      background: rgba(255, 70, 85, 0.15);
      border: 1px solid var(--prx-pink);
      padding: 6px 16px;
      border-radius: 20px;
      color: var(--prx-pink);
      font-weight: 700;
      font-size: 0.9rem;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 15px;
      box-shadow: 0 0 15px rgba(255, 70, 85, 0.2);
    }

    .brand-badge svg {
      width: 18px;
      height: 18px;
      fill: var(--prx-pink);
    }

    h1 {
      font-family: 'Teko', sans-serif;
      font-size: clamp(3rem, 7vw, 5.5rem);
      line-height: 0.9;
      text-transform: uppercase;
      letter-spacing: 2px;
      background: linear-gradient(135deg, #FFF 40%, var(--prx-pink) 75%, var(--prx-cyan) 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      text-shadow: 0 0 30px rgba(255, 70, 85, 0.3);
      margin-bottom: 10px;
    }

    .subtitle {
      color: var(--text-muted);
      font-size: 1.1rem;
      max-width: 650px;
      margin: 0 auto 20px;
    }

    /* --- YOUTUBE DIRECT ACTION BUTTON --- */
    .yt-watch-btn {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      background: #FF0000;
      color: #FFFFFF;
      text-decoration: none;
      font-family: 'Space Grotesk', sans-serif;
      font-weight: 700;
      font-size: 0.95rem;
      padding: 10px 22px;
      border-radius: 30px;
      box-shadow: 0 0 20px rgba(255, 0, 0, 0.4);
      transition: all 0.2s ease;
      margin-bottom: 30px;
    }

    .yt-watch-btn:hover {
      background: #CC0000;
      transform: translateY(-2px);
      box-shadow: 0 0 30px rgba(255, 0, 0, 0.7);
    }

    /* --- QUICK STATS --- */
    .stats-bar {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 20px;
      margin-bottom: 40px;
    }

    .stat-card {
      background: var(--bg-card);
      border: 1px solid rgba(255, 255, 255, 0.08);
      padding: 12px 24px;
      border-radius: 8px;
      min-width: 140px;
      text-align: center;
      backdrop-filter: blur(10px);
      transition: transform 0.2s, border-color 0.2s;
    }

    .stat-card:hover {
      transform: translateY(-3px);
      border-color: var(--prx-pink);
    }

    .stat-value {
      font-family: 'Teko', sans-serif;
      font-size: 2rem;
      font-weight: 700;
      color: var(--prx-cyan);
      line-height: 1;
    }

    .stat-label {
      font-size: 0.8rem;
      color: var(--text-muted);
      text-transform: uppercase;
      letter-spacing: 1px;
    }

    /* --- VIDEO PLAYER & TIMELINE LAYOUT --- */
    .main-grid {
      display: grid;
      grid-template-columns: 1fr;
      gap: 30px;
      margin-bottom: 50px;
    }

    @media (min-width: 992px) {
      .main-grid {
        grid-template-columns: 2.2fr 1fr;
      }
    }

    .video-container {
      background: var(--bg-card);
      border: 1px solid var(--border-glow);
      border-radius: 12px;
      overflow: hidden;
      box-shadow: 0 10px 40px rgba(0, 0, 0, 0.6);
      backdrop-filter: blur(10px);
    }

    .iframe-wrapper {
      position: relative;
      padding-bottom: 56.25%;
      height: 0;
      background: #000;
    }

    .iframe-wrapper iframe {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      border: none;
    }

    .video-info-bar {
      padding: 16px 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border-top: 1px solid rgba(255, 255, 255, 0.08);
      background: rgba(10, 14, 22, 0.8);
      flex-wrap: wrap;
      gap: 10px;
    }

    .now-playing {
      display: flex;
      align-items: center;
      gap: 10px;
      font-size: 0.95rem;
      font-weight: 600;
    }

    .pulse-dot {
      width: 10px;
      height: 10px;
      background-color: var(--prx-pink);
      border-radius: 50%;
      box-shadow: 0 0 10px var(--prx-pink);
      animation: pulse 1.5s infinite;
    }

    @keyframes pulse {
      0% { opacity: 0.4; transform: scale(0.8); }
      50% { opacity: 1; transform: scale(1.2); }
      100% { opacity: 0.4; transform: scale(0.8); }
    }

    .yt-link-text {
      color: var(--prx-cyan);
      text-decoration: none;
      font-size: 0.85rem;
      font-weight: 600;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      transition: color 0.2s;
    }

    .yt-link-text:hover {
      color: #FFF;
      text-decoration: underline;
    }

    /* --- CHAPTERS / TIMELINE PANEL --- */
    .chapters-panel {
      background: var(--bg-card);
      border: 1px solid rgba(255, 255, 255, 0.08);
      border-radius: 12px;
      padding: 20px;
      display: flex;
      flex-direction: column;
      max-height: 520px;
      backdrop-filter: blur(10px);
    }

    .section-title {
      font-family: 'Teko', sans-serif;
      font-size: 1.8rem;
      letter-spacing: 1px;
      text-transform: uppercase;
      margin-bottom: 15px;
      display: flex;
      align-items: center;
      gap: 10px;
      color: #FFF;
    }

    .section-title i {
      color: var(--prx-pink);
    }

    .chapters-list {
      display: flex;
      flex-direction: column;
      gap: 10px;
      overflow-y: auto;
      padding-right: 5px;
    }

    .chapters-list::-webkit-scrollbar {
      width: 6px;
    }
    .chapters-list::-webkit-scrollbar-thumb {
      background: var(--prx-pink);
      border-radius: 4px;
    }

    .chapter-btn {
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: rgba(255, 255, 255, 0.03);
      border: 1px solid rgba(255, 255, 255, 0.05);
      border-left: 3px solid var(--text-muted);
      padding: 12px 14px;
      border-radius: 6px;
      color: var(--text-main);
      cursor: pointer;
      transition: all 0.2s ease;
      text-align: left;
    }

    .chapter-btn:hover {
      background: rgba(255, 70, 85, 0.1);
      border-color: var(--prx-pink);
      border-left-width: 5px;
      transform: translateX(4px);
    }

    .chapter-btn.active {
      background: rgba(255, 70, 85, 0.2);
      border-color: var(--prx-pink);
      border-left: 5px solid var(--prx-pink);
    }

    .chapter-time {
      font-family: 'Teko', sans-serif;
      font-size: 1.2rem;
      color: var(--prx-cyan);
      background: rgba(0, 240, 255, 0.1);
      padding: 2px 8px;
      border-radius: 4px;
      margin-right: 12px;
    }

    .chapter-text {
      font-weight: 600;
      font-size: 0.9rem;
      flex-grow: 1;
    }

    /* --- HYPE BUTTON / SOUNDBOARD --- */
    .hype-section {
      background: linear-gradient(135deg, rgba(255, 70, 85, 0.2) 0%, rgba(0, 240, 255, 0.1) 100%);
      border: 2px solid var(--prx-pink);
      border-radius: 12px;
      padding: 25px;
      text-align: center;
      margin-bottom: 50px;
      position: relative;
      overflow: hidden;
      box-shadow: 0 0 30px rgba(255, 70, 85, 0.2);
    }

    .hype-btn {
      background: linear-gradient(45deg, var(--prx-pink), #FF1E43);
      color: #FFF;
      font-family: 'Teko', sans-serif;
      font-size: 2.2rem;
      letter-spacing: 2px;
      text-transform: uppercase;
      padding: 12px 40px;
      border: none;
      border-radius: 50px;
      cursor: pointer;
      box-shadow: 0 0 20px rgba(255, 70, 85, 0.6);
      transition: all 0.2s ease;
      margin-top: 15px;
      display: inline-flex;
      align-items: center;
      gap: 12px;
    }

    .hype-btn:hover {
      transform: scale(1.05);
      box-shadow: 0 0 35px rgba(255, 70, 85, 0.9);
    }

    .hype-btn:active {
      transform: scale(0.98);
    }

    /* --- ROSTER SHOWCASE --- */
    .roster-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 20px;
      margin-bottom: 50px;
    }

    .player-card {
      background: var(--bg-card);
      border: 1px solid rgba(255, 255, 255, 0.08);
      border-radius: 12px;
      padding: 20px;
      position: relative;
      overflow: hidden;
      transition: all 0.3s ease;
      backdrop-filter: blur(10px);
    }

    .player-card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 4px;
      background: linear-gradient(90deg, var(--prx-pink), var(--prx-cyan));
      opacity: 0.5;
      transition: opacity 0.3s;
    }

    .player-card:hover {
      transform: translateY(-6px);
      border-color: var(--prx-pink);
      box-shadow: 0 10px 30px rgba(255, 70, 85, 0.2);
    }

    .player-card:hover::before {
      opacity: 1;
    }

    .player-header {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      margin-bottom: 12px;
    }

    .player-ign {
      font-family: 'Teko', sans-serif;
      font-size: 2.2rem;
      line-height: 1;
      color: #FFF;
    }

    .player-name {
      color: var(--text-muted);
      font-size: 0.85rem;
    }

    .player-role {
      background: rgba(255, 255, 255, 0.08);
      padding: 4px 10px;
      border-radius: 4px;
      font-size: 0.75rem;
      text-transform: uppercase;
      letter-spacing: 1px;
      color: var(--prx-cyan);
    }

    .player-quote {
      font-style: italic;
      color: #E2E8F0;
      font-size: 0.9rem;
      background: rgba(0, 0, 0, 0.3);
      padding: 10px 12px;
      border-radius: 6px;
      border-left: 2px solid var(--prx-pink);
      margin-top: 12px;
    }

    /* --- BRACKET / MATCH RECAP --- */
    .matches-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 15px;
      margin-bottom: 50px;
    }

    .match-card {
      background: var(--bg-card);
      border: 1px solid rgba(255, 255, 255, 0.08);
      border-radius: 8px;
      padding: 16px;
      text-align: center;
    }

    .match-stage {
      font-size: 0.75rem;
      color: var(--text-muted);
      text-transform: uppercase;
      letter-spacing: 1px;
      margin-bottom: 8px;
    }

    .match-versus {
      font-family: 'Teko', sans-serif;
      font-size: 1.5rem;
      margin-bottom: 6px;
    }

    .match-score {
      font-family: 'Teko', sans-serif;
      font-size: 1.8rem;
      color: var(--prx-yellow);
    }

    .match-result {
      display: inline-block;
      background: rgba(0, 240, 255, 0.15);
      color: var(--prx-cyan);
      font-size: 0.75rem;
      padding: 2px 10px;
      border-radius: 12px;
      font-weight: 700;
      margin-top: 6px;
    }

    /* --- QUOTE GENERATOR --- */
    .quote-box {
      background: var(--bg-card);
      border: 1px solid rgba(255, 255, 255, 0.08);
      border-radius: 12px;
      padding: 30px;
      text-align: center;
      margin-bottom: 50px;
      backdrop-filter: blur(10px);
    }

    .random-quote {
      font-size: 1.3rem;
      font-weight: 600;
      color: #FFF;
      margin-bottom: 10px;
      min-height: 60px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .quote-author {
      color: var(--prx-pink);
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 1px;
      margin-bottom: 20px;
    }

    .gen-btn {
      background: rgba(255, 255, 255, 0.05);
      border: 1px solid var(--prx-cyan);
      color: var(--prx-cyan);
      padding: 10px 24px;
      border-radius: 6px;
      font-family: 'Space Grotesk', sans-serif;
      font-weight: 700;
      cursor: pointer;
      transition: all 0.2s;
    }

    .gen-btn:hover {
      background: var(--prx-cyan);
      color: #000;
      box-shadow: 0 0 15px rgba(0, 240, 255, 0.5);
    }

    /* --- FOOTER --- */
    footer {
      text-align: center;
      padding-top: 40px;
      border-top: 1px solid rgba(255, 255, 255, 0.08);
      color: var(--text-muted);
      font-size: 0.9rem;
    }

    footer a {
      color: var(--prx-pink);
      text-decoration: none;
    }

    footer a:hover {
      text-decoration: underline;
    }
  </style>
</head>
<body>

  <!-- BACKGROUND PATTERNS & SVG PRX WATERMARKS -->
  <div class="bg-grid"></div>
  <div class="bg-slash-pattern"></div>

  <!-- Giant PRX Logo Watermark SVG -->
  <svg class="bg-watermark-logo" viewBox="0 0 500 500" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M100 80 L250 400 L400 80 L320 80 L250 260 L180 80 Z" fill="#FF4655" />
    <path d="M150 120 L250 340 L350 120 L300 120 L250 230 L200 120 Z" fill="#00F0FF" />
  </svg>

  <!-- Floating Ambient PRX Logos -->
  <svg class="floating-logo floating-logo-1" viewBox="0 0 500 500" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M100 80 L250 400 L400 80 L320 80 L250 260 L180 80 Z" fill="#FF4655" />
  </svg>
  <svg class="floating-logo floating-logo-2" viewBox="0 0 500 500" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M100 80 L250 400 L400 80 L320 80 L250 260 L180 80 Z" fill="#00F0FF" />
  </svg>

  <div class="app-container">

    <!-- HEADER -->
    <header>
      <div class="brand-badge">
        <svg viewBox="0 0 100 100">
          <polygon points="20,10 80,10 50,90" fill="#FF4655"/>
        </svg>
        Paper Rex Champions Vault
      </div>
      <h1>HOW WE WON OUR FIRST TROPHY</h1>
      <p class="subtitle">VCT Masters Toronto Official Champions Documentary Showcase</p>

      <!-- DIRECT YOUTUBE LINK BUTTON -->
      <div>
        <a href="https://www.youtube.com/watch?v=jrdHMJEDVXQ" target="_blank" rel="noopener noreferrer" class="yt-watch-btn">
          <i class="fa-brands fa-youtube" style="font-size: 1.2rem;"></i> Watch Directly on YouTube
        </a>
      </div>

      <!-- STATS BAR -->
      <div class="stats-bar">
        <div class="stat-card">
          <div class="stat-value">1.0M+</div>
          <div class="stat-label">YouTube Views</div>
        </div>
        <div class="stat-card">
          <div class="stat-value">TORONTO</div>
          <div class="stat-label">Masters Champions</div>
        </div>
        <div class="stat-card">
          <div class="stat-value">56:48</div>
          <div class="stat-label">Full Length Doc</div>
        </div>
        <div class="stat-card">
          <div class="stat-value">35K+</div>
          <div class="stat-label">Likes</div>
        </div>
      </div>
    </header>

    <!-- MAIN PLAYER & TIMELINE SECTION -->
    <div class="main-grid">
      
      <!-- PLAYER CONTAINER -->
      <div class="video-container">
        <div class="iframe-wrapper">
          <div id="player"></div>
        </div>
        <div class="video-info-bar">
          <div class="now-playing">
            <div class="pulse-dot"></div>
            <span id="current-chapter-title">Select a timeline chapter to jump directly to key moments</span>
          </div>
          <div>
            <a href="https://www.youtube.com/watch?v=jrdHMJEDVXQ" target="_blank" rel="noopener noreferrer" class="yt-link-text">
              Open in YouTube <i class="fa-solid fa-arrow-up-right-from-square"></i>
            </a>
          </div>
        </div>
      </div>

      <!-- CHAPTER TIMELINE PANEL -->
      <div class="chapters-panel">
        <div class="section-title">
          <i class="fa-solid fa-list-ol"></i> Key Documentary Moments
        </div>
        <div class="chapters-list" id="chapters-list">
          <!-- Chapters injected via JavaScript -->
        </div>
      </div>

    </div>

    <!-- HYPE RECTOR BUTTON -->
    <div class="hype-section">
      <h2 style="font-family: 'Teko', sans-serif; font-size: 2rem; letter-spacing: 1px;">CELEBRATE THE FIRST INTERNATIONAL TROPHY!</h2>
      <p style="color: var(--text-muted); font-size: 0.95rem;">Hit the Hype Rector to trigger the championship confetti cascade!</p>
      <button class="hype-btn" onclick="triggerHype()">
        <i class="fa-solid fa-trophy"></i> HYPE RECTOR! <i class="fa-solid fa-fire"></i>
      </button>
    </div>

    <!-- ROSTER SHOWCASE -->
    <div class="section-title">
      <i class="fa-solid fa-users"></i> Paper Rex Championship Roster
    </div>
    <div class="roster-grid">
      <div class="player-card">
        <div class="player-header">
          <div>
            <div class="player-ign">f0rsakeN</div>
            <div class="player-name">Jason Susanto</div>
          </div>
          <span class="player-role">Flex Master</span>
        </div>
        <p style="font-size: 0.85rem; color: var(--text-muted);">The versatile genius capable of playing almost any agent at a world-class level.</p>
        <div class="player-quote">"If you guys want to win, you just go no matter what. Just go round by round."</div>
      </div>

      <div class="player-card">
        <div class="player-header">
          <div>
            <div class="player-ign">Jinggg</div>
            <div class="player-name">Wang Jing Jie</div>
          </div>
          <span class="player-role">Entry / Raze God</span>
        </div>
        <p style="font-size: 0.85rem; color: var(--text-muted);">Unmatched entry aggression, satchel movement specialist, and high-impact playmaker.</p>
        <div class="player-quote">"Guys I need to pee so bad, please end the round!"</div>
      </div>

      <div class="player-card">
        <div class="player-header">
          <div>
            <div class="player-ign">something</div>
            <div class="player-name">Ilya Petrov</div>
          </div>
          <span class="player-role">Duelist Prodigy</span>
        </div>
        <p style="font-size: 0.85rem; color: var(--text-muted);">Superhuman reaction times and clutch Jett operator plays on the global stage.</p>
        <div class="player-quote">"I was like 'Bro why two people not shooting bro, I am jumping jumping!'"</div>
      </div>

      <div class="player-card">
        <div class="player-header">
          <div>
            <div class="player-ign">d4v41</div>
            <div class="player-name">Khalish Rusyaidee</div>
          </div>
          <span class="player-role">Clutch Initiator</span>
        </div>
        <p style="font-size: 0.85rem; color: var(--text-muted);">The calm backbone of PRX, consistently delivering in 1v2 and 1v3 post-plant scenarios.</p>
        <div class="player-quote">"We just realized that the most important thing for us was to be a lot calmer."</div>
      </div>

      <div class="player-card">
        <div class="player-header">
          <div>
            <div class="player-ign">mindfreak</div>
            <div class="player-name">Aaron Leonhart</div>
          </div>
          <span class="player-role">Controller Anchor</span>
        </div>
        <p style="font-size: 0.85rem; color: var(--text-muted);">Ice-cold site anchor who locks down rounds under intense pressure.</p>
        <div class="player-quote">"Masukin literally means wind inside, feeling under the weather."</div>
      </div>

      <div class="player-card">
        <div class="player-header">
          <div>
            <div class="player-ign">alecks</div>
            <div class="player-name">Alexandre Sallé</div>
          </div>
          <span class="player-role">Head Coach</span>
        </div>
        <p style="font-size: 0.85rem; color: var(--text-muted);">The strategic mastermind behind W-gaming and legendary table-slam enthusiast.</p>
        <div class="player-quote">"Remember round by round, doesn't matter if you're ahead or behind."</div>
      </div>
    </div>

    <!-- MATCHES RECAP -->
    <div class="section-title">
      <i class="fa-solid fa-gamepad"></i> Toronto Championship Run
    </div>
    <div class="matches-grid">
      <div class="match-card">
        <div class="match-stage">Playoffs Opening</div>
        <div class="match-versus">PRX vs G2 Esports</div>
        <div class="match-score">2 - 0</div>
        <span class="match-result">VICTORY</span>
      </div>

      <div class="match-card">
        <div class="match-stage">Upper Semifinals</div>
        <div class="match-versus">PRX vs Sentinels</div>
        <div class="match-score">2 - 0</div>
        <span class="match-result">VICTORY</span>
      </div>

      <div class="match-card">
        <div class="match-stage">Upper Final</div>
        <div class="match-versus">PRX vs Wolves Esports</div>
        <div class="match-score">2 - 1</div>
        <span class="match-result">VICTORY</span>
      </div>

      <div class="match-card">
        <div class="match-stage">Grand Finals</div>
        <div class="match-versus">PRX vs Fnatic</div>
        <div class="match-score">3 - 2</div>
        <span class="match-result" style="background: rgba(255, 230, 0, 0.2); color: var(--prx-yellow);">TROPHY LIFTED</span>
      </div>
    </div>

    <!-- RANDOM MEME / QUOTE GENERATOR -->
    <div class="quote-box">
      <div class="section-title" style="justify-content: center;">
        <i class="fa-solid fa-quote-left"></i> Iconic PRX Doc Quote Generator
      </div>
      <div class="random-quote" id="quote-display">
        "Honestly like personally when I play I just don't miss."
      </div>
      <div class="quote-author" id="quote-author">- f0rsakeN</div>
      <button class="gen-btn" onclick="generateQuote()">
        <i class="fa-solid fa-shuffle"></i> Pull Random Quote
      </button>
    </div>

    <!-- FOOTER -->
    <footer>
      <p>Paper Rex VCT Masters Toronto Champions Fan Showcase</p>
      <p style="margin-top: 8px; font-size: 0.85rem;">
        Direct YouTube Link: <a href="https://www.youtube.com/watch?v=jrdHMJEDVXQ" target="_blank" rel="noopener noreferrer">https://www.youtube.com/watch?v=jrdHMJEDVXQ</a>
      </p>
    </footer>

  </div>

  <!-- YOUTUBE IFRAME API & INTERACTIVE JS -->
  <script>
    // Chapter Data
    const chapters = [
      { time: 0, seconds: 0, title: "00:00 - Intro & Team Vlog Vibes" },
      { time: 120, seconds: 120, title: "02:00 - Vs G2 Esports (Revenge Match)" },
      { time: 515, seconds: 515, title: "08:35 - Vs Sentinels Upper Match" },
      { time: 1050, seconds: 1050, title: "17:30 - Hotel Room Pranks & Team Banter" },
      { time: 1655, seconds: 1655, title: "27:35 - Vs Wolves Esports Upper Final" },
      { time: 2160, seconds: 2160, title: "36:00 - Grand Finals Prep & Walkouts" },
      { time: 2430, seconds: 2430, title: "40:30 - Grand Finals vs Fnatic (Battle)" },
      { time: 3020, seconds: 3020, title: "50:20 - CROWNED CHAMPIONS! Trophy Lift" },
      { time: 3185, seconds: 3185, title: "53:05 - Post-Match Reflection & Speeches" }
    ];

    // PRX Quotes Data
    const prxQuotes = [
      { quote: "Honestly like personally when I play I just don't miss.", author: "f0rsakeN" },
      { quote: "Masukin literally translated means enter the wind... feeling under the weather.", author: "mindfreak" },
      { quote: "Guys I need to pee so bad, please end the round!", author: "Jinggg" },
      { quote: "If we win tournament we're going to wear crop top outside of hotel for fun!", author: "something & Jinggg" },
      { quote: "Remember round by round, doesn't matter if you're ahead or behind.", author: "Coach alecks" },
      { quote: "Don't good luck us, good luck the enemy!", author: "f0rsakeN" },
      { quote: "We just learned to play a little bit better and a little bit smarter.", author: "d4v41" }
    ];

    let player;

    // Load YouTube IFrame API
    const tag = document.createElement('script');
    tag.src = "https://www.youtube.com/iframe_api";
    const firstScriptTag = document.getElementsByTagName('script')[0];
    firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

    function onYouTubeIframeAPIReady() {
      player = new YT.Player('player', {
        videoId: 'jrdHMJEDVXQ',
        playerVars: {
          'autoplay': 0,
          'rel': 0,
          'modestbranding': 1
        },
        events: {
          'onReady': onPlayerReady
        }
      });
    }

    function onPlayerReady(event) {
      renderChapters();
    }

    function renderChapters() {
      const container = document.getElementById('chapters-list');
      container.innerHTML = '';

      chapters.forEach((ch, index) => {
        const btn = document.createElement('div');
        btn.className = `chapter-btn ${index === 0 ? 'active' : ''}`;
        btn.onclick = () => jumpToChapter(ch.seconds, btn, ch.title);

        btn.innerHTML = `
          <span class="chapter-time">${formatTime(ch.seconds)}</span>
          <span class="chapter-text">${ch.title.split('-')[1]}</span>
          <i class="fa-solid fa-play" style="font-size: 0.8rem; opacity: 0.6;"></i>
        `;
        container.appendChild(btn);
      });
    }

    function jumpToChapter(seconds, element, title) {
      if (player && player.seekTo) {
        player.seekTo(seconds, true);
        player.playVideo();
      }

      document.querySelectorAll('.chapter-btn').forEach(b => b.classList.remove('active'));
      element.classList.add('active');

      document.getElementById('current-chapter-title').innerText = title;
    }

    function formatTime(sec) {
      const m = Math.floor(sec / 60);
      const s = sec % 60;
      return `${m.toString().padStart(2, '0')}:${s.toString().padStart(2, '0')}`;
    }

    function triggerHype() {
      // Trigger Confetti
      if (window.confetti) {
        confetti({
          particleCount: 120,
          spread: 80,
          origin: { y: 0.6 },
          colors: ['#FF4655', '#00F0FF', '#FFE600', '#FFFFFF']
        });
      }
    }

    function generateQuote() {
      const randomIndex = Math.floor(Math.random() * prxQuotes.length);
      const q = prxQuotes[randomIndex];
      document.getElementById('quote-display').innerText = `"${q.quote}"`;
      document.getElementById('quote-author').innerText = `- ${q.author}`;
    }
  </script>
</body>
</html>
