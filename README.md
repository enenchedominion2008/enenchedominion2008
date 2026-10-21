<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#080b16">
<title>Enenche Dominion</title>
<style>
  :root{--bg:#080b16;--text:#f4f7ff;--muted:#a9b4d0;--cyan:#65f4ff;--violet:#a78bfa;--pink:#ff82d2;--line:rgba(170,190,255,.18)}
  *{box-sizing:border-box}
  html{scroll-behavior:smooth}
  body{margin:0;min-height:100vh;display:grid;place-items:center;overflow:hidden;background:var(--bg);color:var(--text);font-family:Inter,ui-sans-serif,system-ui,-apple-system,"Segoe UI",sans-serif}
  .ambient{position:fixed;inset:0;z-index:-3;overflow:hidden;background:radial-gradient(ellipse at 15% 10%,rgba(74,87,190,.2),transparent 38%),radial-gradient(ellipse at 85% 35%,rgba(0,220,230,.12),transparent 34%),radial-gradient(ellipse at 50% 100%,rgba(147,51,234,.15),transparent 40%),#080b16}
  .orb{position:absolute;width:34rem;aspect-ratio:1;border-radius:50%;filter:blur(75px);opacity:.23;animation:drift 17s ease-in-out infinite alternate}
  .orb.one{background:#4f46e5;top:-15rem;left:-10rem}.orb.two{background:#06b6d4;right:-16rem;top:22%;animation-delay:-6s}.orb.three{background:#9333ea;left:25%;bottom:-24rem;animation-delay:-10s}
  .grid{position:fixed;inset:0;z-index:-2;pointer-events:none;opacity:.2;background-image:linear-gradient(rgba(140,170,255,.08) 1px,transparent 1px),linear-gradient(90deg,rgba(140,170,255,.08) 1px,transparent 1px);background-size:52px 52px;mask-image:linear-gradient(to bottom,black,transparent 90%)}
  main{width:min(760px,calc(100% - 36px));padding:58px 28px;text-align:center;position:relative;isolation:isolate}
  .halo{position:absolute;z-index:-1;left:50%;top:50%;width:min(560px,90vw);aspect-ratio:1;transform:translate(-50%,-50%);border:1px solid rgba(101,244,255,.15);border-radius:50%;animation:rotate 35s linear infinite}
  .halo:before,.halo:after{content:"";position:absolute;width:9px;height:9px;border-radius:50%;background:var(--cyan);box-shadow:0 0 22px var(--cyan)}
  .halo:before{top:14%;left:16%}.halo:after{right:12%;bottom:23%;background:var(--pink);box-shadow:0 0 22px var(--pink)}
  .eyebrow{display:inline-flex;align-items:center;gap:9px;padding:9px 13px;border:1px solid rgba(101,244,255,.22);border-radius:999px;background:rgba(101,244,255,.06);color:var(--cyan);font-size:10px;letter-spacing:.17em;text-transform:uppercase;font-weight:800;animation:rise .8s both}
  .dot{width:7px;height:7px;border-radius:50%;background:#70ffb1;box-shadow:0 0 12px #70ffb1;animation:pulse 1.8s infinite}
  h1{margin:25px 0 12px;font-size:clamp(2.8rem,8vw,5.7rem);line-height:1;letter-spacing:-.075em;font-weight:900;animation:rise .9s .1s both}
  .gradient{display:block;color:transparent;background:linear-gradient(100deg,var(--cyan),#b7a2ff 48%,var(--pink));background-size:200% auto;-webkit-background-clip:text;background-clip:text;animation:shine 7s linear infinite}
  .role{margin:22px 0 34px;color:#dbe4ff;font-size:clamp(1rem,3vw,1.35rem);letter-spacing:.24em;text-transform:uppercase;font-weight:650;animation:rise .9s .2s both}
  .role span{color:var(--cyan)}
  .divider{height:1px;width:76px;margin:0 auto 25px;background:linear-gradient(90deg,transparent,var(--cyan),var(--violet),transparent);animation:grow 1.2s .35s both}
  h2{margin:0 0 18px;color:var(--muted);font-size:11px;text-transform:uppercase;letter-spacing:.22em;animation:rise .9s .3s both}
  .languages{display:flex;flex-wrap:wrap;justify-content:center;gap:11px;max-width:560px;margin:0 auto;animation:rise .9s .4s both}
  .language{padding:12px 17px;border:1px solid var(--line);border-radius:12px;background:rgba(16,23,43,.72);color:#e7edff;font-size:13px;font-weight:700;box-shadow:inset 0 1px rgba(255,255,255,.025);transition:transform .25s,border-color .25s,box-shadow .25s}
  .language:hover{transform:translateY(-4px);border-color:rgba(101,244,255,.55);box-shadow:0 8px 30px rgba(101,244,255,.08)}
  footer{margin-top:44px;color:#687592;font-size:10px;letter-spacing:.12em;animation:rise .9s .55s both}
  @keyframes drift{from{transform:translate(-3%,-2%) scale(.92)}to{transform:translate(7%,8%) scale(1.12)}}
  @keyframes rotate{to{rotate:360deg}}
  @keyframes shine{to{background-position:200% center}}
  @keyframes pulse{0%,100%{opacity:1}50%{opacity:.35}}
  @keyframes rise{from{opacity:0;transform:translateY(18px)}to{opacity:1;transform:translateY(0)}}
  @keyframes grow{from{opacity:0;transform:scaleX(.2)}to{opacity:1;transform:scaleX(1)}}
  @media(max-width:480px){main{padding:45px 8px}.role{letter-spacing:.15em}.language{padding:11px 14px}.halo{width:110vw}}
  @media(prefers-reduced-motion:reduce){*,*:before,*:after{animation-duration:.01ms!important;animation-iteration-count:1!important;scroll-behavior:auto!important;transition-duration:.01ms!important}}
</style>
</head>
<body>
<div class="ambient" aria-hidden="true"><div class="orb one"></div><div class="orb two"></div><div class="orb three"></div></div>
<div class="grid" aria-hidden="true"></div>
<main>
  <div class="halo" aria-hidden="true"></div>
  <div class="eyebrow"><span class="dot"></span> Building the future with code</div>
  <h1>Enenche <span class="gradient">Dominion</span></h1>
  <p class="role"><span>AI</span> Engineer</p>
  <div class="divider"></div>
  <h2>Languages & Technologies</h2>
  <div class="languages">
    <span class="language">Python</span>
    <span class="language">Golang</span>
    <span class="language">Bash</span>
    <span class="language">HTML</span>
    <span class="language">JavaScript</span>
  </div>
  <footer>CURIOUS BY NATURE · ENGINEERED WITH PURPOSE</footer>
</main>
</body>
</html>
