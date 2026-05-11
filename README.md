<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Live UI Demo - Working Proof</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: system-ui, 'Segoe UI', 'Inter', sans-serif;
    }

    body {
      background: linear-gradient(145deg, #0a0f1e, #03050b);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 1rem;
    }

    /* glassomorphic card */
    .card {
      background: rgba(20, 25, 45, 0.7);
      backdrop-filter: blur(12px);
      border-radius: 2rem;
      padding: 2rem;
      width: 540px;
      max-width: 100%;
      border: 1px solid #7c3aed;
      box-shadow: 0 25px 40px -12px rgba(0, 0, 0, 0.6);
      transition: all 0.2s ease;
    }

    .card:hover {
      border-color: #a855f7;
      box-shadow: 0 30px 45px -12px black;
    }

    h1 {
      background: linear-gradient(135deg, #c084fc, #60a5fa);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      margin-bottom: 0.6rem;
      font-size: 1.9rem;
      letter-spacing: -0.3px;
    }

    .sub {
      color: #94a3b8;
      font-size: 0.9rem;
      margin-bottom: 1.2rem;
      border-left: 2px solid #7c3aed;
      padding-left: 0.75rem;
    }

    button {
      background: #7c3aed;
      border: none;
      padding: 0.6rem 1.3rem;
      border-radius: 2rem;
      font-weight: 600;
      color: white;
      cursor: pointer;
      transition: all 0.2s;
      margin-top: 0.8rem;
      margin-right: 0.8rem;
      font-size: 0.9rem;
    }

    button:hover {
      background: #a855f7;
      transform: scale(1.02);
      box-shadow: 0 0 12px #a855f7;
    }

    .value {
      font-size: 3.2rem;
      font-weight: 800;
      color: #c084fc;
      margin: 0.8rem 0 0.5rem 0;
      letter-spacing: 2px;
    }

    .time {
      font-family: 'Fira Code', monospace;
      background: #00000040;
      padding: 0.6rem;
      border-radius: 1.2rem;
      text-align: center;
      margin-top: 1.2rem;
      font-size: 1rem;
      color: #b9c7dd;
    }

    input {
      width: 100%;
      padding: 0.75rem;
      border-radius: 1.2rem;
      border: 1px solid #2d3250;
      background: #0f1222;
      color: white;
      margin: 0.5rem 0;
      font-size: 0.9rem;
      outline: none;
      transition: 0.2s;
    }

    input:focus {
      border-color: #a855f7;
      box-shadow: 0 0 0 2px rgba(168, 85, 247, 0.3);
    }

    .preview-box {
      background: #00000030;
      border-radius: 1.2rem;
      padding: 0.7rem;
      margin-top: 0.7rem;
      font-size: 0.95rem;
      border: 1px solid #2a2e48;
    }

    .flex-buttons {
      display: flex;
      flex-wrap: wrap;
      gap: 0.6rem;
      align-items: center;
    }

    hr {
      margin: 1rem 0;
      border-color: #2d3250;
    }

    footer {
      font-size: 0.7rem;
      text-align: center;
      margin-top: 1.5rem;
      opacity: 0.6;
      color: #7e8aa8;
    }
  </style>
</head>
<body>
<div class="card">
  <h1>✨ Advanced UI Preview</h1>
  <div class="sub">Live counter · real‑time clock · instant edit</div>

  <!-- counter section -->
  <div class="value" id="counter">0</div>
  <div class="flex-buttons">
    <button id="incBtn">➕ Increase +1</button>
    <button id="resetBtn" style="background: #334155;">🔄 Reset</button>
  </div>

  <!-- live editable text -->
  <input type="text" id="textInput" placeholder="Type something amazing..." value="Hello world">
  <div class="preview-box">
    💬 <strong>Live preview:</strong> <span id="preview">Hello world</span>
  </div>

  <!-- live clock -->
  <div class="time" id="liveClock">--:--:--</div>
  <footer>
    ⚡ Fully functional · interactive glassmorphism · no external dependencies
  </footer>
</div>

<script>
  // 1. counter logic
  let count = 0;
  const counterDiv = document.getElementById('counter');
  const incBtn = document.getElementById('incBtn');
  const resetBtn = document.getElementById('resetBtn');

  incBtn.onclick = () => {
    count++;
    counterDiv.innerText = count;
    // optional micro feedback (visual pulse)
    counterDiv.style.transform = 'scale(1.05)';
    setTimeout(() => { counterDiv.style.transform = 'scale(1)'; }, 120);
  };

  resetBtn.onclick = () => {
    count = 0;
    counterDiv.innerText = count;
    counterDiv.style.transform = 'scale(0.98)';
    setTimeout(() => { counterDiv.style.transform = 'scale(1)'; }, 150);
  };

  // 2. live text preview
  const textInput = document.getElementById('textInput');
  const previewSpan = document.getElementById('preview');

  textInput.oninput = () => {
    let newText = textInput.value;
    previewSpan.innerText = newText;
    // additional dynamic effect
    previewSpan.style.opacity = '0.7';
    setTimeout(() => { previewSpan.style.opacity = '1'; }, 100);
  };

  // 3. real-time clock (updates every second)
  function updateClock() {
    const now = new Date();
    // Indian standard time format (24h or 12h)
    const timeString = now.toLocaleTimeString('en-IN', { 
      hour12: false,
      hour: '2-digit',
      minute: '2-digit',
      second: '2-digit'
    });
    const clockElement = document.getElementById('liveClock');
    if (clockElement) clockElement.innerText = `🕒 ${timeString} IST`;
  }
  updateClock();
  setInterval(updateClock, 1000);
</script>
</body>
</html>
