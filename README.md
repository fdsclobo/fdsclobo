<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Fernando Seminario Conte — Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Sora:wght@300;400;600;700&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0b0d11;
    --surface: #12151c;
    --surface2: #1a1e28;
    --border: rgba(255,255,255,0.07);
    --border-hover: rgba(255,255,255,0.15);
    --accent: #4fffb0;
    --accent2: #00c2ff;
    --accent3: #a78bfa;
    --text: #e8eaf0;
    --muted: #7a8090;
    --mono: 'Space Mono', monospace;
    --sans: 'Sora', sans-serif;
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: var(--sans);
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
    line-height: 1.7;
  }

  /* Subtle grid bg */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(79,255,176,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(79,255,176,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  /* NAV */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2.5rem;
    background: rgba(11,13,17,0.85);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
  }

  .nav-logo {
    font-family: var(--mono);
    font-size: 0.85rem;
    color: var(--accent);
    letter-spacing: 0.05em;
  }

  .nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
  }

  .nav-links a {
    font-family: var(--mono);
    font-size: 0.78rem;
    color: var(--muted);
    text-decoration: none;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    transition: color 0.2s;
  }

  .nav-links a:hover { color: var(--accent); }

  /* HERO */
  .hero {
    position: relative;
    z-index: 1;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 7rem 2.5rem 4rem;
    max-width: 900px;
    margin: 0 auto;
  }

  .hero-tag {
    font-family: var(--mono);
    font-size: 0.78rem;
    color: var(--accent);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin-bottom: 1.5rem;
    display: flex;
    align-items: center;
    gap: 0.75rem;
  }

  .hero-tag::before {
    content: '';
    display: block;
    width: 32px;
    height: 1px;
    background: var(--accent);
  }

  h1 {
    font-size: clamp(2.8rem, 7vw, 5.5rem);
    font-weight: 700;
    line-height: 1.05;
    letter-spacing: -0.03em;
    margin-bottom: 1rem;
  }

  h1 span {
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-sub {
    font-size: 1.15rem;
    color: var(--muted);
    max-width: 480px;
    margin-bottom: 2.5rem;
    font-weight: 300;
  }

  .hero-sub strong {
    color: var(--text);
    font-weight: 400;
  }

  .hero-cta {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
  }

  .btn {
    font-family: var(--mono);
    font-size: 0.8rem;
    letter-spacing: 0.06em;
    padding: 0.75rem 1.75rem;
    border-radius: 6px;
    text-decoration: none;
    transition: all 0.2s;
    cursor: pointer;
  }

  .btn-primary {
    background: var(--accent);
    color: #0b0d11;
    border: 1px solid var(--accent);
    font-weight: 700;
  }

  .btn-primary:hover {
    background: transparent;
    color: var(--accent);
  }

  .btn-ghost {
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border-hover);
  }

  .btn-ghost:hover {
    border-color: var(--accent);
    color: var(--accent);
  }

  /* STATUS BADGE */
  .status-badge {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.4rem 1rem;
    background: rgba(79,255,176,0.08);
    border: 1px solid rgba(79,255,176,0.2);
    border-radius: 99px;
    font-family: var(--mono);
    font-size: 0.72rem;
    color: var(--accent);
    margin-bottom: 2rem;
  }

  .status-dot {
    width: 7px; height: 7px;
    border-radius: 50%;
    background: var(--accent);
    animation: pulse 2s infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.3; }
  }

  /* SECTIONS */
  section {
    position: relative;
    z-index: 1;
    max-width: 900px;
    margin: 0 auto;
    padding: 5rem 2.5rem;
  }

  .section-label {
    font-family: var(--mono);
    font-size: 0.72rem;
    color: var(--accent);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 0.5rem;
  }

  .section-title {
    font-size: 2rem;
    font-weight: 700;
    letter-spacing: -0.02em;
    margin-bottom: 3rem;
    color: var(--text);
  }

  .divider {
    height: 1px;
    background: var(--border);
    max-width: 900px;
    margin: 0 auto;
  }

  /* ABOUT */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
  }

  .about-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 1.75rem;
    transition: border-color 0.2s;
  }

  .about-card:hover { border-color: var(--border-hover); }

  .about-card-icon {
    font-size: 1.5rem;
    margin-bottom: 0.75rem;
  }

  .about-card h3 {
    font-size: 0.85rem;
    font-weight: 600;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.08em;
    margin-bottom: 0.4rem;
    font-family: var(--mono);
  }

  .about-card p {
    font-size: 1rem;
    color: var(--text);
  }

  /* EDUCATION */
  .edu-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 2rem;
    margin-bottom: 1rem;
    display: flex;
    gap: 1.5rem;
    align-items: flex-start;
    transition: border-color 0.2s;
  }

  .edu-card:hover { border-color: var(--border-hover); }

  .edu-icon {
    width: 48px;
    height: 48px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.4rem;
    flex-shrink: 0;
  }

  .edu-icon.unlp { background: rgba(0,194,255,0.1); border: 1px solid rgba(0,194,255,0.2); }
  .edu-icon.java { background: rgba(167,139,250,0.1); border: 1px solid rgba(167,139,250,0.2); }

  .edu-info h3 {
    font-size: 1.05rem;
    font-weight: 600;
    margin-bottom: 0.25rem;
  }

  .edu-info .inst {
    font-family: var(--mono);
    font-size: 0.78rem;
    color: var(--accent2);
    margin-bottom: 0.5rem;
  }

  .edu-info .inst.java-color { color: var(--accent3); }

  .edu-info p {
    font-size: 0.9rem;
    color: var(--muted);
  }

  .badge-status {
    display: inline-block;
    padding: 0.2rem 0.65rem;
    border-radius: 4px;
    font-family: var(--mono);
    font-size: 0.68rem;
    font-weight: 700;
    letter-spacing: 0.06em;
    text-transform: uppercase;
  }

  .badge-active {
    background: rgba(79,255,176,0.1);
    color: var(--accent);
    border: 1px solid rgba(79,255,176,0.25);
  }

  /* SKILLS */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
    gap: 1rem;
  }

  .skill-pill {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 1rem 1.25rem;
    text-align: center;
    transition: all 0.2s;
  }

  .skill-pill:hover {
    border-color: var(--accent);
    transform: translateY(-2px);
  }

  .skill-pill .sk-icon { font-size: 1.6rem; margin-bottom: 0.5rem; }

  .skill-pill span {
    display: block;
    font-family: var(--mono);
    font-size: 0.75rem;
    color: var(--muted);
  }

  /* CONTACT */
  .contact-box {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 3rem;
    text-align: center;
  }

  .contact-box h2 {
    font-size: 2rem;
    font-weight: 700;
    margin-bottom: 0.75rem;
  }

  .contact-box p {
    color: var(--muted);
    margin-bottom: 2rem;
    max-width: 400px;
    margin-left: auto;
    margin-right: auto;
  }

  .contact-links {
    display: flex;
    justify-content: center;
    gap: 1rem;
    flex-wrap: wrap;
  }

  /* FOOTER */
  footer {
    position: relative;
    z-index: 1;
    text-align: center;
    padding: 2rem;
    font-family: var(--mono);
    font-size: 0.72rem;
    color: var(--muted);
    border-top: 1px solid var(--border);
  }

  /* ANIMATIONS */
  .fade-up {
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }
  .fade-up.visible {
    opacity: 1;
    transform: none;
  }

  @media (max-width: 640px) {
    nav { padding: 1rem 1.25rem; }
    .nav-links { gap: 1rem; }
    .hero { padding: 6rem 1.25rem 3rem; }
    section { padding: 3.5rem 1.25rem; }
    .about-grid { grid-template-columns: 1fr; }
    .edu-card { flex-direction: column; }
    .contact-box { padding: 2rem 1.25rem; }
  }
</style>
</head>
<body>

<nav>
  <div class="nav-logo">fsc.dev</div>
  <ul class="nav-links">
    <li><a href="#sobre-mi">Sobre mí</a></li>
    <li><a href="#educacion">Educación</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#contacto">Contacto</a></li>
  </ul>
</nav>

<!-- HERO -->
<div class="hero">
  <div class="status-badge">
    <span class="status-dot"></span>
    Disponible para proyectos y colaboraciones
  </div>

  <div class="hero-tag">Desarrollador en formación</div>

  <h1>
    Fernando<br>
    <span>Seminario Conte</span>
  </h1>

  <p class="hero-sub">
    Tengo <strong>35 años</strong>, soy de La Plata, Buenos Aires. Estudio
    <strong>Licenciatura en Sistemas (UNLP)</strong> y me especializo en
    <strong>Backend con Java</strong>.
  </p>

  <div class="hero-cta">
    <a href="#educacion" class="btn btn-primary">Ver mi camino</a>
    <a href="#contacto" class="btn btn-ghost">Contactarme</a>
  </div>
</div>

<div class="divider"></div>

<!-- SOBRE MÍ -->
<section id="sobre-mi">
  <div class="section-label">// 01</div>
  <div class="section-title">Sobre mí</div>

  <div class="about-grid">
    <div class="about-card fade-up">
      <div class="about-card-icon">🎯</div>
      <h3>Enfoque</h3>
      <p>Apasionado por el desarrollo backend, la arquitectura de sistemas y escribir código limpio y eficiente.</p>
    </div>
    <div class="about-card fade-up" style="transition-delay:0.1s">
      <div class="about-card-icon">📍</div>
      <h3>Ubicación</h3>
      <p>La Plata, Buenos Aires, Argentina.</p>
    </div>
    <div class="about-card fade-up" style="transition-delay:0.2s">
      <div class="about-card-icon">📚</div>
      <h3>Actualmente estudiando</h3>
      <p>Lic. en Sistemas en la UNLP + Curso de Backend en Java.</p>
    </div>
    <div class="about-card fade-up" style="transition-delay:0.3s">
      <div class="about-card-icon">🚀</div>
      <h3>Objetivo</h3>
      <p>Construir soluciones robustas y escalar como desarrollador backend profesional.</p>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- EDUCACIÓN -->
<section id="educacion">
  <div class="section-label">// 02</div>
  <div class="section-title">Educación</div>

  <div class="edu-card fade-up">
    <div class="edu-icon unlp">🎓</div>
    <div class="edu-info">
      <h3>Licenciatura en Sistemas</h3>
      <div class="inst">Universidad Nacional de La Plata (UNLP)</div>
      <p>Formación en fundamentos de la computación, algoritmos, bases de datos, ingeniería de software y sistemas distribuidos.</p>
      &nbsp;
      <span class="badge-status badge-active">En curso</span>
    </div>
  </div>

  <div class="edu-card fade-up" style="transition-delay:0.15s">
    <div class="edu-icon java">☕</div>
    <div class="edu-info">
      <h3>Curso de Backend — Java</h3>
      <div class="inst java-color">Desarrollo Profesional</div>
      <p>Spring Boot, APIs REST, JPA/Hibernate, manejo de bases de datos relacionales y buenas prácticas de desarrollo backend.</p>
      &nbsp;
      <span class="badge-status badge-active">En curso</span>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- SKILLS -->
<section id="skills">
  <div class="section-label">// 03</div>
  <div class="section-title">Tecnologías & Skills</div>

  <div class="skills-grid">
    <div class="skill-pill fade-up">
      <div class="sk-icon">☕</div>
      <span>Java</span>
    </div>
    <div class="skill-pill fade-up" style="transition-delay:0.05s">
      <div class="sk-icon">🍃</div>
      <span>Spring Boot</span>
    </div>
    <div class="skill-pill fade-up" style="transition-delay:0.1s">
      <div class="sk-icon">🗄️</div>
      <span>SQL / JPA</span>
    </div>
    <div class="skill-pill fade-up" style="transition-delay:0.15s">
      <div class="sk-icon">🔗</div>
      <span>REST APIs</span>
    </div>
    <div class="skill-pill fade-up" style="transition-delay:0.2s">
      <div class="sk-icon">🐙</div>
      <span>Git & GitHub</span>
    </div>
    <div class="skill-pill fade-up" style="transition-delay:0.25s">
      <div class="sk-icon">🐧</div>
      <span>Linux</span>
    </div>
    <div class="skill-pill fade-up" style="transition-delay:0.3s">
      <div class="sk-icon">📐</div>
      <span>Algoritmos</span>
    </div>
    <div class="skill-pill fade-up" style="transition-delay:0.35s">
      <div class="sk-icon">🏗️</div>
      <span>OOP</span>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- CONTACTO -->
<section id="contacto">
  <div class="contact-box fade-up">
    <h2>¿Hablamos?</h2>
    <p>Estoy abierto a colaboraciones, proyectos académicos y oportunidades de aprendizaje.</p>
    <div class="contact-links">
      <a href="https://github.com/" class="btn btn-primary" target="_blank">GitHub</a>
      <a href="mailto:fernando@email.com" class="btn btn-ghost">✉ Email</a>
      <a href="https://linkedin.com/" class="btn btn-ghost" target="_blank">LinkedIn</a>
    </div>
  </div>
</section>

<footer>
  <p>Construido con HTML puro · Fernando Seminario Conte © 2025</p>
</footer>

<script>
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) e.target.classList.add('visible');
    });
  }, { threshold: 0.15 });

  document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));
</script>

</body>
</html>

  <!-- Change the `github-readme-stats.anuraghazra1.vercel.app` to `github-readme-stats.vercel.app`  -->

  <img align="center" src="https://github-readme-stats.anuraghazra1.vercel.app/api/pin/?username=nneji123&repo=Alien-Shooter&theme=tokyonight" />

</a> 

<p align="center">
  <img  src="https://raw.githubusercontent.com/Elanza-48/Elanza-48/main/resources/img/github-contribution-grid-snake.svg"
    alt="example" />
</p>

-----
