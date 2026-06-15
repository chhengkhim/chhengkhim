
<style>
@import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;600&family=Inter:wght@300;400;500;600&display=swap');
*{box-sizing:border-box;margin:0;padding:0}
.wrap{background:#080808;color:#e0e0e0;font-family:'Inter',sans-serif;padding:0;min-height:100vh;overflow:hidden}
.banner{position:relative;height:180px;background:#080808;overflow:hidden;display:flex;align-items:center;justify-content:center;flex-direction:column}
.grid-lines{position:absolute;inset:0;pointer-events:none}
.banner-text{position:relative;z-index:2;text-align:center}
.banner-title{font-family:'JetBrains Mono',monospace;font-size:22px;font-weight:600;color:#fff;letter-spacing:-0.02em;animation:fadeSlideUp 0.8s ease forwards;opacity:0}
.banner-sub{font-family:'JetBrains Mono',monospace;font-size:13px;color:#555;margin-top:6px;animation:fadeSlideUp 0.8s ease 0.2s forwards;opacity:0}
.horizon{position:absolute;bottom:0;left:0;right:0;height:60px}
@keyframes fadeSlideUp{from{opacity:0;transform:translateY(12px)}to{opacity:1;transform:translateY(0)}}
.scanline{position:absolute;inset:0;background:repeating-linear-gradient(0deg,transparent,transparent 3px,rgba(0,0,0,0.08) 3px,rgba(0,0,0,0.08) 4px);pointer-events:none;z-index:1}
.body{padding:20px 24px 32px;position:relative;z-index:1}
.links-row{display:flex;gap:8px;flex-wrap:wrap;justify-content:center;margin-bottom:20px;animation:fadeSlideUp 0.7s ease 0.35s forwards;opacity:0}
.lnk{font-family:'JetBrains Mono',monospace;font-size:10px;padding:5px 12px;border-radius:4px;border:0.5px solid #2a2a2a;color:#888;text-decoration:none;background:#111;transition:all 0.2s;letter-spacing:0.04em}
.lnk:hover{border-color:#555;color:#fff;background:#1a1a1a}
.divider{height:0.5px;background:#1a1a1a;margin:18px 0}
.section-label{font-family:'JetBrains Mono',monospace;font-size:9px;color:#444;letter-spacing:0.12em;text-transform:uppercase;margin-bottom:12px}
.about-grid{display:grid;grid-template-columns:1fr 90px;gap:20px;align-items:start;animation:fadeSlideUp 0.7s ease 0.5s forwards;opacity:0}
.about-text{font-size:13px;color:#777;line-height:1.7}
.about-text strong{color:#ccc;font-weight:500}
.about-list{margin-top:10px;list-style:none}
.about-list li{font-size:12px;color:#555;padding:3px 0;font-family:'JetBrains Mono',monospace}
.about-list li::before{content:'→ ';color:#333}
.astro-frame{width:90px;height:90px;border-radius:8px;border:0.5px solid #1e1e1e;background:#0d0d0d;display:flex;align-items:center;justify-content:center;overflow:hidden;position:relative}
.astro-svg{width:70px;height:70px}
.tags-wrap{display:flex;flex-wrap:wrap;gap:6px;animation:fadeSlideUp 0.7s ease 0.65s forwards;opacity:0}
.tag{font-family:'JetBrains Mono',monospace;font-size:10px;padding:4px 9px;border-radius:4px;border:0.5px solid #1e1e1e;color:#666;background:#0d0d0d;transition:all 0.2s;cursor:default;letter-spacing:0.02em}
.tag:hover{border-color:#3a3a3a;color:#ccc;background:#151515;transform:translateY(-1px)}
.stats-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;animation:fadeSlideUp 0.7s ease 0.8s forwards;opacity:0}
.stat{background:#0d0d0d;border:0.5px solid #1a1a1a;border-radius:8px;padding:14px 12px;text-align:center;transition:all 0.2s;position:relative;overflow:hidden}
.stat::before{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,#333,transparent);opacity:0;transition:opacity 0.3s}
.stat:hover{border-color:#2e2e2e;background:#111}
.stat:hover::before{opacity:1}
.stat-n{font-family:'JetBrains Mono',monospace;font-size:24px;font-weight:600;color:#fff;display:block;line-height:1}
.stat-l{font-size:10px;color:#444;margin-top:5px;font-family:'JetBrains Mono',monospace;letter-spacing:0.06em}
.graph-wrap{background:#0a0a0a;border:0.5px solid #1a1a1a;border-radius:8px;padding:14px;animation:fadeSlideUp 0.7s ease 0.95s forwards;opacity:0}
.graph-bars{display:flex;align-items:flex-end;gap:3px;height:64px}
.bar{flex:1;background:#1a1a1a;border-radius:2px;transition:background 0.2s;cursor:default;min-width:0}
.bar:hover{background:#3a3a3a}
.bar.active{background:#444}
.graph-labels{display:flex;justify-content:space-between;margin-top:6px}
.graph-lbl{font-size:9px;color:#333;font-family:'JetBrains Mono',monospace}
.footer-text{text-align:center;font-family:'JetBrains Mono',monospace;font-size:10px;color:#2a2a2a;padding-top:20px;letter-spacing:0.06em;animation:fadeSlideUp 0.7s ease 1.1s forwards;opacity:0}
.dot{display:inline-block;width:5px;height:5px;border-radius:50%;background:#3a3a3a;margin:0 6px;vertical-align:middle}
.dot.live{background:#2d5a3d;animation:livePulse 2s ease-in-out infinite}
@keyframes livePulse{0%,100%{opacity:1}50%{opacity:0.3}}
.cursor{display:inline-block;width:2px;height:14px;background:#555;vertical-align:text-bottom;margin-left:1px;animation:blink 1s step-end infinite}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}
</style>

<div class="wrap">
  <div class="banner">
    <canvas id="grid" style="position:absolute;inset:0;width:100%;height:100%;opacity:0.4"></canvas>
    <div class="scanline"></div>
    <svg class="horizon" viewBox="0 0 680 60" preserveAspectRatio="none" style="position:absolute;bottom:0">
      <path d="M0 45 Q120 28 200 38 Q300 50 400 30 Q480 18 560 32 Q620 40 680 28 L680 60 L0 60Z" fill="#0e0e0e"/>
      <path d="M0 55 Q100 48 180 52 Q280 58 380 46 Q460 38 540 50 Q610 56 680 44 L680 60 L0 60Z" fill="#0a0a0a"/>
    </svg>
    <div class="banner-text">
      <div class="banner-title">Welcome to Chheng Khim's Github<span class="cursor"></span></div>
      <div class="banner-sub">&lt; full stack · mobile · ui/ux /&gt;</div>
    </div>
  </div>

  <div class="body">
    <div class="links-row">
      <a class="lnk" href="mailto:pisethsambo763@gmail.com"><i class="ti ti-mail" style="font-size:11px;margin-right:4px" aria-hidden="true"></i>GMAIL</a>
      <a class="lnk" href="https://github.com/chhengkhim"><i class="ti ti-brand-github" style="font-size:11px;margin-right:4px" aria-hidden="true"></i>GITHUB</a>
      <a class="lnk" href="https://figma.com"><i class="ti ti-brand-figma" style="font-size:11px;margin-right:4px" aria-hidden="true"></i>FIGMA</a>
      <span class="lnk" style="cursor:default"><span class="dot live"></span>open to work</span>
    </div>

    <div class="divider"></div>

    <div style="margin-bottom:20px">
      <div class="section-label">about me</div>
      <div class="about-grid">
        <div>
          <div class="about-text">
            Hello! I'm <strong>Pisethsambo Phok</strong>, a Full Stack Developer & UI/UX Designer. I love building clean, modern web and mobile experiences.
          </div>
          <ul class="about-list">
            <li>Studying Computer Science</li>
            <li>Vue.js · Next.js · FastAPI · Flutter</li>
            <li>UI/UX with Figma</li>
            <li>Freelance &amp; collab friendly</li>
          </ul>
        </div>
        <div class="astro-frame">
          <svg class="astro-svg" viewBox="0 0 70 70" xmlns="http://www.w3.org/2000/svg">
            <ellipse cx="35" cy="38" rx="12" ry="14" fill="#1a1a1a" stroke="#333" stroke-width="0.5"/>
            <rect x="26" y="30" width="18" height="16" rx="3" fill="#222" stroke="#333" stroke-width="0.5"/>
            <circle cx="35" cy="24" r="9" fill="#1e1e1e" stroke="#444" stroke-width="0.5"/>
            <circle cx="35" cy="24" r="6" fill="#111" stroke="#333" stroke-width="0.5"/>
            <circle cx="35" cy="24" r="3" fill="#0a0a0a"/>
            <rect x="16" y="32" width="10" height="6" rx="2" fill="#181818" stroke="#333" stroke-width="0.5"/>
            <rect x="44" y="32" width="10" height="6" rx="2" fill="#181818" stroke="#333" stroke-width="0.5"/>
            <rect x="29" y="46" width="5" height="10" rx="1" fill="#181818" stroke="#2e2e2e" stroke-width="0.5"/>
            <rect x="36" y="46" width="5" height="10" rx="1" fill="#181818" stroke="#2e2e2e" stroke-width="0.5"/>
            <line x1="35" y1="20" x2="35" y2="12" stroke="#2e2e2e" stroke-width="0.5"/>
            <circle cx="35" cy="11" r="2" fill="none" stroke="#2e2e2e" stroke-width="0.5"/>
            <g id="astro-g" style="transform-origin:35px 35px">
              <circle cx="35" cy="5" r="1.5" fill="#333"/>
            </g>
          </svg>
        </div>
      </div>
    </div>

    <div class="divider"></div>

    <div style="margin-bottom:20px">
      <div class="section-label">technologies</div>
      <div class="tags-wrap">
        <span class="tag">vue.js</span><span class="tag">next.js</span><span class="tag">react</span><span class="tag">typescript</span><span class="tag">tailwind</span><span class="tag">bootstrap</span><span class="tag">python</span><span class="tag">fastapi</span><span class="tag">node.js</span><span class="tag">flutter</span><span class="tag">dart</span><span class="tag">postgresql</span><span class="tag">mysql</span><span class="tag">docker</span><span class="tag">git</span><span class="tag">linux</span><span class="tag">figma</span><span class="tag">wordpress</span>
      </div>
    </div>

    <div class="divider"></div>

    <div style="margin-bottom:20px">
      <div class="section-label">statistics</div>
      <div class="stats-grid">
        <div class="stat"><span class="stat-n" id="sn1">0</span><div class="stat-l">commits</div></div>
        <div class="stat"><span class="stat-n" id="sn2">0</span><div class="stat-l">streak days</div></div>
        <div class="stat"><span class="stat-n" id="sn3">0</span><div class="stat-l">repos</div></div>
      </div>
    </div>

    <div class="divider"></div>

    <div style="margin-bottom:4px">
      <div class="section-label">contribution graph</div>
      <div class="graph-wrap">
        <div class="graph-bars" id="graph-bars"></div>
        <div class="graph-labels">
          <span class="graph-lbl">Jan</span>
          <span class="graph-lbl">Mar</span>
          <span class="graph-lbl">May</span>
          <span class="graph-lbl">Jun</span>
        </div>
      </div>
    </div>

    <div class="footer-text">
      web<span class="dot"></span>mobile<span class="dot"></span>ui/ux<span class="dot"></span>open to work
    </div>
  </div>
</div>

<script>
const canvas = document.getElementById('grid');
const ctx = canvas.getContext('2d');
function drawGrid() {
  canvas.width = canvas.offsetWidth;
  canvas.height = canvas.offsetHeight;
  ctx.clearRect(0,0,canvas.width,canvas.height);
  ctx.strokeStyle = 'rgba(255,255,255,0.04)';
  ctx.lineWidth = 0.5;
  const sz = 32;
  for(let x=0;x<canvas.width;x+=sz){ctx.beginPath();ctx.moveTo(x,0);ctx.lineTo(x,canvas.height);ctx.stroke()}
  for(let y=0;y<canvas.height;y+=sz){ctx.beginPath();ctx.moveTo(0,y);ctx.lineTo(canvas.width,y);ctx.stroke()}
}
drawGrid();

const bars = document.getElementById('graph-bars');
const heights = [8,15,6,22,12,30,18,10,25,40,20,35,15,28,12,45,30,18,22,38,16,28,10,42,20,34,15,25,8,20,35,28,15,40,22,30];
heights.forEach((h,i)=>{
  const b = document.createElement('div');
  b.className = 'bar' + (i > 28 ? ' active' : '');
  b.style.height = '0px';
  b.style.transition = `height 0.5s ease ${i*0.015}s`;
  bars.appendChild(b);
  setTimeout(()=>{ b.style.height = h+'px'; }, 300);
});

function animateNum(el, target, duration) {
  const start = performance.now();
  const update = (now) => {
    const t = Math.min((now-start)/duration, 1);
    const ease = 1-Math.pow(1-t,3);
    el.textContent = Math.round(target*ease);
    if(t<1) requestAnimationFrame(update);
  };
  requestAnimationFrame(update);
}
setTimeout(()=>{
  animateNum(document.getElementById('sn1'), 247, 1400);
  animateNum(document.getElementById('sn2'), 42, 1000);
  animateNum(document.getElementById('sn3'), 18, 800);
}, 500);

let angle = 0;
const astroG = document.getElementById('astro-g');
(function orbit(){
  angle += 0.008;
  const x = 35 + Math.cos(angle)*28;
  const y = 35 + Math.sin(angle)*18;
  astroG.setAttribute('transform', `translate(${x-35},${y-35})`);
  requestAnimationFrame(orbit);
})();
</script>
