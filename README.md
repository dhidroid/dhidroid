
<style>
  @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700&family=Sora:wght@300;400;600;700&display=swap');

  * { box-sizing: border-box; margin: 0; padding: 0; }

  .rp { font-family: 'Sora', sans-serif; background: #0a0c10; color: #e2e8f0; min-height: 100vh; padding: 2rem 1.5rem; line-height: 1.6; }

  .header { text-align: center; padding: 2.5rem 0 2rem; position: relative; }
  .header::before {
    content: '';
    position: absolute; top: 0; left: 50%; transform: translateX(-50%);
    width: 1px; height: 40px; background: linear-gradient(to bottom, transparent, #00ff9d40);
  }

  .name-tag { font-family: 'JetBrains Mono', monospace; font-size: 11px; color: #00ff9d; letter-spacing: 0.2em; text-transform: uppercase; margin-bottom: 0.75rem; opacity: 0; animation: fadeUp 0.6s ease forwards 0.2s; }
  .main-name { font-size: clamp(1.8rem, 5vw, 2.8rem); font-weight: 700; color: #f8fafc; letter-spacing: -0.02em; line-height: 1.1; opacity: 0; animation: fadeUp 0.6s ease forwards 0.4s; }
  .main-name span { color: #00ff9d; }
  .subtitle { font-size: 0.95rem; color: #64748b; font-weight: 300; margin-top: 0.5rem; opacity: 0; animation: fadeUp 0.6s ease forwards 0.6s; }

  .divider { width: 60px; height: 1px; background: #00ff9d30; margin: 1.5rem auto; opacity: 0; animation: fadeUp 0.4s ease forwards 0.8s; }

  .stats-row { display: flex; gap: 1px; justify-content: center; margin: 1.5rem 0; flex-wrap: wrap; gap: 8px; opacity: 0; animation: fadeUp 0.5s ease forwards 0.9s; }
  .stat-chip { font-family: 'JetBrains Mono', monospace; font-size: 10px; color: #94a3b8; background: #0f1318; border: 1px solid #1e2530; padding: 6px 14px; border-radius: 100px; letter-spacing: 0.05em; }
  .stat-chip strong { color: #00ff9d; }

  .section { margin: 2rem 0; opacity: 0; animation: fadeUp 0.5s ease forwards; }
  .section-label { font-family: 'JetBrains Mono', monospace; font-size: 10px; color: #334155; letter-spacing: 0.2em; text-transform: uppercase; margin-bottom: 1rem; display: flex; align-items: center; gap: 8px; }
  .section-label::after { content: ''; flex: 1; height: 1px; background: #1e2530; }

  .about-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 10px; }
  .about-card { background: #0f1318; border: 1px solid #1e2530; border-radius: 8px; padding: 1rem 1.1rem; transition: border-color 0.2s; }
  .about-card:hover { border-color: #00ff9d30; }
  .about-card .label { font-family: 'JetBrains Mono', monospace; font-size: 9px; color: #334155; letter-spacing: 0.15em; text-transform: uppercase; margin-bottom: 4px; }
  .about-card .val { font-size: 13px; color: #cbd5e1; font-weight: 400; }

  .skills-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(160px, 1fr)); gap: 8px; }
  .skill-item { background: #0f1318; border: 1px solid #1e2530; border-radius: 8px; padding: 0.75rem 1rem; display: flex; align-items: center; gap: 10px; transition: all 0.2s; cursor: default; }
  .skill-item:hover { border-color: #00ff9d40; transform: translateY(-1px); }
  .skill-dot { width: 8px; height: 8px; border-radius: 50%; background: #00ff9d; flex-shrink: 0; }
  .skill-dot.amber { background: #fbbf24; }
  .skill-dot.blue { background: #60a5fa; }
  .skill-dot.coral { background: #f87171; }
  .skill-dot.purple { background: #a78bfa; }
  .skill-name { font-family: 'JetBrains Mono', monospace; font-size: 11px; color: #94a3b8; }
  .skill-name strong { display: block; font-size: 12px; color: #e2e8f0; font-weight: 500; }

  .currently-row { display: flex; flex-wrap: wrap; gap: 8px; }
  .tag { font-family: 'JetBrains Mono', monospace; font-size: 10px; border: 1px solid; border-radius: 4px; padding: 5px 12px; letter-spacing: 0.05em; }
  .tag.green { color: #00ff9d; border-color: #00ff9d30; background: #00ff9d08; }
  .tag.blue { color: #60a5fa; border-color: #60a5fa30; background: #60a5fa08; }
  .tag.amber { color: #fbbf24; border-color: #fbbf2430; background: #fbbf2408; }
  .tag.purple { color: #a78bfa; border-color: #a78bfa30; background: #a78bfa08; }

  .reach-row { display: flex; gap: 10px; flex-wrap: wrap; }
  .reach-link { display: flex; align-items: center; gap: 8px; background: #0f1318; border: 1px solid #1e2530; border-radius: 8px; padding: 0.6rem 1rem; font-family: 'JetBrains Mono', monospace; font-size: 11px; color: #94a3b8; text-decoration: none; transition: all 0.2s; }
  .reach-link:hover { border-color: #00ff9d30; color: #e2e8f0; }
  .reach-link .dot { width: 6px; height: 6px; border-radius: 50%; }

  .terminal { background: #080a0d; border: 1px solid #1e2530; border-radius: 8px; padding: 1rem 1.2rem; font-family: 'JetBrains Mono', monospace; font-size: 11px; }
  .terminal .line { color: #334155; margin-bottom: 2px; }
  .terminal .line .prompt { color: #00ff9d; }
  .terminal .line .cmd { color: #60a5fa; }
  .terminal .line .out { color: #64748b; }
  .cursor { display: inline-block; width: 7px; height: 12px; background: #00ff9d; animation: blink 1.2s step-end infinite; vertical-align: -2px; margin-left: 2px; }

  @keyframes fadeUp { from { opacity: 0; transform: translateY(12px); } to { opacity: 1; transform: translateY(0); } }
  @keyframes blink { 50% { opacity: 0; } }

  .section:nth-child(1) { animation-delay: 1.0s; }
  .section:nth-child(2) { animation-delay: 1.2s; }
  .section:nth-child(3) { animation-delay: 1.4s; }
  .section:nth-child(4) { animation-delay: 1.6s; }
  .section:nth-child(5) { animation-delay: 1.8s; }
</style>

<div class="rp">
  <div class="header">
    <div class="name-tag">// developer profile</div>
    <div class="main-name">Dhinesh<span>Kumar</span><br>Thirupathi</div>
    <div class="subtitle">Mobile App Developer · Chennai, India</div>
    <div class="divider"></div>
    <div class="stats-row">
      <div class="stat-chip">React Native <strong>primary</strong></div>
      <div class="stat-chip">Open Source <strong>advocate</strong></div>
      <div class="stat-chip">Full Stack <strong>capable</strong></div>
    </div>
  </div>

  <div class="section">
    <div class="section-label">about</div>
    <div class="terminal">
      <div class="line"><span class="prompt">$</span> <span class="cmd">whoami</span></div>
      <div class="line"><span class="out">→ Mobile developer building cross-platform apps with React Native</span></div>
      <div class="line"><span class="out">→ Exploring Go, Docker, and GitOps in production pipelines</span></div>
      <div class="line"><span class="out">→ Open to collaborating on meaningful open-source projects</span></div>
      <div class="line"><span class="out">→ Ask me anything about GoLang, React, or Android</span></div>
      <div class="line" style="margin-top:8px;"><span class="prompt">$</span> <span class="cursor"></span></div>
    </div>
  </div>

  <div class="section">
    <div class="section-label">currently learning</div>
    <div class="currently-row">
      <div class="tag green">React Native</div>
      <div class="tag blue">GoLang</div>
      <div class="tag amber">Docker</div>
      <div class="tag purple">GitOps</div>
    </div>
  </div>

  <div class="section">
    <div class="section-label">tech stack</div>
    <div class="skills-grid">
      <div class="skill-item"><div class="skill-dot"></div><div class="skill-name"><strong>React Native</strong>mobile apps</div></div>
      <div class="skill-item"><div class="skill-dot"></div><div class="skill-name"><strong>React.js</strong>web frontend</div></div>
      <div class="skill-item"><div class="skill-dot blue"></div><div class="skill-name"><strong>TypeScript</strong>type safety</div></div>
      <div class="skill-item"><div class="skill-dot blue"></div><div class="skill-name"><strong>JavaScript</strong>core language</div></div>
      <div class="skill-item"><div class="skill-dot amber"></div><div class="skill-name"><strong>GoLang</strong>backend</div></div>
      <div class="skill-item"><div class="skill-dot amber"></div><div class="skill-name"><strong>Node.js</strong>server-side</div></div>
      <div class="skill-item"><div class="skill-dot blue"></div><div class="skill-name"><strong>Express.js</strong>REST APIs</div></div>
      <div class="skill-item"><div class="skill-dot coral"></div><div class="skill-name"><strong>Redux</strong>state mgmt</div></div>
      <div class="skill-item"><div class="skill-dot coral"></div><div class="skill-name"><strong>Firebase</strong>BaaS</div></div>
      <div class="skill-item"><div class="skill-dot amber"></div><div class="skill-name"><strong>Docker</strong>containers</div></div>
      <div class="skill-item"><div class="skill-dot purple"></div><div class="skill-name"><strong>Tailwind CSS</strong>styling</div></div>
      <div class="skill-item"><div class="skill-dot"></div><div class="skill-name"><strong>Git / Bash</strong>version ctrl</div></div>
    </div>
  </div>

  <div class="section">
    <div class="section-label">connect</div>
    <div class="reach-row">
      <a class="reach-link" href="https://linkedin.com/in/dhineshkumar-thirupathi-00aa8b1a5"><div class="dot" style="background:#60a5fa"></div>LinkedIn</a>
      <a class="reach-link" href="mailto:dhinesh4668@outlook.com"><div class="dot" style="background:#00ff9d"></div>dhinesh4668@outlook.com</a>
      <a class="reach-link" href="https://dhinesh-4668.web.app/"><div class="dot" style="background:#fbbf24"></div>Portfolio</a>
    </div>
  </div>
</div>
