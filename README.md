<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="theme-color" content="#080b16" />
  <meta name="description" content="Enenche Dominion — aspiring software developer exploring Python, Flask, web development, and creative digital experiences." />
  <title>Enenche Dominion | Developer Portfolio</title>
  <style>
    :root {
      --bg: #080b16;
      --panel: rgba(17, 24, 45, .72);
      --text: #f4f7ff;
      --muted: #a9b4d0;
      --cyan: #65f4ff;
      --violet: #a78bfa;
      --pink: #ff82d2;
      --line: rgba(170, 190, 255, .17);
    }
    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0; min-height: 100vh; overflow-x: hidden;
      color: var(--text); background: var(--bg);
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }
    a { color: inherit; text-decoration: none; }
    .ambient {
      position: fixed; inset: 0; z-index: -3; overflow: hidden;
      background:
        radial-gradient(ellipse at 15% 10%, rgba(74, 87, 190, .2), transparent 38%),
        radial-gradient(ellipse at 85% 35%, rgba(0, 220, 230, .12), transparent 34%),
        radial-gradient(ellipse at 50% 100%, rgba(147, 51, 234, .15), transparent 40%),
        #080b16;
    }
    .orb {
      position: absolute; width: 34rem; aspect-ratio: 1; border-radius: 50%;
      filter: blur(75px); opacity: .22; mix-blend-mode: screen;
      animation: drift 17s ease-in-out infinite alternate;
    }
    .orb.one { background: #4f46e5; top: -15rem; left: -10rem; }
    .orb.two { background: #06b6d4; right: -16rem; top: 22%; animation-delay: -6s; }
    .orb.three { background: #9333ea; left: 25%; bottom: -24rem; animation-delay: -10s; }
    .grid {
      position: fixed; inset: 0; z-index: -2; pointer-events: none; opacity: .22;
      background-image: linear-gradient(rgba(140, 170, 255, .08) 1px, transparent 1px),
                        linear-gradient(90deg, rgba(140, 170, 255, .08) 1px, transparent 1px);
      background-size: 52px 52px;
      mask-image: linear-gradient(to bottom, black, transparent 88%);
    }
    .topbar {
      width: min(1100px, calc(100% - 40px)); margin: 0 auto; padding: 26px 0;
      display: flex; align-items: center; justify-content: space-between; gap: 20px;
    }
    .brand { display: flex; align-items: center; gap: 11px; font-weight: 800; letter-spacing: -.04em; }
    .brand-mark {
      width: 38px; height: 38px; display: grid; place-items: center; border-radius: 13px;
      color: #08111e; font-size: 14px; font-weight: 900;
      background: linear-gradient(135deg, var(--cyan), var(--violet));
      box-shadow: 0 0 28px rgba(101, 244, 255, .22);
    }
    .nav { display: flex; gap: 24px; color: var(--muted); font-size: 13px; }
    .nav a { transition: color .25s ease; }
    .nav a:hover { color: var(--cyan); }
    .hero {
      width: min(1100px, calc(100% - 40px)); margin: 0 auto; min-height: 76vh;
      display: grid; grid-template-columns: 1.3fr .7fr; align-items: center; gap: 60px;
      padding: 65px 0 100px;
    }
    .eyebrow {
      display: inline-flex; align-items: center; gap: 9px; color: var(--cyan);
      border: 1px solid rgba(101,244,255,.22); background: rgba(101,244,255,.06);
      border-radius: 999px; padding: 9px 13px; font-size: 11px; letter-spacing: .15em;
      text-transform: uppercase; font-weight: 750;
    }
    .status-dot { width: 7px; height: 7px; border-radius: 50%; background: #70ffb1; box-shadow: 0 0 12px #70ffb1; animation: pulse 1.8s infinite; }
    h1 {
      margin: 24px 0 20px; font-size: clamp(3.2rem, 8vw, 6.8rem); line-height: .94;
      letter-spacing: -.075em; font-weight: 850;
    }
    .gradient-text {
      display: block; color: transparent;
      background: linear-gradient(100deg, var(--cyan) 5%, #b7a2ff 47%, var(--pink) 90%);
      background-size: 200% auto; -webkit-background-clip: text; background-clip: text;
      animation: shine 7s linear infinite;
    }
    .intro { color: var(--muted); font-size: clamp(1rem, 1.7vw, 1.15rem); line-height: 1.85; max-width: 650px; }
    .intro strong { color: var(--text); font-weight: 650; }
    .actions { display: flex; flex-wrap: wrap; gap: 12px; margin-top: 30px; }
    .btn {
      display: inline-flex; align-items: center; justify-content: center; gap: 10px;
      padding: 13px 18px; border-radius: 13px; font-size: 13px; font-weight: 750;
      border: 1px solid var(--line); transition: transform .25s, border-color .25s, box-shadow .25s;
    }
    .btn:hover { transform: translateY(-3px); border-color: rgba(101,244,255,.55); box-shadow: 0 10px 35px rgba(0,0,0,.25); }
    .btn.primary { color: #08111e; background: linear-gradient(110deg, var(--cyan), #b9a5ff); border: 0; }
    .visual { display: grid; place-items: center; position: relative; min-height: 360px; }
    .ring {
      position: absolute; width: min(320px, 78vw); aspect-ratio: 1; border: 1px solid rgba(101,244,255,.23);
      border-radius: 50%; animation: rotate 24s linear infinite;
    }
    .ring::before, .ring::after {
      content: ""; position: absolute; width: 10px; height: 10px; border-radius: 50%;
      background: var(--cyan); box-shadow: 0 0 20px var(--cyan);
    }
    .ring::before { top: 16%; left: 13%; }
    .ring::after { right: 8%; bottom: 25%; width: 6px; height: 6px; background: var(--pink); box-shadow: 0 0 18px var(--pink); }
    .ring.ring-two { width: min(250px, 62vw); border-color: rgba(167,139,250,.28); animation: rotate 18s linear infinite reverse; transform: rotateX(65deg); }
    .ring.ring-two::before { background: var(--violet); box-shadow: 0 0 20px var(--violet); top: 5%; left: 50%; }
    .core {
      position: relative; width: 175px; height: 175px; display: grid; place-items: center;
      border: 1px solid rgba(255,255,255,.24); border-radius: 42px; transform: rotate(-7deg);
      background: linear-gradient(145deg, rgba(101,244,255,.17), rgba(167,139,250,.12) 55%, rgba(255,130,210,.1));
      box-shadow: inset 0 0 35px rgba(255,255,255,.04), 0 0 90px rgba(101,244,255,.12);
      backdrop-filter: blur(14px); animation: float 5s ease-in-out infinite;
    }
    .core span { font-size: 48px; font-weight: 900; letter-spacing: -.1em; background: linear-gradient(135deg, white, var(--cyan)); color: transparent; -webkit-background-clip: text; background-clip: text; transform: rotate(7deg); }
    .float-tag {
      position: absolute; padding: 10px 13px; border: 1px solid var(--line); border-radius: 12px;
      background: rgba(12, 18, 35, .85); color: #dbe7ff; font-size: 11px; font-weight: 750;
      box-shadow: 0 10px 35px rgba(0,0,0,.22); backdrop-filter: blur(12px);
      animation: float 4s ease-in-out infinite;
    }
    .tag-python { top: 16%; left: 0; animation-delay: -1s; }
    .tag-web { right: -2%; top: 28%; animation-delay: -2.2s; }
    .tag-flask { bottom: 15%; left: 5%; animation-delay: -3s; }
    .section { width: min(1100px, calc(100% - 40px)); margin: 0 auto; padding: 45px 0 85px; }
    .section-head { margin-bottom: 28px; }
    .kicker { color: var(--cyan); text-transform: uppercase; letter-spacing: .18em; font-size: 10px; font-weight: 800; }
    h2 { margin: 10px 0 0; font-size: clamp(1.8rem, 4vw, 2.7rem); letter-spacing: -.055em; }
    .section-copy { color: var(--muted); max-width: 650px; line-height: 1.8; font-size: 14px; }
    .cards { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; }
    .card {
      min-height: 205px; padding: 24px; border: 1px solid var(--line); border-radius: 22px;
      background: linear-gradient(145deg, rgba(22,31,57,.76), rgba(11,15,30,.74));
      position: relative; overflow: hidden; transition: transform .3s, border-color .3s;
    }
    .card::after { content: ""; position: absolute; width: 140px; height: 140px; border-radius: 50%; right: -80px; bottom: -90px; background: var(--glow, var(--cyan)); opacity: .13; filter: blur(25px); }
    .card:hover { transform: translateY(-6px); border-color: rgba(101,244,255,.38); }
    .card-icon { width: 43px; height: 43px; display: grid; place-items: center; border-radius: 14px; font-size: 19px; margin-bottom: 22px; background: rgba(101,244,255,.09); border: 1px solid rgba(101,244,255,.14); }
    .card h3 { margin: 0 0 9px; font-size: 16px; letter-spacing: -.025em; }
    .card p { margin: 0; color: var(--muted); font-size: 13px; line-height: 1.75; }
    .skills { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 25px; }
    .skill { padding: 10px 13px; border: 1px solid var(--line); border-radius: 10px; background: rgba(255,255,255,.025); color: #d9e3fb; font-size: 12px; transition: .25s; }
    .skill:hover { color: var(--cyan); border-color: rgba(101,244,255,.4); transform: translateY(-2px); }
    .project {
      display: grid; grid-template-columns: 1fr auto; gap: 25px; align-items: center;
      padding: 27px; border: 1px solid var(--line); border-radius: 22px;
      background: linear-gradient(120deg, rgba(19,28,52,.85), rgba(13,17,33,.75));
    }
    .project h3 { margin: 0 0 8px; font-size: 19px; }
    .project p { margin: 0; color: var(--muted); line-height: 1.8; font-size: 13px; max-width: 700px; }
    .quote {
      margin-top: 22px; padding: 23px 26px; border-left: 2px solid var(--violet);
      background: linear-gradient(90deg, rgba(167,139,250,.09), transparent); color: #d9e0f5;
      line-height: 1.8; font-size: 14px;
    }
    footer {
      width: min(1100px, calc(100% - 40px)); margin: 0 auto; padding: 26px 0 35px;
      border-top: 1px solid var(--line); display: flex; flex-wrap: wrap; justify-content: space-between; gap: 12px;
      color: #7f8ba8; font-size: 11px;
    }
    .reveal { opacity: 0; transform: translateY(22px); transition: opacity .8s ease, transform .8s ease; }
    .reveal.visible { opacity: 1; transform: translateY(0); }
    @keyframes drift { from { transform: translate3d(-3%, -2%, 0) scale(.92); } to { transform: translate3d(7%, 8%, 0) scale(1.12); } }
    @keyframes float { 0%,100% { translate: 0 0; } 50% { translate: 0 -12px; } }
    @keyframes rotate { to { rotate: 360deg; } }
    @keyframes shine { to { background-position: 200% center; } }
    @keyframes pulse { 0%,100% { opacity: 1; } 50% { opacity: .35; } }
    @media (max-width: 760px) {
      .nav { gap: 13px; font-size: 11px; }
      .hero { grid-template-columns: 1fr; gap: 20px; padding-top: 45px; text-align: center; }
      .eyebrow, .actions { justify-content: center; }
      .intro { margin-inline: auto; }
      .visual { min-height: 330px; grid-row: 1; }
      h1 { font-size: clamp(3rem, 13vw, 5rem); }
      .cards { grid-template-columns: 1fr; }
      .card { min-height: 0; }
      .project { grid-template-columns: 1fr; }
    }
    @media (max-width: 420px) {
      .topbar { width: calc(100% - 28px); }
      .brand { font-size: 13px; }
      .nav { gap: 10px; }
      .hero, .section, footer { width: calc(100% - 28px); }
      .float-tag { font-size: 10px; }
    }
    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after { animation-duration: .01ms !important; animation-iteration-count: 1 !important; scroll-behavior: auto !important; transition-duration: .01ms !important; }
      .reveal { opacity: 1; transform: none; }
    }
  </style>
</head>
<body>
  <div class="ambient" aria-hidden="true"><div class="orb one"></div><div class="orb two"></div><div class="orb three"></div></div>
  <div class="grid" aria-hidden="true"></div>

  <header class="topbar">
    <a class="brand" href="#home" aria-label="Enenche Dominion home">
      <span class="brand-mark">ED</span><span>ENENCHE<span style="color:var(--cyan)">.</span></span>
    </a>
    <nav class="nav" aria-label="Main navigation">
      <a href="#about">About</a><a href="#skills">Skills</a><a href="#projects">Projects</a>
    </nav>
  </header>

  <main>
    <section class="hero" id="home">
      <div class="hero-copy">
        <div class="eyebrow"><span class="status-dot"></span> Learning. Building. Evolving.</div>
        <h1>Enenche<br><span class="gradient-text">Dominion.</span></h1>
        <p class="intro">
          Aspiring <strong>software developer</strong> with a growing passion for building useful,
          beautiful digital experiences. I’m exploring Python, backend development, and the creative
          side of the web — one project, one problem, and one breakthrough at a time.
        </p>
        <div class="actions">
          <a class="btn primary" href="#skills">Explore my toolkit <span aria-hidden="true">↗</span></a>
          <a class="btn" href="#about">More about me <span aria-hidden="true">↓</span></a>
        </div>
      </div>
      <div class="visual" aria-label="Animated developer-themed graphic">
        <div class="ring"></div><div class="ring ring-two"></div>
        <div class="core"><span>&lt;/&gt;</span></div>
        <div class="float-tag tag-python">🐍 Python</div>
        <div class="float-tag tag-web">✦ Web Experiences</div>
        <div class="float-tag tag-flask">⚙ Flask · Backend</div>
      </div>
    </section>

    <section class="section reveal" id="about">
      <div class="section-head">
        <div class="kicker">01 / The person behind the code</div>
        <h2>Curious mind. Builder’s mindset.</h2>
        <p class="section-copy">I’m developing my skills by learning the fundamentals, practising with real code, and turning ideas into projects. I enjoy both the logic that powers an application and the details that make an interface feel alive.</p>
      </div>
      <div class="cards">
        <article class="card" style="--glow:#65f4ff">
          <div class="card-icon">⌘</div><h3>Software Development</h3>
          <p>Practising Python and strengthening my problem-solving skills through functions, data structures, routes, and application logic.</p>
        </article>
        <article class="card" style="--glow:#a78bfa">
          <div class="card-icon">◈</div><h3>Web Development</h3>
          <p>Exploring HTML, CSS, and JavaScript to create responsive pages with polished layouts, smooth transitions, and interactive details.</p>
        </article>
        <article class="card" style="--glow:#ff82d2">
          <div class="card-icon">⚡</div><h3>Backend & Team Projects</h3>
          <p>Learning how web applications work behind the scenes with Flask, routes, and collaborative project workflows.</p>
        </article>
      </div>
    </section>

    <section class="section reveal" id="skills">
      <div class="section-head">
        <div class="kicker">02 / My current toolkit</div>
        <h2>Skills in progress.</h2>
        <p class="section-copy">A snapshot of the technologies I’ve been learning and using. I’m always improving, experimenting, and adding new tools to the toolkit.</p>
      </div>
      <div class="skills">
        <span class="skill">Python</span><span class="skill">Flask</span><span class="skill">HTML5</span>
        <span class="skill">CSS3</span><span class="skill">JavaScript</span><span class="skill">Git</span>
        <span class="skill">GitHub</span><span class="skill">Responsive Design</span>
        <span class="skill">UI Animation</span><span class="skill">Debugging</span>
      </div>
    </section>

    <section class="section reveal" id="projects">
      <div class="section-head">
        <div class="kicker">03 / What I’m focused on</div>
        <h2>Learning with purpose.</h2>
        <p class="section-copy">I’m building a solid foundation in programming and web development, practising consistently, and growing through hands-on projects and collaboration.</p>
      </div>
      <div class="cards">
        <article class="card" style="--glow:#65f4ff">
          <div class="card-icon">⌁</div><h3>Python & Problem Solving</h3>
          <p>Improving my Python skills through functions, data structures, application logic, debugging, and practical exercises.</p>
        </article>
        <article class="card" style="--glow:#a78bfa">
          <div class="card-icon">▤</div><h3>Backend Development</h3>
          <p>Learning Flask, routes, request handling, and how different parts of a web application work together.</p>
        </article>
        <article class="card" style="--glow:#ff82d2">
          <div class="card-icon">✧</div><h3>Creative Web Design</h3>
          <p>Experimenting with responsive layouts, visual effects, motion, and polished user experiences using HTML, CSS, and JavaScript.</p>
        </article>
      </div>
      <div class="quote">“Learning every day. Building step by step. Turning curiosity into skills, and ideas into working code.”</div>
    </section>
  </main>

  <footer>
    <span>© <span id="year"></span> Enenche Dominion</span>
    <span>Python · Flask · HTML · CSS · JavaScript</span>
    <span>Made with curiosity, code & a little creativity ✦</span>
  </footer>

  <script>
    document.getElementById("year").textContent = new Date().getFullYear();

    // Reveal sections gently as they enter the viewport.
    const revealItems = document.querySelectorAll(".reveal");
    if ("IntersectionObserver" in window) {
      const observer = new IntersectionObserver((entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add("visible");
            observer.unobserve(entry.target);
          }
        });
      }, { threshold: 0.12 });
      revealItems.forEach((item) => observer.observe(item));
    } else {
      revealItems.forEach((item) => item.classList.add("visible"));
    }
  </script>
</body>
</html>
