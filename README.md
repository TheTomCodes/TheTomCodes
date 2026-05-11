<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Advanced Live UI · Professional Template</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;400;500;600;700;800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      background: linear-gradient(145deg, #0a0f1e 0%, #05070f 100%);
      font-family: 'Inter', sans-serif;
      color: #edf2ff;
      padding: 1.5rem;
      min-height: 100vh;
    }
    .dashboard {
      max-width: 1400px;
      margin: 0 auto;
    }
    /* glass cards */
    .glass {
      background: rgba(20, 25, 45, 0.55);
      backdrop-filter: blur(14px);
      border: 1px solid rgba(124, 58, 237, 0.3);
      border-radius: 2rem;
      transition: all 0.25s ease;
    }
    .glass:hover {
      border-color: #a855f7;
      transform: translateY(-3px);
      box-shadow: 0 20px 35px -12px rgba(0, 0, 0, 0.5);
    }
    .stat-card {
      padding: 1.5rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    h1 { font-size: 2.2rem; font-weight: 700; background: linear-gradient(135deg, #c084fc, #60a5fa); -webkit-background-clip: text; background-clip: text; color: transparent; }
    .live-badge {
      background: #10b98120;
      border-radius: 60px;
      padding: 0.3rem 1rem;
      font-size: 0.8rem;
      border-left: 3px solid #10b981;
    }
    .grid-3 {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.5rem;
      margin: 2rem 0;
    }
    .btn {
      background: #7c3aed;
      border: none;
      padding: 0.6rem 1.2rem;
      border-radius: 40px;
      font-weight: 600;
      cursor: pointer;
      transition: 0.2s;
    }
    .btn-outline {
      background: transparent;
      border: 1px solid #a855f7;
    }
    .btn:hover { background: #a855f7; transform: scale(1.02); box-shadow: 0 0 12px #a855f7; }
    .live-feed {
      background: #0b0e18;
      border-radius: 1.5rem;
      padding: 1rem;
      font-family: monospace;
      max-height: 200px;
      overflow-y: auto;
    }
    .feed-item {
      padding: 0.5rem;
      border-bottom: 1px solid #2d2f45;
      font-size: 0.85rem;
    }
    input, textarea {
      width: 100%;
      background: #0f1222;
      border: 1px solid #2d3250;
      border-radius: 1rem;
      padding: 0.8rem;
      color: white;
    }
    @keyframes pulse { 0% { opacity: 0.6; } 100% { opacity: 1; } }
    .pulse { animation: pulse 1.5s infinite; }
    footer { text-align: center; margin-top: 3rem; font-size: 0.75rem; opacity: 0.7; }
  </style>
</head>
<body>
<div class="dashboard">
  <!-- header with live clock + interactive -->
  <div style="display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 1rem; margin-bottom: 2rem;">
    <div>
      <h1><i class="fas fa-cube"></i> Advanced Live UI Panel</h1>
      <p>Real‑time dashboard — professional & interactive</p>
    </div>
    <div class="glass" style="padding: 0.8rem 1.5rem; text-align: center;">
      <i class="far fa-clock"></i> <span id="liveClock">--:--:--</span> IST &nbsp;|&nbsp;
      <span id="liveDate"></span>
    </div>
  </div>

  <!-- stats row -->
  <div class="grid-3">
    <div class="glass stat-card"><span><i class="fas fa-chart-line"></i> Live visitors</span> <strong id="visitorCount">247</strong></div>
    <div class="glass stat-card"><span><i class="fas fa-code-branch"></i> Active sessions</span> <strong id="activeSess">18</strong></div>
    <div class="glass stat-card"><span><i class="fas fa-bolt"></i> UI events (sec)</span> <strong id="eventRate">0</strong></div>
  </div>

  <!-- Two column layout: live feed + interactive action -->
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(330px, 1fr)); gap: 1.8rem;">
    <!-- live feed (dynamic messages) -->
    <div class="glass" style="padding: 1.5rem;">
      <h3><i class="fas fa-rss"></i> Live activity feed</h3>
      <div id="feedContainer" class="live-feed" style="margin-top: 1rem;">
        <div class="feed-item">✅ UI ready — listening for actions</div>
        <div class="feed-item">🖱️ Click on demo button to see live updates</div>
      </div>
      <button id="triggerAction" class="btn" style="margin-top: 1rem; width: 100%;"><i class="fas fa-play"></i> Simulate user action</button>
    </div>

    <!-- dynamic code preview / editable content (advanced feel) -->
    <div class="glass" style="padding: 1.5rem;">
      <h3><i class="fas fa-edit"></i> Live editable content</h3>
      <textarea id="editableText" rows="3" placeholder="Type something... this updates the card below in real time">Professional UI with live reactivity</textarea>
      <div style="margin-top: 0.8rem; background: #00000030; border-radius: 1rem; padding: 0.8rem;" id="livePreviewCard">
        <i class="fas fa-sync-alt"></i> <span id="previewText">Professional UI with live reactivity</span>
      </div>
      <div class="skills-wrapper" style="display: flex; flex-wrap: wrap; gap: 0.4rem; margin-top: 1rem;">
        <span class="badge" style="background:#7c3aed30; border-radius: 30px; padding: 0.2rem 0.8rem;">⚡ Real‑time</span>
        <span class="badge" style="background:#7c3aed30; border-radius: 30px; padding: 0.2rem 0.8rem;">🎨 Glassmorphism</span>
        <span class="badge" style="background:#7c3aed30; border-radius: 30px; padding: 0.2rem 0.8rem;">📊 Charts ready</span>
      </div>
    </div>
  </div>

  <!-- Advanced demo: live chart & data simulation -->
  <div class="glass" style="margin-top: 2rem; padding: 1.5rem;">
    <h3><i class="fas fa-chart-simple"></i> Live data simulation (real‑time counter)</h3>
    <div style="display: flex; align-items: baseline; gap: 1rem; flex-wrap: wrap;">
      <span style="font-size: 2.5rem; font-weight: 800;" id="liveNumber">0</span>
      <button id="incBtn" class="btn">+1</button>
      <button id="resetBtn" class="btn btn-outline">Reset</button>
    </div>
    <div style="margin-top: 1rem; background: #0a0c16; border-radius: 1rem; padding: 0.5rem;">
      <div style="width: 100%; background: #2d2f45; border-radius: 20px; height: 12px;">
        <div id="progressFill" style="width: 0%; background: linear-gradient(90deg, #a855f7, #60a5fa); height: 12px; border-radius: 20px;"></div>
      </div>
    </div>
  </div>
  <footer>
    <i class="fas fa-shield-alt"></i> Fully functional interactive demo · ready to replace with your actual code
  </footer>
</div>

<script>
  // 1. real time clock
  function updateClockAndDate() {
    const now = new Date();
    const timeStr = now.toLocaleTimeString('en-IN', { timeZone: 'Asia/Kolkata', hour12: false });
    document.getElementById('liveClock').innerText = timeStr;
    document.getElementById('liveDate').innerText = now.toLocaleDateString('en-IN');
  }
  setInterval(updateClockAndDate, 1000);
  updateClockAndDate();

  // 2. live feed log function
  const feedContainer = document.getElementById('feedContainer');
  function addFeedMessage(msg, type = 'info') {
    const div = document.createElement('div');
    div.className = 'feed-item';
    div.innerHTML = `<i class="fas ${type === 'action' ? 'fa-hand-pointer' : 'fa-info-circle'}"></i> ${msg}`;
    feedContainer.prepend(div);
    if (feedContainer.children.length > 8) feedContainer.removeChild(feedContainer.lastChild);
  }
  // simulate random visitor increment
  let visitors = 247;
  setInterval(() => {
    visitors += Math.floor(Math.random() * 3);
    document.getElementById('visitorCount').innerText = visitors;
    addFeedMessage(`📈 +${Math.floor(Math.random() * 3)} new visitor (total ${visitors})`);
  }, 12000);

  let sessions = 18;
  setInterval(() => {
    sessions = Math.floor(Math.random() * 25) + 10;
    document.getElementById('activeSess').innerText = sessions;
  }, 9000);

  // event counter for UI interactivity
  let eventCount = 0;
  function updateEventRate() {
    document.getElementById('eventRate').innerText = eventCount;
  }
  document.getElementById('triggerAction').addEventListener('click', () => {
    eventCount++;
    updateEventRate();
    addFeedMessage(`✨ User triggered demo action — event #${eventCount}`, 'action');
  });
  // live number counter & progress
  let counter = 0;
  const liveNumSpan = document.getElementById('liveNumber');
  const progressFill = document.getElementById('progressFill');
  function updateCounterUI() {
    liveNumSpan.innerText = counter;
    let percent = Math.min(100, (counter / 50) * 100);
    progressFill.style.width = percent + '%';
    if (counter === 100) addFeedMessage('🎉 Target 100 reached! reset to continue');
  }
  document.getElementById('incBtn').addEventListener('click', () => {
    counter++;
    updateCounterUI();
    addFeedMessage(`🔢 Counter increased to ${counter}`, 'action');
    eventCount++;
    updateEventRate();
  });
  document.getElementById('resetBtn').addEventListener('click', () => {
    counter = 0;
    updateCounterUI();
    addFeedMessage(`🔄 Counter reset to 0`, 'action');
    eventCount++;
    updateEventRate();
  });
  // live editable preview
  const textarea = document.getElementById('editableText');
  const previewSpan = document.getElementById('previewText');
  textarea.addEventListener('input', (e) => {
    previewSpan.innerText = e.target.value;
    addFeedMessage(`✏️ Live preview updated: "${e.target.value.substring(0, 30)}"`);
  });
  // initial feed
  addFeedMessage('🚀 Advanced UI template loaded — ready to embed your project code');
  setInterval(() => {
    addFeedMessage(`⏱️ System heartbeat at ${new Date().toLocaleTimeString()}`);
  }, 25000);
</script>
</body>
</html>
