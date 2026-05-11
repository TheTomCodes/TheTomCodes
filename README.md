<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Mahammadali Aglodiya · Advanced Interactive Portfolio</title>
  <!-- Google Fonts + Font Awesome 6 (free) -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: radial-gradient(circle at 10% 20%, #0a0c12, #03050b);
      font-family: 'Inter', sans-serif;
      color: #eef2ff;
      line-height: 1.5;
      scroll-behavior: smooth;
    }

    /* animated grain texture */
    body::before {
      content: "";
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-image: url('data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIzMDAiIGhlaWdodD0iMzAwIj48ZmlsdGVyIGlkPSJmIj48ZmVUdXJidWxlbmNlIHR5cGU9ImZyYWN0YWxOb2lzZSIgYmFzZUZyZXF1ZW5jeT0iLjciIG51bU9jdGF2ZXM9IjMiLz48L2ZpbHRlcj48cmVjdCB3aWR0aD0iMTAwJSIgaGVpZ2h0PSIxMDAlIiBmaWx0ZXI9InVybCgjZikiIG9wYWNpdHk9IjAuMDMiLz48L3N2Zz4=');
      background-repeat: repeat;
      opacity: 0.2;
      pointer-events: none;
      z-index: 0;
    }

    .container {
      max-width: 1300px;
      margin: 0 auto;
      padding: 2rem 1.5rem;
      position: relative;
      z-index: 2;
    }

    /* glassmorphic cards */
    .glass-card {
      background: rgba(18, 22, 35, 0.55);
      backdrop-filter: blur(12px);
      border: 1px solid rgba(96, 165, 250, 0.2);
      border-radius: 2rem;
      box-shadow: 0 20px 35px -15px rgba(0, 0, 0, 0.4), 0 0 0 0.5px rgba(124, 58, 237, 0.1) inset;
      transition: all 0.3s ease;
    }

    .glass-card:hover {
      border-color: rgba(124, 58, 237, 0.5);
      box-shadow: 0 25px 40px -12px rgba(0, 0, 0, 0.5), 0 0 0 1px rgba(124, 58, 237, 0.3) inset;
      transform: translateY(-3px);
    }

    /* gradient text */
    .gradient-text {
      background: linear-gradient(135deg, #C084FC, #60A5FA, #34D399);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      font-weight: 800;
    }

    /* badge & tech chips */
    .tech-chip {
      background: rgba(124, 58, 237, 0.18);
      border-radius: 40px;
      padding: 0.3rem 1rem;
      font-size: 0.75rem;
      font-weight: 500;
      backdrop-filter: blur(4px);
      border: 0.5px solid rgba(139, 92, 246, 0.4);
      transition: 0.2s;
    }
    .tech-chip:hover {
      background: rgba(124, 58, 237, 0.4);
      border-color: #a855f7;
    }

    /* animated hero button */
    .btn-glow {
      background: linear-gradient(95deg, #7c3aed, #a855f7);
      border: none;
      padding: 0.8rem 1.8rem;
      border-radius: 60px;
      font-weight: 600;
      color: white;
      transition: all 0.3s;
      box-shadow: 0 0 8px #a855f7;
    }
    .btn-glow:hover {
      transform: scale(1.02);
      box-shadow: 0 0 20px #c084fc;
      background: linear-gradient(95deg, #8b5cf6, #c084fc);
    }

    /* skills grid */
    .skills-wrapper {
      display: flex;
      flex-wrap: wrap;
      gap: 0.6rem;
      margin-top: 1rem;
    }

    /* project cards grid */
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 1.8rem;
    }

    /* timeline simple */
    .timeline-item {
      border-left: 2px solid #7c3aed;
      padding-left: 1.2rem;
      position: relative;
      margin-bottom: 1.5rem;
    }
    .timeline-item::before {
      content: "▹";
      position: absolute;
      left: -12px;
      top: 0;
      color: #c084fc;
      font-size: 1rem;
    }

    /* live typing + status */
    #dynamic-activity {
      font-weight: 600;
      background: linear-gradient(120deg, #a78bfa, #2dd4bf);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
    }

    /* stats images responsive */
    .stats-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem;
      margin-top: 1.5rem;
    }
    .stats-row img {
      max-width: 100%;
      border-radius: 16px;
      background: #0b0e17;
      box-shadow: 0 8px 20px rgba(0,0,0,0.3);
    }

    /* footer wave effect */
    .footer-wave {
      text-align: center;
      margin-top: 3rem;
      padding-top: 1.5rem;
      border-top: 1px solid rgba(96, 165, 250, 0.2);
    }

    /* responsive adjustments */
    @media (max-width: 768px) {
      .container { padding: 1.2rem; }
      .hero-flex { flex-direction: column; text-align: center; }
      .social-links { justify-content: center; }
    }

    a {
      text-decoration: none;
      color: inherit;
    }

    .social-icon {
      background: rgba(255,255,255,0.05);
      border-radius: 50%;
      width: 40px;
      height: 40px;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      transition: all 0.2s;
      font-size: 1.2rem;
    }
    .social-icon:hover {
      background: #7c3aed;
      transform: translateY(-4px);
    }
  </style>
</head>
<body>
<div class="container">
  
  <!-- HERO SECTION with live typing + wave banner -->
  <div class="glass-card" style="padding: 2rem 2rem 1.8rem; margin-bottom: 2rem; overflow: hidden;">
    <div class="hero-flex" style="display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 1.5rem;">
      <div>
        <div style="display: flex; align-items: center; gap: 0.8rem; flex-wrap: wrap;">
          <h1 style="font-size: 2.8rem; font-weight: 800; letter-spacing: -0.02em;">Mahammadali <span class="gradient-text">Aglodiya</span></h1>
          <span style="background: #1e1b2f; border-radius: 60px; padding: 0.2rem 0.8rem; font-size: 0.8rem; border: 1px solid #7c3aed;"><i class="fas fa-map-marker-alt" style="color:#60a5fa;"></i> Ahmedabad, India 🇮🇳</span>
        </div>
        <!-- Live typing effect (rotating roles) -->
        <div style="margin-top: 0.5rem; font-size: 1.3rem; font-weight: 500;">
          <i class="fas fa-code" style="color: #a855f7; margin-right: 6px;"></i>
          <span id="typed-text" style="color: #cbd5e6;"></span>
          <span class="cursor-blink" style="background-color: #c084fc; width: 2px; display: inline-block; margin-left: 2px;">|</span>
        </div>
        <p style="max-width: 550px; margin-top: 1rem; color: #b9c7dd;">MCA student · Full-stack developer · AI/ML explorer. I build scalable, user-centric applications with clean code & modern design.</p>
        <div style="margin-top: 1.5rem; display: flex; gap: 1rem; flex-wrap: wrap;">
          <a href="mailto:mohammadaliaglodiya51@gmail.com" class="btn-glow"><i class="far fa-envelope"></i> Contact Me</a>
          <a href="https://github.com/TheTomCodes" target="_blank" style="background: rgba(255,255,255,0.05); backdrop-filter: blur(8px); border-radius: 60px; padding: 0.8rem 1.5rem; font-weight: 500; transition: 0.2s;"><i class="fab fa-github"></i> GitHub</a>
        </div>
      </div>
      <!-- dynamic live status widget -->
      <div style="background: rgba(0,0,0,0.4); border-radius: 2rem; padding: 1rem 2rem; text-align: center; border: 1px solid rgba(96,165,250,0.3);">
        <div><i class="fas fa-sync-alt fa-fw" style="color: #2dd4bf;"></i> <span style="font-size: 0.9rem;">LIVE ACTIVITY</span></div>
        <div id="live-status" style="font-size: 1rem; margin-top: 8px; font-weight: 500;"><span id="dynamic-activity">Building modern UIs</span> <span style="font-size:0.8rem;">✨</span></div>
        <div style="font-size: 0.7rem; margin-top: 12px;"><i class="far fa-clock"></i> <span id="live-clock"></span> IST</div>
      </div>
    </div>
    <!-- Social Icons row -->
    <div class="social-links" style="display: flex; gap: 1rem; margin-top: 2rem; flex-wrap: wrap;">
      <a href="https://twitter.com/mahammadali2004" target="_blank" class="social-icon"><i class="fab fa-twitter"></i></a>
      <a href="https://linkedin.com/in/mahammadali-aglodiya" target="_blank" class="social-icon"><i class="fab fa-linkedin-in"></i></a>
      <a href="https://discord.gg/TheTomCodes" target="_blank" class="social-icon"><i class="fab fa-discord"></i></a>
      <a href="mailto:mohammadaliaglodiya51@gmail.com" class="social-icon"><i class="fas fa-envelope"></i></a>
      <a href="https://github.com/TheTomCodes" target="_blank" class="social-icon"><i class="fab fa-github"></i></a>
    </div>
  </div>

  <!-- two column layout: about + skills / summary -->
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 1.8rem; margin-bottom: 2.5rem;">
    <!-- Profile Summary Card -->
    <div class="glass-card" style="padding: 1.8rem;">
      <h3 style="display: flex; gap: 0.5rem; margin-bottom: 1rem;"><i class="fas fa-user-astronaut" style="color:#60a5fa"></i> Profile Summary</h3>
      <p style="color: #d1dbf0;">MCA student with a strong foundation in web development and hands-on experience in Python, PHP, JavaScript, and MySQL. Passionate about building scalable, user-friendly web applications using clean code and responsive design. Experienced in AI/ML integration through a BISAG-N internship involving YOLOv8-based satellite image detection, FastAPI, and Flask.</p>
      <div style="margin-top: 1.2rem;">
        <div><i class="fas fa-graduation-cap"></i> <strong>Education:</strong> MCA (LJIMS) 2024–Present · BCA (I.T. Sheliya Jafari) 2021–2024</div>
        <div><i class="fas fa-briefcase"></i> <strong>Intern:</strong> Python Developer @ BISAG-N (3 months)</div>
      </div>
    </div>
    <!-- Skills + Tools advanced chips -->
    <div class="glass-card" style="padding: 1.8rem;">
      <h3 style="display: flex; gap: 0.5rem; margin-bottom: 1rem;"><i class="fas fa-cogs"></i> Tech Arsenal</h3>
      <div class="skills-wrapper">
        <span class="tech-chip">C / C++</span><span class="tech-chip">C#</span><span class="tech-chip">Java</span><span class="tech-chip">Python</span>
        <span class="tech-chip">PHP</span><span class="tech-chip">JavaScript</span><span class="tech-chip">HTML5/CSS3</span>
        <span class="tech-chip">React</span><span class="tech-chip">Laravel</span><span class="tech-chip">FastAPI</span><span class="tech-chip">Flask</span>
        <span class="tech-chip">TailwindCSS</span><span class="tech-chip">Bootstrap</span><span class="tech-chip">MySQL/PostgreSQL</span>
        <span class="tech-chip">YOLOv8</span><span class="tech-chip">OpenCV</span><span class="tech-chip">Git/GitHub</span>
        <span class="tech-chip">Flutter</span><span class="tech-chip">ASP.NET (learning)</span>
      </div>
      <hr style="border-color: #2d2f40; margin: 1rem 0;">
      <div><i class="fas fa-tools"></i> <strong>Tools & IDEs:</strong> VS Code, Visual Studio, Jupyter, Spyder, XAMPP, WordPress, Figma basics</div>
    </div>
  </div>

  <!-- Featured Project Highlight -->
  <div class="glass-card" style="margin-bottom: 2rem; padding: 1.5rem; background: linear-gradient(105deg, rgba(80, 40, 150, 0.2), rgba(20, 30, 60, 0.4));">
    <div style="display: flex; justify-content: space-between; flex-wrap: wrap; align-items: center;">
      <div>
        <span style="background: #7c3aed30; border-radius: 40px; padding: 0.2rem 1rem; font-size: 0.7rem; font-weight: bold;"><i class="fas fa-star-of-life"></i> ACTIVE PROJECT</span>
        <h2 style="margin-top: 0.5rem;">🛒 Grocery Store Management System</h2>
        <p>Full-featured inventory, billing, role-based access & analytics dashboard. PHP · Laravel · MySQL · TailwindCSS</p>
        <div class="skills-wrapper" style="margin-top: 0.5rem;"><span class="tech-chip">PHP</span><span class="tech-chip">Laravel</span><span class="tech-chip">MySQL</span><span class="tech-chip">Chart.js</span></div>
      </div>
      <i class="fas fa-store" style="font-size: 3.5rem; opacity: 0.6; color: #a78bfa;"></i>
    </div>
  </div>

  <!-- Projects Grid -->
  <h2 style="margin: 2rem 0 1rem 0; display: flex; gap: 8px;"><i class="fas fa-laptop-code"></i> Featured <span class="gradient-text">Projects</span></h2>
  <div class="projects-grid">
    <div class="glass-card" style="padding: 1.5rem;">
      <div><i class="fas fa-satellite" style="font-size: 2rem; color: #86efac;"></i></div>
      <h3 style="margin: 0.8rem 0 0.3rem;">Satellite Image Detection</h3>
      <p style="font-size: 0.85rem;">YOLOv8 + FastAPI + React + Leaflet.js. Real-time detection and mapping.</p>
      <div class="skills-wrapper" style="margin-top: 0.6rem;"><span class="tech-chip">Python</span><span class="tech-chip">React</span><span class="tech-chip">YOLOv8</span><span class="tech-chip">PostgreSQL</span></div>
    </div>
    <div class="glass-card" style="padding: 1.5rem;">
      <div><i class="fas fa-users" style="font-size: 2rem; color: #facc15;"></i></div>
      <h3 style="margin: 0.8rem 0 0.3rem;">Society Management System</h3>
      <p>PHP, MySQL, Bootstrap – complete society event, billing, notice board system.</p>
      <div class="skills-wrapper"><span class="tech-chip">PHP</span><span class="tech-chip">MySQL</span><span class="tech-chip">Bootstrap</span></div>
    </div>
    <div class="glass-card" style="padding: 1.5rem;">
      <div><i class="fas fa-chalkboard-user" style="font-size: 2rem; color: #c084fc;"></i></div>
      <h3 style="margin: 0.8rem 0 0.3rem;">Classroom Management</h3>
      <p>Laravel + TailwindCSS – attendance, assignment submission, teacher dashboard.</p>
      <div class="skills-wrapper"><span class="tech-chip">PHP</span><span class="tech-chip">Tailwind</span><span class="tech-chip">JavaScript</span></div>
    </div>
    <div class="glass-card" style="padding: 1.5rem;">
      <div><i class="fas fa-user-tie" style="font-size: 2rem; color: #2dd4bf;"></i></div>
      <h3 style="margin: 0.8rem 0 0.3rem;">Employee Management</h3>
      <p>Full CRUD, role-based login, salary slip – MySQL + TailwindCSS.</p>
      <div class="skills-wrapper"><span class="tech-chip">PHP</span><span class="tech-chip">MySQL</span><span class="tech-chip">TailwindCSS</span></div>
    </div>
  </div>

  <!-- Experience + Education row -->
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 2rem; margin: 2.5rem 0;">
    <div class="glass-card" style="padding: 1.8rem;">
      <h3><i class="fas fa-briefcase"></i> Experience</h3>
      <div class="timeline-item" style="margin-top: 1rem;">
        <h4>Python Developer Intern</h4>
        <p style="font-size:0.8rem; color:#b0c4de;">BISAG-N, Gandhinagar · 3 months</p>
        <p style="font-size:0.85rem;">FastAPI, Flask, YOLOv8, PostgreSQL, SQLAlchemy, JWT – built satellite image detection pipelines & REST APIs.</p>
      </div>
      <div class="timeline-item">
        <h4>Freelance Web Projects</h4>
        <p style="font-size:0.85rem;">Developed multiple PHP/JS based management systems for small business, improved UX & efficiency.</p>
      </div>
    </div>
    <div class="glass-card" style="padding: 1.8rem;">
      <h3><i class="fas fa-university"></i> Education & Learning</h3>
      <div class="timeline-item">
        <h4>Master of Computer Applications (MCA)</h4>
        <p>L.J. Institute of Management Studies, Ahmedabad · 2024 – Present</p>
      </div>
      <div class="timeline-item">
        <h4>Bachelor of Computer Applications (BCA)</h4>
        <p>I.T. Sheliya Jafari B.C.A. College · 2021 – 2024</p>
      </div>
      <div><i class="fas fa-brain"></i> <strong>Currently exploring:</strong> ML, Flutter, ASP.NET/C#</div>
      <div class="skills-wrapper" style="margin-top: 12px;"><span class="tech-chip">Machine Learning</span><span class="tech-chip">Flutter</span><span class="tech-chip">C#</span></div>
    </div>
  </div>

  <!-- GitHub Stats Live Show (real data for TheTomCodes) -->
  <div class="glass-card" style="padding: 1.8rem; margin-bottom: 2rem;">
    <h3 style="display: flex; gap: 8px;"><i class="fab fa-github-alt"></i> GitHub Analytics · live stats</h3>
    <div class="stats-row">
      <img src="https://github-readme-stats.vercel.app/api?username=thetomcodes&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=7c3aed&icon_color=06b6d4&count_private=true" alt="GitHub Stats" style="width: 48%; min-width: 240px;">
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=thetomcodes&layout=compact&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=7c3aed" alt="Top Languages" style="width: 48%; min-width: 240px;">
    </div>
    <div class="stats-row">
      <img src="https://github-readme-streak-stats.herokuapp.com?user=thetomcodes&theme=tokyonight&hide_border=true&background=0d1117&ring=7c3aed&fire=f59e0b" alt="Streak stats" style="width: 70%;">
    </div>
    <div style="text-align: center; margin-top: 1rem;">
      <img src="https://github-profile-trophy.vercel.app/?username=thetomcodes&theme=tokyonight&no-frame=true&no-bg=true&margin-w=8&row=1&column=7" alt="trophies" style="width: 100%; max-width: 780px;">
    </div>
  </div>

  <!-- Contact / CTA with live UI Show -->
  <div class="glass-card" style="padding: 2rem; text-align: center; background: rgba(20, 22, 45, 0.7);">
    <i class="fas fa-paper-plane" style="font-size: 2.2rem; color: #a78bfa;"></i>
    <h3 style="margin: 0.5rem 0;">Let's connect & build something <span class="gradient-text">extraordinary</span></h3>
    <p style="margin-bottom: 1rem;">Open for collaborations, freelance opportunities, or just tech chat.</p>
    <div style="display: flex; justify-content: center; gap: 1.2rem; flex-wrap: wrap;">
      <a href="mailto:mohammadaliaglodiya51@gmail.com" class="btn-glow" style="background: #2d2b55;"><i class="far fa-envelope"></i> mohammadaliaglodiya51@gmail.com</a>
      <a href="https://github.com/TheTomCodes" target="_blank" style="background: #161b2e; border-radius: 40px; padding: 0.7rem 1.6rem;"><i class="fab fa-github"></i> github.com/TheTomCodes</a>
    </div>
  </div>

  <div class="footer-wave">
    <p style="font-size: 0.8rem;">⚡ MAHAMMADALI AGLODIYA — constantly shipping creative code & responsive experiences</p>
    <p style="font-size: 0.7rem; margin-top: 0.8rem;"><i class="fas fa-heart" style="color: #f43f5e;"></i> Advanced interactive UI | Live status | Real-time insights</p>
  </div>
</div>

<script>
  // Rotating typing effect + Live UI activities
  const roles = [
    "Full Stack Developer 💻",
    "Python & AI Enthusiast 🤖",
    "Laravel Artisan ⚙️",
    "UI/UX Perfectionist 🎨",
    "Open Source Contributor 🚀"
  ];
  let roleIndex = 0;
  let charIndex = 0;
  let isDeleting = false;
  const typedSpan = document.getElementById("typed-text");
  const cursorSpan = document.querySelector(".cursor-blink");
  
  function typeEffect() {
    const currentRole = roles[roleIndex];
    if (isDeleting) {
      typedSpan.innerText = currentRole.substring(0, charIndex - 1);
      charIndex--;
    } else {
      typedSpan.innerText = currentRole.substring(0, charIndex + 1);
      charIndex++;
    }
    if (!isDeleting && charIndex === currentRole.length) {
      isDeleting = true;
      setTimeout(typeEffect, 2000);
      return;
    }
    if (isDeleting && charIndex === 0) {
      isDeleting = false;
      roleIndex = (roleIndex + 1) % roles.length;
      setTimeout(typeEffect, 300);
      return;
    }
    const speed = isDeleting ? 50 : 80;
    setTimeout(typeEffect, speed);
  }
  typeEffect();

  // live dynamic activity (rotating activities every 7 sec)
  const activities = [
    "Building Grocery Store Management System 🛒",
    "Learning Flutter & ML 📱",
    "Improving satellite detection API 🛰️",
    "Writing clean PHP/Laravel backends 🧹",
    "Contributing to open source ⭐",
    "Crafting Tailwind UI components 🌊"
  ];
  let actIdx = 0;
  const activitySpan = document.getElementById("dynamic-activity");
  function updateLiveActivity() {
    actIdx = (actIdx + 1) % activities.length;
    if (activitySpan) {
      activitySpan.style.opacity = "0";
      setTimeout(() => {
        activitySpan.innerText = activities[actIdx];
        activitySpan.style.opacity = "1";
      }, 150);
    }
  }
  setInterval(updateLiveActivity, 5500);
  
  // Real-time clock (Ahmedabad IST)
  function updateClock() {
    const now = new Date();
    const options = { hour: '2-digit', minute: '2-digit', second: '2-digit', timeZone: 'Asia/Kolkata' };
    const timeString = now.toLocaleTimeString('en-IN', options);
    const clockSpan = document.getElementById("live-clock");
    if (clockSpan) clockSpan.innerText = timeString;
  }
  updateClock();
  setInterval(updateClock, 1000);

  // Additional micro-interaction: add hover effect to all glass cards 
  const cards = document.querySelectorAll('.glass-card');
  cards.forEach(card => {
    card.addEventListener('mousemove', (e) => {
      const rect = card.getBoundingClientRect();
      const x = ((e.clientX - rect.left) / rect.width) * 100;
      const y = ((e.clientY - rect.top) / rect.height) * 100;
      card.style.setProperty('--x', `${x}%`);
      card.style.setProperty('--y', `${y}%`);
    });
  });
  // styling dynamic gradient on hover (optional better already)
  document.head.insertAdjacentHTML('beforeend', `
    <style>
      .glass-card {
        --x: 50%;
        --y: 50%;
        transition: transform 0.2s, border-color 0.2s, box-shadow 0.2s;
      }
    </style>
  `);
  // Live view: also add page load entrance 
  console.log('Advanced UI live — Professional Portfolio Ready');
</script>
</body>
</html>
